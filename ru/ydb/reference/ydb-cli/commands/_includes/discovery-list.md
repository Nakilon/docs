---
sourcePath: ru/ydb/ydb-docs-core/ru/core/reference/ydb-cli/commands/_includes/discovery-list.md
---
# Список эндпоинтов

Информационная команда `discovery list` позволяет получить список [эндпоинтов](../../../../concepts/connect.md#endpoint) кластера YDB, с которыми можно открывать соединения для работы с заданной базой данных:

``` bash
{{ ydb-cli }} [connection options] discovery list
```

, где [connection options] - опции [соединения с БД](../../connect.md#command-line-pars)

В выводимых в ответ строках содержится следующая информация:
1. Эндпоинт, включая протокол и порт
2. В квадратных скобках зона доступности
3. С символом `#` перечень сервисов YDB, доступных на данном эндпоинте

Запрос к кластеру YDB на endpoint discovery выполняется в YDB SDK при инициализации драйвера, и команду CLI `discovery list` можно использовать для локализации возможных проблем соединения.

## Пример

``` bash
$ ydb --profile db1 discovery list
grpcs://vm-etn01q5-ysor.etn01q5k.ydb.mdb.yandexcloud.net:2135 [sas] #table_service #scripting #discovery #rate_limiter #locking #kesus
grpcs://vm-etn01q5-arum.etn01ftr.ydb.mdb.yandexcloud.net:2135 [vla] #table_service #scripting #discovery #rate_limiter #locking #kesus
grpcs://vm-etn01q5beftr.ydb.mdb.yandexcloud.net:2135 [myt] #table_service #scripting #discovery #rate_limiter #locking #kesus
```
