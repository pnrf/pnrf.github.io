---
layout: post
title:  "Prefixes for commits"
date:   2023-04-23 16:45:18 +0300
categories: git/github
---

Наименования коммитов должны соответствовать определенным правилам. Среди разработчиков применяется [спецификация](https://www.conventionalcommits.org/en/v1.0.0/), которая содержит простой набор правил для унификации коммитов и упрощения их автоматизированной обработки.

### Префиксы:

- `build:` - при изменениях, влияющих на систему сборки или внешние зависимости (например, webpack, gulp, npm и пр.)

- `ci:` - при изменении конфигурационных файлов в проекте; 

- `docs:` - при изменении документации (например, Readme.md и пр.);

- `feat:` - при добавлении новой функциональности;

- `fix:` - при исправлении ошибок в кодовой базе;

- `perf:` - при изменении кода, если такие изменения в значительной мере повышают производительность проекта;

- `refactor:` - при изменении кода, если такие изменения не связаны с исправлением ошибок (`fix:`) или с добавлением новой функциональности (`feat:`);

- `style:` - при изменении кода, если такие изменения не оказывают значимое влияние на код (например, при добавлении/удалении пробелов, форматировании, исправлении пунктуации и пр.);

Для критически важных изменений допустимо применять футер `BREAKING CHANGE:` или `!` после префикса.

Примеры:

```bash
# Commit message with description and breaking change footer

feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

```bash
# Commit message with `!` to draw attention to breaking change

feat!: send an email to the customer when a product is shipped
```

```bash
# Commit message with scope and ! to draw attention to breaking change

feat(api)!: send an email to the customer when a product is shipped
```

```bash
# Commit message with both ! and BREAKING CHANGE footer

chore!: drop support for Node 6

BREAKING CHANGE: use JavaScript features not available in Node 6.
```

```bash
# Commit message with no body

docs: correct spelling of CHANGELOG
```

```bash
# Commit message with scope

feat(lang): add Polish language
```

```bash
# Commit message with multi-paragraph body and multiple footers

fix: prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Reviewed-by: Z
Refs: #123
```