---
sourcePath: ru/ydb/overlay/_includes/create-db-via-console.md
---
Чтобы создать базу данных:

{% list tabs %}

- Serverless

  1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором будет создана база данных.
  1. В списке сервисов выберите **{{ ydb-name }}**.
  1. Нажмите кнопку **Создать базу данных**.
  1. Введите **Имя** базы. Требования к имени:

      {% include [name-format](../../_includes/name-format.md) %}

  1. В блоке **Тип базы данных** выберите опцию **Serverless**.
  1. Вам будут предложены значения по умолчанию для параметров создаваемой базы данных. Вы можете оставить их без изменений, они выбраны таким образом, чтобы вы могли эффективно начать работу. В будущем вы можете их [изучить](../concepts/serverless_and_dedicated.md) и поменять, если потребуется.
  1. Нажмите кнопку **Создать базу данных**.

      Дождитесь запуска базы данных. В процессе создания база будет иметь статус `Provisioning`, а когда станет готова к использованию — статус сменится на `Running`.

- Dedicated

  1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором будет создана база данных.
  1. В списке сервисов выберите **{{ ydb-name }}**.
  1. Нажмите кнопку **Создать базу данных**.
  1. Введите **Имя** базы. Требования к имени:

      {% include [name-format](../../_includes/name-format.md) %}

  1. В блоке **Тип базы данных** выберите опцию **Dedicated**.
  1. В блоке **Вычислительные ресурсы** выберите тип и количество [вычислительных ресурсов](../concepts/databases.md#compute-units).
  1. В блоке **Группы хранения** выберите тип диска и количество [групп хранения](../concepts/databases.md#storage-groups), определяющее суммарный объем хранилища.
  1. В блоке **Сеть** настройте параметры сети:
      1. (опционально) В блоке **Публичные IP-адреса** выберите опцию **Присвоить**, если вы планируете отправлять запросы к базе не только из сети {{ yandex-cloud }}, но и через интернет.

          {% include  [traffic_metering](../_includes/traffic_metering.md) %}

      1. Выберите существующую сеть из списка **Облачная сеть** или создайте новую:
          * Нажмите кнопку **Создать новую**.
          * В открывшемся окне укажите **Имя** новой сети.
          * (опционально) Выберите опцию **Создать подсети**. Подсети в каждой зоне доступности будут созданы автоматически.
          * Нажмите кнопку **Создать**.
      1. В блоке **Подсети** выберите или создайте подсеть для каждой [зоны доступности](../../overview/concepts/geo-scope.md):
          * Нажмите кнопку **Создать подсеть**.
          * В открывшемся окне укажите **Имя** новой подсети.
          * (опционально) Введите **Описание** подсети.
          * Выберите из списка **Зона доступности** нужную зону.
          * Задайте адрес подсети в формате [**CIDR**](https://ru.wikipedia.org/wiki/Бесклассовая_адресация).
          * Нажмите кнопку **Создать**.
  1. Нажмите кнопку **Создать базу данных**.

      Дождитесь запуска базы данных. В процессе создания база будет иметь статус `Provisioning`, а когда станет готова к использованию — статус сменится на `Running`.

{% endlist %}
