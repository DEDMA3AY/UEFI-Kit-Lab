# UEFI Kit Lab

Универсальный диагностический комплекс для UEFI-платформ.
Запускается с загрузочной флешки, без установки и ОС.

Universal diagnostic suite for UEFI platforms.
Boots from a USB stick, no installation, no OS.

## Возможности / Features
- Тест физической памяти: 25 тестов (функциональные, Rowhammer/TRR,
  retention/Bit-Fade, термические, пропускная способность) с per-chip
  диагностикой и картой ошибок
- Physical RAM testing: 25 tests (functional, Rowhammer/TRR,
  retention/Bit-Fade, thermal, bandwidth) with per-chip diagnostics
  and error maps
- SPD: чтение/дамп всех планок (DDR3/DDR4/DDR5) по SMBus
- SPD: read/dump all modules (DDR3/DDR4/DDR5) over SMBus
- SPI BIOS: дамп и восстановление прошивки (Intel PCH / AMD FCH)
- SPI BIOS: dump and restore of the firmware (Intel PCH / AMD FCH)
- GPU vBIOS дамп / GPU vBIOS dump
- Телеметрия: RAPL, температура, MCA/ECC, NVRAM-история прогонов
- Telemetry: RAPL, temperature, MCA/ECC, NVRAM run history

## Установка / Installation
Запишите `dist/uefi-kit-lab.iso` через Rufus (GPT, UEFI), загрузитесь с флешки.
Write `dist/uefi-kit-lab.iso` with Rufus (GPT, UEFI) and boot from the stick.
Подробное описание — info.html внутри дистрибутива.
Full description — see info.html inside the distribution.

## Требования / Requirements
x64 UEFI-платформа. Для нагрузочных тестов 15/17/18/20 — AVX2.
x64 UEFI platform. Load tests 15/17/18/20 require AVX2.

## Важно / Important
Restore SPI BIOS перезаписывает прошивку платы — работайте только
с проверенными дампами, снятыми на этой же плате.
Restore SPI BIOS overwrites the board firmware — only work with
verified dumps taken from that same board.
