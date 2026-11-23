# domains

Списки доменов и IP/CIDR для маршрутизации трафика в **Stash**, **mihomo (Clash Meta)** и **OpenWrt / dnsmasq / nftables**.

## Основные файлы

- `rule-direct.lst`, `rule-to-proxy.lst`, `rule-to-us.lst`, `rule-to-nl.lst` — ручные списки доменов для `behavior: domain`, `format: text` (формат записей: `+.example.com`).
- `rule-direct-ip.lst`, `rule-to-proxy-ip.lst`, `rule-tg-ip.lst` — списки IP/CIDR для `behavior: ipcidr`.
- `ru-mobile-whitelist.lst` — автообновляемый белый список доменов мобильного интернета РФ (источник: [ancored/ru-mobile-whitelist](https://github.com/ancored/ru-mobile-whitelist), формат `+.example.com`).
- `whitelist-exceptions.lst` — список доменов-исключений, которые вырезаются из `ru-mobile-whitelist.lst` при сборке (включая поддомены).
- `inside-raw.lst` — локальный список доменов.
- `inside-raw-itdog.lst`, `inside-raw-merged.lst`, `inside-dnsmasq-nfset.lst`, `inside-merged-yaml.txt`, `inside-merged-ru-yaml.txt` — автогенерируемые списки.

## Автообновление (GitHub Actions)

Workflow `.github/workflows/merge.yml` запускается:
- по расписанию каждые 8 часов (`0 */8 * * *` UTC);
- вручную через `workflow_dispatch`.

Конвертация `ru-mobile-whitelist.lst` выполняется только при изменении `SHA-256` исходного файла.

## Правила ведения репозитория

1. **Вести `changelog.md`:** при любых значимых изменениях (добавление/изменение правил, источников, структуры файлов или workflow) обязательно добавлять запись в [changelog.md](changelog.md) с указанием даты.
2. **Формат доменов:** в файлах `rule-*.lst` использовать префикс `+.` (`+.example.com`), чтобы правило одинаково матчило и корневой домен, и поддомены в Stash и mihomo.
