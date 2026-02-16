# Маршрутизация знаний

> **Source-of-truth** для всех промптов KE.
> При добавлении нового Pack'а — обновить ТОЛЬКО этот файл.
> Все промпты читают маршрутизацию отсюда.

---

## 1. Pack-репо по домену

| Домен | Pack | Префикс | Путь |
|-------|------|---------|------|
| Логистика, доставка, посылки, SLA, маркетплейс | PACK-marketplace | `MP` | `c:/Users/Admin/YandexDisk/репо s2r/PACK-marketplace/pack/marketplace/` |
| Цифровая платформа, ИТ, ИИ-системы, архитектура, SOTA | PACK-digital-platform-marketplace | `DP` | `c:/Users/Admin/YandexDisk/репо s2r/PACK-digital-platform-marketplace/pack/digital-platform/` |

## 2. Директории по типу знания

| Тип | Код | Директория в Pack | Формат файла |
|-----|-----|-------------------|-------------|
| Доменная сущность | `entity` | `02-domain-entities/` | Отдельный файл |
| Различение | `distinction` | `01-domain-contract/01B-distinctions.md` | Секция в файле |
| Метод | `method` | `03-methods/` | Отдельный файл |
| Рабочий продукт | `wp` | `04-work-products/` | Отдельный файл |
| Failure mode | `fm` | `05-failure-modes/` | Отдельный файл |
| Характеристика | `chr` | `06-characteristics/` | Отдельный файл |
| SoTA-аннотация | `sota` | `06-sota/` | Отдельный файл |
| Правило (глобальное) | `rule` | `c:/Users/Admin/YandexDisk/репо s2r/CLAUDE.md` | Строки |
| Правило (локальное) | `rule` | `<repo>/CLAUDE.md` | Строки |
| Правило (урок) | `rule` | `memory/<topic>.md` | Строки |

## 3. Именование файлов

**Конвенция:** `{PREFIX}.{TYPE}.{NNN}-{slug}.md`

| Компонент | Источник | Пример |
|-----------|----------|--------|
| `PREFIX` | Колонка «Префикс» из таблицы 1 | `MP`, `DP` |
| `TYPE` | Код типа (AISYS, METHOD, FM, WP, CHR, SOTA, ...) | `METHOD` |
| `NNN` | max(существующий) + 1 | `002` |
| `slug` | kebab-case из названия | `handler-per-state` |

## 4. Тест маршрутизации

Для каждого кандидата:

1. **Домен?** → определи Pack по таблице 1
2. **Тип знания?** → определи директорию по таблице 2
3. **Проверка bounded context:** Прочитай `00-pack-manifest.md` целевого Pack'а — попадает ли кандидат в scope?
4. **Если не попадает ни в один Pack** → предложи defer и уточни у пользователя

## 5. Feedback (обратная связь)

При reject/defer — записать причину в `config/feedback-log.md`.
При повторном inbox-check — прочитать feedback-log и не предлагать аналогичные кандидаты.

---

*Последнее обновление: 2026-02-16*
