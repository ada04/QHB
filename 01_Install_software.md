https://repo.quantom.info/qhb/std-1/doc/1.5.1/ru/Appendix/download.html#qhb-для-ubuntu-1804-и-2204

Для подключения к репозиторию выполните следующую команду:

    sudo     apt install gnupg2 apt-transport-https wget

Для корректной работы репозитория СУБД «Квант-Гибрид» в файле конфигурации репозиториев /etc/apt/sources.list должна быть добавлена запись:
`ubuntu  [arch=amd64] https://repo.quantom.info/qhb/std-1/ubuntu/22/ stretch main`

Установите репозиторий программного продукта СУБД «Квант-Гибрид» командой:

    sudo wget -qO - https://repo.quantom.info/qhb/keys/RPM-GPG-KEY-qhb --no-check-certificate | sudo apt-key add -

Далее выполните команды:

    sudo echo 'deb https://repo.quantom.info/qhb/std-1/ubuntu/22 stretch main' >> /etc/apt/sources.list

и

    sudo apt update

Установите бинарные пакеты командой:

    sudo apt install qhb-core [qhb-contrib] [qcp] [qdl] [qdlm] [qbackup] [metricsd] [qhb-serial] [qhb-license-bin] [...]

Например:

    sudo apt install qhb-core

В результате установки пакета ядра QHB будет создан пользователь qhb. Ядро QHB, по умолчанию, установится в каталог /usr/local/qhb.

Многие утилиты QHB устанавливаются в каталог /usr/local/qhb/bin. Если этот каталог указать в переменной окружения $PATH, это облегчит их запуск.
    
    sudo mkdir /opt/qhb
    sudo chown qhb:qhb /opt/qhb /usr/local/qhb
    sudo su - qhb
    echo 'export PATH=/usr/local/qhb/bin:$PATH' >> ~/.profile

Инициализируйте кластер баз данных при помощи утилиты initdb или qhb_bootstrap. В данном примере /opt/qhb/data — расположение каталога базы данных.

    /usr/local/qhb/bin/qhb_bootstrap -D /opt/qhb/data -U qhb

 You can now start the database server using:

    /usr/local/qhb/bin/qhb_ctl -D /opt/qhb/data -l logfile start

**Настройка сервиса**
https://repo.quantom.info/qhb/std-1/doc/1.5.1/ru/Guides/how-to-setup-service.html
