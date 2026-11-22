# Changelog

Все значимые изменения в репозитории фиксируются в этом файле.

## 2026-11-22

### Добавлено
- В workflow `.github/workflows/merge.yml` добавлен шаг загрузки и конвертации белого списка мобильного интернета РФ из [ancored/ru-mobile-whitelist](https://github.com/ancored/ru-mobile-whitelist) (`ru-mobile-whitelist-sni.txt`) в `ru-mobile-whitelist.lst` с префиксом `+.` и проверкой изменений по `SHA-256`.
- Сгенерирован `ru-mobile-whitelist.lst` (1 394 домена).
- Созданы `readme.md` и `changelog.md`.

### Изменено
- Во всех доменных файлах `rule-*.lst` (`rule-direct.lst`, `rule-to-nl.lst`, `rule-to-proxy.lst`, `rule-to-us.lst`) префикс `.` заменён на `+.` для одинакового матчинга корня и поддоменов в Stash и mihomo.
