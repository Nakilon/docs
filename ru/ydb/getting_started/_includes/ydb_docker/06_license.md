---
sourcePath: ru/ydb/ydb-docs-core/ru/core/getting_started/_includes/ydb_docker/06_license.md
---
## Лицензия и используемые компоненты {#license}

В корне Docker-контейнера расположены файл с текстом лицензионного соглашения (`LICENSE`) и список используемых компонентов и их лицензии (`THIRD_PARTY_LICENSES`).

Просмотрите текст лицензионного соглашения:

```bash
sudo docker run --rm -it --entrypoint cat {{ ydb_local_docker_image }} LICENSE
```

Просмотрите все использованные при создании компоненты и их лицензии:

```bash
sudo docker run --rm -it --entrypoint cat {{ ydb_local_docker_image }} THIRD_PARTY_LICENSES
```
