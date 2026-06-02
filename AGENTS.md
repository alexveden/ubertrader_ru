# Блог Ubertrader — Jekyll/Chirpy

## Стек

Ruby + Jekyll (тема Chirpy), деплой на GitHub Pages через GitHub Actions.

## Чем занимаемся

Всё редактирование сводится к Markdown-файлам в трёх папках:

- `_posts/` — опубликованные посты
- `_drafts/` — черновики
- `_tabs/` — страницы (about, categories, tags)

Всё остальное (тема, конфиги, CI, скрипты) — служебное, трогать не нужно.

## Установка

```bash
bundle install               # установка Ruby-зависимостей (Gemfile)
git submodule update --init  # подмодуль assets/lib
```

## Разработка

```bash
./tools/run.sh                        # dev-сервер с live reload
./tools/run.sh -p                     # сервер в production-режиме
./tools/test.sh                       # production-сборка + html-proofer
```

Или напрямую:

```bash
bundle exec jekyll s -l
```

## CI

`.github/workflows/pages-deploy.yml` — сборка + html-proofer при пуше в
`main`/`master`, деплой на GitHub Pages. Это единственный тест.

## Dev Container

`.devcontainer/devcontainer.json` — образ Jekyll 2-bullseye с предустановленными
расширениями VS Code. Используется для единообразного окружения.

## Линтер

Используется markdownlint (через `package.json`):

```bash
npm run lint
```

Конфиг в `.markdownlint.yaml`. Запускать после любых правок Markdown-файлов.

## Стиль

- Шаблон поста: `layout: post` в front matter.
- Язык блога — русский (`lang: ru-RU`).
- После редактирования Markdown: **линтер → `./tools/test.sh`** (если нужна полная проверка).
