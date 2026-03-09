# TOOLS.md - Локальные настройки

## Напоминания
Все напоминания - sessionTarget: "isolated" + payload.kind: "agentTurn"
НИКОГДА sessionTarget: "main" + systemEvent!

## После обновления OpenClaw
1. openclaw status
2. Проверить WAL mode
3. Проверить плагины

НЕ openclaw gateway restart из сессии!
Mac: launchctl kickstart -k
Linux: systemctl restart openclaw

## Маршрутизация моделей
- Мощная (Opus): разговор, стратегия, тексты
- Быстрая (Sonnet): данные, черновики, кроны
- Одна модель - используйте для всего

Кроны: полное имя модели (anthropic/claude-sonnet-4-6)
SQLite WAL обязателен!
