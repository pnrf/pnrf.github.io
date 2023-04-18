---
layout: post
title:  "Настройки для VS Code"
date:   2023-04-16 18:20:01 +0300
categories: tools and settings
---

Уютное место, доброжелательное окружение и отлаженные инструменты крайне важны для эффективной работы. Воспользовался советами от [WebDeign Master](https://webdesign-master.ru/blog/tools/vscode.html), чтобы настроить под себя VSCode и в дальнейшем на это не отвлекаться.

**Сайт VS Code:**
- https://code.visualstudio.com -- скачать и установить редактор (это бесплатно);

**Настройки VS Code**
- `code > parameters > settings` -- открыть окно настроек редактора;
- `"editor.smoothScrolling": true` -- плавный скрол;
- `"editor.fontSize": 14` -- размер основного шрифта кода;
- `"terminal.integrated.fontSize": 14` -- размер шрифта во встроенном терминале;
- `"editor.minimap.enabled": false` -- отключить миникарту;
- `"breadcrumbs.enabled": false` -- отключить хлебные крошки;
- `"editor.renderControlCharacters": true` -- включить управляющие символы в коде;
- `"editor.tabSize": 2` -- отступы в коде (число пробелов табуляции);
- `"editor.detectIndentation": false` -- отключить авто определение для Tab Size и Insert Spaces;
- `"editor.folding": false` -- отключить опцию скрытия текста;
- `"editor.parameterHints.enabled": false` -- отключить попап с подсказками (документацией по параметру);
- `"editor.hover.enabled": false` -- отключить подсказку при наведении курсора на теги;
- `"editor.lineHeight": 23` -- высота строки (чтобы строчки не сливались);
- `"editor.insertSpaces": false` -- отключить мягкую и включить жесткую табуляцию;
- `"editor.linkedEditing": true` -- включить связанную поддержку редактирования;
- `"editor.renderWhitespace": "boundary"` -- отобразить пробелы в виде точек.

**Расширения:**
- `New Moon Syntax Theme` или `New Moon: Blue Syntax Theme` -- цветовая темя для интерфейса;
  
- `CSS Peek` -- позволяет по клику перейти из html-файла к css-стилям выбранного класса;

- `eCSStractor for VSCode` -- позволяет скопировать названия классов из выделенного куска html-кода в css-файл;

- `Gist` -- позволяет хранить отдельные участки кода, сниппеты в гистах. Нужно привязать к своему github-аккаунту.

- `HTML to CSS completion` -- подсказывает название класса при написании стилей в css-файле;

- `IntelliSense for CSS class names in HTML` -- подсказывает название класса при написании html-кода;

- `Live Server` -- позволяет запустить локальный сервер;
