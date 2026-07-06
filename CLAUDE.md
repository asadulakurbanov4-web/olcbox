# Olcbox - клиент-конфигуратор olcRTC (Kotlin Multiplatform + Compose)

> ⚠️ **Внешний upstream-форк (MIT, автор alananisimov). Ведётся только вручную.**
> НЕ подключать автопилот и делегирование, не коммитить автоматически, не вести здесь автономную разработку.

## Мини-карта (полный INDEX не строим — форк)
- **Что:** клиент-конфигуратор olcRTC на Kotlin Multiplatform + Compose (Android/desktop/iOS).
- **Модули:** `:sharedUI` (общий UI/логика) · `:sharedUI:olcrtc-bin` (ядро olcRTC через gomobile из `~/olcrtc-src`) · `:androidApp` · `:desktopApp` (+ `iosApp`).
- **Точка сборки:** корневой Gradle (`./gradlew`, `settings.gradle.kts`); гейт из CI — см. раздел «Сборка и проверки» ниже.

Общие правила (стиль общения, делегирование субагентам, коммиты) - в user memory `~/.claude/CLAUDE.md`.
Здесь - специфика клиента.

Kotlin Multiplatform + Compose. Ветка по умолчанию - `main`. Лицензия - MIT. Статус - alpha.
Модули: `:sharedUI` (общий UI/логика), `:sharedUI:olcrtc-bin` (ядро olcRTC через gomobile),
`:androidApp`, `:desktopApp` (+ `iosApp`).

## Перед кодом

- Ориентируйся через граф: `graphify query "<вопрос>"` (в корне есть `graphify-out/graph.json`),
  сырые файлы читай после. После правок: `graphify update .`.
- `:sharedUI:olcrtc-bin` собирается из Go-ядра через gomobile+mage - для правок самого ядра
  смотри репозиторий `~/olcrtc-src`, здесь только его биндинг.

## Сборка и проверки

Гейт из CI (`.github/workflows/pr-checks.yml`) - гоняй его перед коммитом:
```
./gradlew :sharedUI:jvmTest :desktopApp:compileKotlin :androidApp:assembleDebug --stacktrace
```
- Тесты shared-слоя: `:sharedUI:jvmTest`.
- Сборка Android: `:androidApp:assembleDebug`; desktop: `:desktopApp:compileKotlin`.
- Для сборки нужны Android SDK/NDK и gomobile+mage (см. pr-checks.yml).

## Стиль кода

- Английский в коде и комментариях; русский в документации.
- Пиши в стиле окружающего Compose/KMP-кода, без новых зависимостей без нужды.

> NB: раскладку и конвенции этого репо владелец ещё не зафиксировал - при расширении этого
> файла сверься с ним (это отдельный продукт со своей лицензией и автором).
