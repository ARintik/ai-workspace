# DO_NOT_DELETE.md - Защита от удаления

## Критичные файлы (НИКОГДА не удалять)

- IDENTITY.md, SOUL.md, USER.md, AGENTS.md, MEMORY.md, TOOLS.md, HEARTBEAT.md
- ~/.openclaw/openclaw.json
- memory/core/* (всё в этой папке)
- memory/decisions/* (всё в этой папке)
- memory/projects/* (всё в этой папке)
- skills/**/*.md (все скиллы)

## Разрешено удалять

- memory/YYYY-MM-DD.md старше 90 дней (после архивации!)
- *.bak старше 30 дней
- *.tmp
- .DS_Store

## Правило

Перед удалением ЛЮБОГО файла - сверься с этим списком.
Если файла нет в "Разрешено удалять" - спроси владельца.
Удаляй через trash, не через rm -rf.
