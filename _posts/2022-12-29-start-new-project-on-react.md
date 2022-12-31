---
layout: post
title:  "Начать новый проект на React.js"
date:   2022-12-29 11:38:01 +0300
categories: dev tools
---

Алгоритм действий для запуска нового проекта на [React.js](https://ru.reactjs.org/docs/getting-started.html). Компоненты протестированы в [Storybook](https://storybook.js.org).

### Последовательность действий:
- на github.com создать новый репозиторий;

- клонировать репозиторий на компьютер командой `git clone <SSH>`, где SSH копируем из созданного репозитория;

- находясь в родительской директории склонированного репозитория, установить React Create App командой `npx create-react-app название_проекта`. Название проекта должно совпадать с названием склонированного репозитория;

- создать файл `.editorconfig`:

```
//.editorconfig

# http://editorconfig.org
# A special property that should be specified at the top of the file outside of
# any sections. Set to true to stop .editor config file search on current file

root = true

[*]
# Indentation style
# Possible values - tab, space

indent_style = space

# Indentation size in single-spaced characters
# Possible values - an integer, tab

indent_size = 2

# Line ending file format
# Possible values - lf, crlf, cr

end_of_line = lf

# File character encoding
# Possible values - latin1, utf-8, utf-16be, utf-16le

charset = utf-8

# Denotes whether to trim whitespace at the end of lines
# Possible values - true, false

trim_trailing_whitespace = true

# Denotes whether file should end with a newline
# Possible values - true, false

insert_final_newline = true
```

- изменить файл `.gitignore`:

```
//.gitignore

# See https://help.github.com/articles/ignoring-files/ for more about ignoring files.

# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# dependencies
/node_modules
/.pnp
.pnp.js

# testing
/coverage

# Optional npm cache directory
.npm

# Optional REPL history
.DS_Store
.idea
.vscode

# production
/build

# misc
.env
.env.local
.env.development.local
.env.test.local
.env.production.local

npm-debug.log*
yarn-debug.log*
yarn-error.log*
```
- отредактировать `Readme.md`;

- из директории с проектом установить Storybook командой: `npx storybook init`. При необходимости выполнить требуемые установщиком действия. После установки Storybook запускается командой `npm run storybook` на 6006 порту (`http://localhost:6006/`).