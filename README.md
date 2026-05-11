# CMR Renamer

## Быстрый запуск

1. Подготовьте папку с исходными PDF, например `input/`.
2. Подготовьте `manifest.json` (массив объектов `DocumentMeta`).
3. Запустите:

```bash
python cmr_renamer.py \
  --input-dir ./input \
  --output-dir ./output \
  --manifest ./manifest.json
```

После выполнения:
- переименованные файлы будут в `output/`
- отчёт будет в `output/report.json`

## Проверка ZIP перед обработкой

Если получен архив, можно включить контроль количества PDF в ZIP против количества записей в `manifest.json`:

```bash
python cmr_renamer.py \
  --input-dir ./input \
  --output-dir ./output \
  --manifest ./manifest.json \
  --zip ./docs.zip
```

При несовпадении количества программа завершится с ошибкой.

## Пример `manifest.json`

```json
[
  {
    "original_name": "00000001.PDF",
    "colt_numbers": ["1040378"],
    "sender": "FUTURUS FOOD SIA",
    "consignee": "MAXIMA EESTI OU",
    "doc_date": "30.04.2026",
    "rotate_180": true,
    "zone24_signed": false
  },
  {
    "original_name": "00000002.PDF",
    "sender": "AD BALTIC",
    "place_of_delivery": "Ringtee 35 Tartu",
    "doc_date": "28.04.2026"
  }
]
```
