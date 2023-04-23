---
layout: post
title:  "Новый проект на React.js + Storybook"
date:   2022-12-29 11:38:01 +0300
categories: dev tools
---

Алгоритм действий для запуска нового проекта на [React.js](https://ru.reactjs.org/docs/getting-started.html) с возможностью тестирования компонентов в [Storybook](https://storybook.js.org).

### Последовательность действий:
- на github.com создать новый репозиторий;

- клонировать репозиторий на компьютер командой `git clone <SSH>`, где SSH копируем из созданного github-репозитория;

- находясь в **родительской** директории склонированного репозитория, установить React командой `npx create-react-app название_проекта`. Название проекта должно совпадать с названием склонированного репозитория;

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

# Sass
.sass-cache/
*.css.map
*.sass.map
*.scss.map

# Logs
logs
*.log

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
.env.local
.env.development.local
.env.test.local
.env.production.local

npm-debug.log*
yarn-debug.log*
yarn-error.log*
```
- отредактировать `Readme.md`;

- из директории с проектом установить Storybook командой: `npx storybook@latest init` (см. официальную [документацию](https://storybook.js.org/docs/react/get-started/install/)). При необходимости выполнить требуемые установщиком действия. После установки Storybook запускается изолированно от основного приложения командой `npm run storybook` на 6006 порту (`http://localhost:6006/`).

- скорректировать файловую структуру. Например:  

```html
<!--Это файловя струтктура. Тег <code> использован для корректного отображения структуры в блоге. Смысловую нагрузку не несет-->
<code>
    - public/
        - favicon.ico
        - index.html
        - robots.txt
    - src/
        - components/
            - App/
                - App.css
                - App.js
                - App.test.js
            - Footer/
                - Footer.css
                - Footer.js
            - etc...
        - contexts/
            - CurrentUserContext.js
        - images/
            - icons/
                - arrow-right-white.svg
            - logo.svg
            - etc...
        - utils/
            - MainApi.js
            - constants.js
            - jwt.js
            - etc...
        - vendor/
            - fonts/
                - Inter-Black.woff
                - Inter-Black.woff2
                - etc...
                - LICENSE.txt
                - fonts.css
            - normalize.css
        - index.css
        - index.js
        - reportWebVitals.js
        - setupTests.js
    - .editorconfig
    - .gitignore
    - README.md
    - package-lock.json
    - package.json
</code>
```
- в директории `public` изменить favicon.ico, robots.txt и index.html:

```html
<!-- index.html -->

<!DOCTYPE html>
<html lang="ru">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="keywords" content="детский, сад, Митино, дети, английский, язык">
    <meta name="robots" content="noindex, nofollow">
    <meta name="description" content="Английский детский сад в Митино для детей с 2 до 7 лет с погружением в языковую среду">
    <title>Kids Story — билингвальный детский сад в Митино</title>
  </head>
  <body class="root">
		<div class="page">
			<noscript id="nojs">
				<div style="margin: 10px 10px; padding: 10px 30px; color: #FFF; background-color: #0000DE; font-family: Ubuntu, OpenSans,sans-serif; text-align:center; border-radius: 20px 0;">
					Для корректной работы сайта, пожалуйста, включите JavaScript в настройках вашего браузера
				</div>
			</noscript>
		</div>
  </body>
</html>
```

- добавить normalize.css и шрифты в директорию vendors;
- отредактировать index.css. Например:

```css
/* index.css */

@import url(./vendor/normalize.css);
@import url(./vendor/fonts/fonts.css);

#root {
  margin: 0 auto;
  padding: 0;
  box-sizing: border-box;
  max-width: 1920px;
  min-width: 320px;
  background-color: #fff;
  color: #334155;
  font-family: 'Montserrat', Arial, sans-serif;
  cursor: auto;

  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
  -moz-text-size-adjust: 100%;
}
```
- создать stories для компонентов.