# Описание playbook

Playbook скачивает и устанавливает пакеты версии `22.3.3.44` под RPM based системы `clickhouse-client`, `clickhouse-server`, `clickhouse-common-static`.

Если необходима другая версия, её можно изменить в директории с переменными `group_vars/clickhouse/vars.yml`.

После установки создается БД logs и таблица mytable с одинм полем `message String`.

Изменен адрес доступа clickhouse-server с localhost на 0.0.0.0.

После установки clickhouse, происходит установка vector'а версии `0.30.0` в директорию `/opt/vector`, путем скачивания архива и создания systemd service.
Запуск происходит от пользователя `vector`, который также создается в playbook.

Конфигурационный файл vector лежит в директории templates.
Systemd service лежит в директории templates.

После установки vector, происходит установка lighthouse для просмотра логов в директорию `/opt/lighthouse`. Также для lighthouse будет установлен `nginx` со стандартной конфигурацией и минимальной конфиграцией для lighthouse в `/etc/nginx/conf.d/`. Саму конфигурацию можно посмотреть в [templates/lighthouse-nginx.conf.j2](templates/lighthouse-nginx.conf.j2).
