---
sourcePath: ru/ydb/ydb-docs-core/ru/core/reference/ydb-cli/commands/_includes/scheme-ls/intro.md
---
# Список объектов

Чтобы получить список объектов, используйте подкоманду `scheme ls <Путь>`. Если путь не указан, то будет выведен листинг корня базы данных:

```bash
{{ ydb-cli }} scheme ls
```

Результат:

```text
episodes seasons  series .sys
```

Чтобы посмотреть подробную информацию об объектах, добавьте флаг `-l`:

```bash
{{ ydb-cli }} scheme ls -l
```
