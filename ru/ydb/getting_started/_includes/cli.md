---
sourcePath: ru/ydb/ydb-docs-core/ru/core/getting_started/_includes/cli.md
---
# YDB CLI - Начало работы

## Предварительные требования {#prerequisites}

Для выполнения команд через CLI вам потребуются параметры соединения с базой данных, которые вы можете получить при её [создании](../create_db.md):

- [Эндпоинт](../../concepts/connect.md#endpoint)
- [Имя базы данных](../../concepts/connect.md#database)

Также вам может потребоваться токен или логин/пароль, если база данных требует [аутентификации](../auth.md). Если для аутентификации применяется токен, то для успешного исполнения сценария ниже вам нужно выбрать вариант его сохранения в переменной окружения.

## Установка CLI {#install}

Установите YDB CLI как описано в статье [Установка YDB CLI](../../reference/ydb-cli/install.md).

Проверьте успешность установки YDB CLI запуском с параметром `--help`. В ответ должно быть выведено приветственное сообщение, краткое описание синтаксиса, и перечень доступных команд:

``` bash
$ {{ ydb-cli }} --help
YDB client

Usage: ydb [options...] <subcommand>

Subcommands:
ydb
├─ config                   Manage YDB CLI configuration
│  └─ profile               Manage configuration profiles
│     ├─ activate           Activate specified configuration profile (aliases: set)
...
```

Все возможности работы со встроенной справкой YDB CLI описаны в статье [Встроенная справка](../../reference/ydb-cli/commands/service.md#help) справочника по YDB CLI.

## Проверьте успешность соединения {#ping} {#scheme-ls}

Для проверки успешности соединения можно использовать команду [получения перечня объектов](../../reference/ydb-cli/commands/scheme-ls.md) в базе данных `scheme ls`:

``` bash
{{ ydb-cli }} -e <endpoint> -d <database> scheme ls
```

При успешном выполнении команды в ответ будет выведен перечень объектов в базе данных. Если вы еще не создавали ничего в БД, то вывод будет содержать только системный каталог `.sys`, в котором находятся [диагностические представления YDB](../../troubleshooting/system_views.md).

{% include [cli/ls_examples.md](cli/ls_examples.md) %}

## Создание профиля соединения {#profile}

Параметры соединения с базой данных могут быть довольно длинными, особенно при использовании явного указания [параметров аутентификации в командной строке](../../reference/ydb-cli/connect.md#command-line-pars). Чтобы не писать их каждый раз при вызове YDB CLI, воспользуйтесь [профилем](../../reference/ydb-cli/profile/index.md).

[Создайте профиль](../../reference/ydb-cli/profile/create.md) `db1` следующей командой: 

``` bash
{{ ydb-cli }} config profile create db1
```

В интерактивном режиме будут запрошены параметры соединения, которые нужно связать с данным профилем. Используйте для них проверенные на [предыдущем шаге](#ping) значения.

Имя профиля `db1` будет использоваться в следующих шагах, чтобы вы могли просто копировать примеры через буфер обмена.

Проверьте работоспособность профиля командой `scheme ls`:
``` bash
$ {{ ydb-cli }} --profile db1 scheme ls
.sys
```

## Исполнение YQL скрипта {#yql}

Команда YDB CLI `scripting yql` позволяет выполнить любую команду (как DDL так и DML) на [языке YQL](../../yql/reference/index.md) - диалекте SQL, поддерживаемом YDB:

``` bash
{{ ydb-cli }} --profile <profile_name> scripting yql -s <yql_request>
```

Например:
- Создание таблицы

  ``` bash
  {{ ydb-cli }} --profile db1 scripting yql -s "create table t1( id uint64, primary key(id))"
  ```
- Добавление записи 

  ``` bash
  {{ ydb-cli }} --profile db1 scripting yql -s "insert into t1(id) values (1)"
  ```
- Выборка данных

  ``` bash
  {{ ydb-cli }} --profile db1 scripting yql -s "select * from t1"
  ```

Если вы получаете ошибку `Profile db1 does not exist` - значит вы не создали его на [предыдущем шаге](#profile).

Для знакомства с синтаксисом и основными командами YQL перейдите к статье [YQL - Начало работы](../yql.md).

## Специализированные команды CLI {#ydb-api}

Исполнение команд через `scripting yql` является хорошим простым способом начать работу. Однако, YQL-интерфейс поддерживает неполный набор возможных функций, доступных на YDB API, а также работает не самым эффективным образом из-за своей универсальности.

YDB CLI поддерживает отдельные команды с полным набором опций для всех существующих YDB API. Описание полного перечня команд находится в [справочнике по YDB CLI](../../reference/ydb-cli/index.md).