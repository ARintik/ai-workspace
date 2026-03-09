# VPN Setup

## Зачем
Claude API заблокирован в стране. Трафик идёт через VPN.

## Цепочка
OpenClaw → Privoxy (8118) → Shadowsocks-local (1080) → VPN сервер США (208.123.119.93:443) → Anthropic API

## Компоненты
- **shadowsocks-libev** (ss-local): конфиг /etc/shadowsocks-libev/config.json, протокол chacha20-ietf-poly1305
- **shadowsocks-client.service**: системный сервис, 127.0.0.1:1080, enabled
- **privoxy**: HTTP→SOCKS5 конвертер, порт 8118, enabled
- **openclaw-gateway**: user-сервис, Environment HTTPS_PROXY/HTTP_PROXY = http://127.0.0.1:8118

## OpenAI Embeddings Proxy
- OpenAI API тоже заблокирован по региону
- Решение: локальный reverse proxy (Node.js) на порту 8119
- Путь: localhost:8119 → SOCKS5 :1080 → VPN → api.openai.com
- Сервис: ~/.config/systemd/user/openai-proxy.service (user, enabled)
- Код: ~/.openclaw/openai-proxy/server.mjs
- В openclaw.json: memorySearch.remote.baseUrl = "http://127.0.0.1:8119/v1"

## Автозапуск
Все четыре сервиса enabled - стартуют автоматически при загрузке:
1. shadowsocks-client (system) - SOCKS5 :1080
2. privoxy (system) - HTTP proxy :8118
3. openai-proxy (user) - reverse proxy :8119
4. openclaw-gateway (user) - использует :8118 и :8119
