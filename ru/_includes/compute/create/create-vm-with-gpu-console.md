Чтобы создать виртуальную машину:
1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором будет создана виртуальная машина.
1. В списке сервисов выберите **{{ compute-name }}**.
1. Нажмите кнопку **Создать ВМ**.
1. В блоке **Базовые параметры**:
    * Введите имя и описание ВМ. Требования к имени:

        {% include [name-format](../../name-format.md) %}

        {% include [name-fqdn](../name-fqdn.md) %}

    * Выберите [зону доступности](../../../overview/concepts/geo-scope.md), в которой будет находиться виртуальная машина.

1. В блоке **Выбор образа/загрузочного диска** на вкладке **{{ marketplace-name }}** выберите один из GPU-ориентированных [образов](../../../compute/operations/images-with-pre-installed-software/get-list.md) и версию операционной системы.

    {% include [gpu-os](../gpu-os.md) %}

1. (опционально) В блоке **Диски и файловые хранилища** настройте загрузочный диск:
    * Выберите [тип диска](../../../compute/concepts/disk.md#disks_types).
    * Укажите нужный размер диска.

1. (опционально) В блоке **Диски и файловые хранилища** на вкладке **Файловые хранилища** подключите [файловое хранилище](../../../compute/concepts/filesystem.md) и введите имя устройства.

1. В блоке **Вычислительные ресурсы**:
    * Выберите одну из [платформ](../../../compute/concepts/vm-platforms.md#gpu-platforms):
        * {{ v100-broadwell }}.
        * {{ v100-cascade-lake }}.
        * {{ a100-epyc }}.
    * Выберите [конфигурацию](../../../compute/concepts/gpus.md#config) виртуальной машины, указав необходимое количество GPU.
    * При необходимости сделайте виртуальную машину [прерываемой](../../../compute/concepts/preemptible-vm.md).

1. В блоке **Сетевые настройки**:
    * Укажите идентификатор подсети или выберите [облачную сеть](../../../vpc/concepts/network.md#network) из списка.
        Если сети нет, нажмите **Создать сеть** и создайте ее:
        * В открывшемся окне укажите укажите имя сети и каталог, в котором она будет создана.
        * (опционально) Для автоматического создания подсетей выберите опцию **Создать подсети**.
        * Нажмите **Создать**.
        У каждой сети должна быть как минимум одна [подсеть](../../../vpc/concepts/network.md#subnet). Если подсети нет, создайте ее, выбрав **Добавить подсеть**.
    * В поле **Публичный адрес** выберите способ назначения адреса:
        * **Автоматически** — чтобы назначить случайный IP-адрес из пула адресов {{ yandex-cloud }}. В этом случае можно включить [защиту от DDoS-атак](../../../vpc/ddos-protection/index.md) при помощи опции ниже.
        * **Список** — чтобы выбрать публичный IP-адрес из списка зарезервированных заранее статических адресов. Подробнее читайте в разделе [{#T}](../../../vpc/operations/set-static-ip.md).
        * **Без адреса** — чтобы не назначать публичный IP-адрес.
    * В поле **Внутренний адрес** выберите способ назначения внутренних адресов: **Автоматически** или **Вручную**.
    * (опционально) Создайте запись для ВМ в [зоне DNS](../../../dns/concepts/dns-zone.md). Разверните блок **Настройки DNS для внутренних адресов**, нажмите кнопку **Добавить запись** и укажите зону, FQDN и время жизни записи. Подробнее см. [Интеграция Cloud DNS с Compute Cloud](../../../dns/concepts/compute-integration.md).
    * Выберите [подходящие группы безопасности](../../../vpc/concepts/security-groups.md) (если соответствующего поля нет, для виртуальной машины будет разрешен любой входящий и исходящий трафик).

1. В блоке **Доступ** укажите данные для доступа на виртуальную машину:
    * (опционально) Выберите или создайте [сервисный аккаунт](../../../iam/concepts/index.md#sa). Использование сервисного аккаунта позволяет гибко настраивать права доступа к ресурсам.

        Для ВМ с операционной системой на базе Linux:
    * В поле **Логин** введите имя пользователя.

     {% note alert %}

     Не используйте логин `root` или другие имена, зарезервированные операционной системой. Для выполнения операций, требующих прав суперпользователя, используйте команду `sudo`.

     {% endnote %}

    * В поле **SSH-ключ** вставьте содержимое файла [открытого ключа](../../../compute/operations/vm-connect/ssh.md#creating-ssh-keys).

        Для ВМ с операционной системой на базе Windows:
    * При создании виртуальной машины в операционной системе будет автоматически создан пользователь `Administrator`. В поле **Пароль** задайте пароль для этого пользователя, с которым можно будет войти на виртуальную машину по RDP.

        {% include [password-requirements](../../compute/password-requirements.md) %}

    * (опционально) При необходимости разрешите доступ к [серийной консоли](../../../compute/operations/index.md#serial-console).

1. Нажмите кнопку **Создать ВМ**.

Виртуальная машина появится в списке.