---
sourcePath: ru/ydb/ydb-docs-core/ru/core/maintenance/_includes/backup_and_recovery/06_s3_3_access_keys.md
---
### Создание ключей доступа {#s3_create_access_keys}

Для аутентификации и авторизации в S3-совместимых хранилищах используются ключи доступа. [Консольный клиент YDB](../../../reference/ydb-cli/index.md) предоставляет три варианта передачи ключей:

* через опции командной строки `--access-key` и `--secret-key`;
* через переменные окружения `AWS_ACCESS_KEY_ID` и `AWS_SECRET_ACCESS_KEY`;
* через файл `~/.aws/credentials`, создаваемый и используемый [AWS CLI](https://aws.amazon.com/ru/cli/).

Настройки применяются в порядке, описанном выше. Например, если одновременно использовать все три варианта передачи значения access_key или secret_key, то будут использованы значения, переданные через опции командной строки.
