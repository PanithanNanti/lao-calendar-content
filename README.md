# Lao Calendar content

Holidays, Buddhist festivals and customs (ຮີດສິບສອງ) read by the Lao Calendar app
(ປະຕິທິນລາວ). The app ships a copy and downloads this file to stay up to date:

    https://panithannanti.github.io/lao-calendar-content/v1/content.json

Do not edit here by hand: the source file lives in the app repo
(`LaoCalendarKit/Sources/LaoCalendarKit/Resources/content.json`) and is published with
`content/publish.sh`, which runs the tests first.

## Format (schemaVersion 1)

Each event has `id`, `kind` (`publicHoliday`, `buddhist`, `tradition`, `commemoration`, `bank`),
`title` `{lo, en}`, optional `description`, and a `rule`:

| rule | example |
|---|---|
| `fixed` | `{"type": "fixed", "month": 12, "day": 2}`; `length` for several days; `overrides` per year |
| `dates` | `{"type": "dates", "dates": [["2027-04-13", "2027-04-16"]]}` |
| `lunar` | `{"type": "lunar", "month": 3, "phase": "waxing", "day": 15}`; `"day": "last"` = ວັນດັບ |
| `lunarMonth` | `{"type": "lunarMonth", "month": 1}` (the whole month) |
| `lunarRange` | `{"type": "lunarRange", "from": {...}, "to": {...}}` |

Lunar month 8 means ເດືອນແປດຫຼັງ in a leap-month year. Bump `contentVersion` on every change.
Older apps skip events they can't read; a new incompatible format needs `schemaVersion` 2 under `v2/`.
