# Publishing new versions / Публикация новых версий

## One-time setup / Разовая настройка

1. Install [GitHub CLI](https://cli.github.com/): `winget install GitHub.cli`
   Установить GitHub CLI: `winget install GitHub.cli`
2. Authorize: `gh auth login` (GitHub.com → HTTPS → Login with a web browser)
   Авторизоваться: `gh auth login` (GitHub.com → HTTPS → браузер)
3. git identity: настроен глобально (DEDMA3AY). / configured globally.

## Release workflow / Порядок выпуска версии

### Step 1 / Шаг 1 — Make changes / Внести изменения
Код правится в `E:\PROJECTS\TEST_NIOCHEM` (UefiAppPkg).

### Step 2 / Шаг 2 — Bump version / Поднять версию
`UefiAppPkg\UefiApp\Version.h`:
```c
#define APP_VERSION_MAJOR  1
#define APP_VERSION_MINOR  82   // → 83
```
(отображаемые строки APP_VERSION_V / APP_VERSION_RV — синхронно)

### Step 3 / Шаг 3 — Update CHANGELOG / Обновить CHANGELOG
Новая запись СВЕРХУ в `CHANGELOG.md` (правило AGENTS.md, Правило 6).
Затем: `tools\make_changelog.ps1` (локальный CHANGELOG.html) и
`tools\make_changelog_github.ps1` (витринный для репозитория).

### Step 4 / Шаг 4 — Fill release notes / Заполнить заметки
Отредактировать `RELEASE_NOTES.md` в этой папке — содержимое попадёт
в описание релиза на GitHub.

### Step 5 / Шаг 5 — Publish / Опубликовать
```
publish_release_kit.bat
```
Лежит в корне `E:\PROJECTS\TEST_NIOCHEM`. Скрипт сам соберёт проект,
создаст ISO и ZIP, обновит витрину, создаст релиз и напечатает ссылку.

### Step 6 / Шаг 6 — Verify / Проверить
- https://github.com/DEDMA3AY/UEFI-Kit-Lab/releases

## What publish_release_kit.bat does / Что делает скрипт

| # | Action / Действие |
|---|---|
| 1 | Читает версию из `Version.h` (APP_VERSION_MINOR) / reads version |
| 2 | Проверяет авторизацию gh CLI / checks gh auth |
| 3 | Проверяет, что тег vX.Y свободен / tag availability |
| 4 | Собирает: `build.bat RELEASE VS2019` / builds the EFI app |
| 5 | Дистрибутив: `Make-Dist.bat` → ISO → ZIP / makes ISO + ZIP |
| 6 | Обновляет витрину (README/CHANGELOG/notes) / syncs the showcase repo |
| 7 | `gh release create vX.Y <ZIP>` — ZIP как ассет релиза / publishes the release |

## Important / Важно

- **Исходники не публикуются** — в репозитории только README, CHANGELOG,
  RELEASE_NOTES и PUBLISH.md. ZIP/ISO — ассеты релиза, не коммиты.
  / **Never commit sources or the ZIP to git** — the repo holds only
  README, CHANGELOG and notes; the ZIP is a release asset.
- ZIP содержит: `uefi-kit-lab.iso`, `info.html` (RU+EN), `CHANGELOG.html`
  (витринный, заголовки версий).
