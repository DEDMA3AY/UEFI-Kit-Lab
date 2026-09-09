# UEFI Kit Lab v2.82

Первый публичный релиз. / First public release.

## Состав / Contents
- `uefi-kit-lab.iso` — загрузочный образ (Rufus, GPT/UEFI) / bootable image
- `info.html` — описание программы и тестов (RU + EN) / program and test description
- `CHANGELOG.html` — история изменений / version history

## Последние изменения (v2.74 — v2.82) / Recent changes

**RU**
- Корректное досрочное завершение тестов: фантомные ошибки BlockMove
  при остановке прогона устранены
- Плавный секундомер и экран во всех тестах (без подмерзаний)
- Скорость памяти: методология как у MemTest86 (read+write),
  вывод в строке Memory
- BW-вердикт: ложные «severe» устранены, пометка «шум доминирует»
- Test 23/24 запускаются из меню, тесты 21-24 видны в результатах
- Dump BIOS не снимает защиту записи; restore с гейтом
- Пакет исправлений по независимому аудиту (v2.73) — полный список в CHANGELOG

**EN**
- Correct early test termination: phantom BlockMove errors on run
  interruption are eliminated
- Smooth stopwatch and display in all tests (no freezes)
- Memory bandwidth: MemTest86 methodology (read+write), shown in
  the Memory row
- BW verdict: false "severe" eliminated, "noise floor" annotation
- Test 23/24 launch from the menu, tests 21-24 visible in results
- Dump BIOS no longer removes write protection; gated restore
- Independent-audit fix pack (v2.73) — full list in the CHANGELOG
