https://repo.quantom.info/qhb/std-1/doc/1.5.1/ru/Appendix/download.html#qhb-для-ubuntu-1804-и-2204

Для подключения к репозиторию выполните следующую команду:

    apt install gnupg2 apt-transport-https wget

Для корректной работы репозитория СУБД «Квант-Гибрид» в файле конфигурации репозиториев /etc/apt/sources.list должна быть добавлена запись:

    ubuntu  [arch=amd64] https://repo.quantom.info/qhb/std-1/ubuntu/22/ stretch main

Установите репозиторий программного продукта СУБД «Квант-Гибрид» командой:

    wget -qO - https://repo.quantom.info/qhb/keys/RPM-GPG-KEY-qhb --no-check-certificate | apt-key add -

Далее выполните команды:

    echo 'ubuntu https://repo.quantom.info/qhb/std-1/ubuntu/22 stretch main' >> /etc/apt/sources.list

и

    apt update

Установите бинарные пакеты командой:

    apt install qhb-core [qhb-contrib] [qcp] [qdl] [qdlm] [qbackup] [metricsd] [qhb-serial] [qhb-license-bin] [...]

Например:

    apt install qhb-core

В результате установки пакета ядра QHB будет создан пользователь qhb. Ядро QHB, по умолчанию, установится в каталог /usr/local/qhb.

Многие утилиты QHB устанавливаются в каталог /usr/local/qhb/bin. Если этот каталог указать в переменной окружения $PATH, это облегчит их запуск.
