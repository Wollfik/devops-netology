# Домашнее задание к занятию 3 «Использование Ansible»

## Подготовка к выполнению

1. Подготовьте в Yandex Cloud три хоста: для `clickhouse`, для `vector` и для `lighthouse`.

![01](https://github.com/malkops/ansible-practice/assets/44001733/fcdc5ac0-4946-4ee9-b70d-554e7d4f9ea6)

2. Репозиторий LightHouse находится [по ссылке](https://github.com/VKCOM/lighthouse).

## Основная часть

1. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает LightHouse. - _**[подготовил и очистил](playbook/inventory/prod.yml)**_
2. При создании tasks рекомендую использовать модули: `get_url`, `template`, `yum`, `apt`.
3. Tasks должны: скачать статику LightHouse, установить Nginx или любой другой веб-сервер, настроить его конфиг для открытия LightHouse, запустить веб-сервер.
4. Подготовьте свой inventory-файл `prod.yml`.
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.

![5](https://github.com/malkops/ansible-practice/assets/44001733/5cf6d3ed-81c2-40d0-b12e-e463af8c00f6)

6. Попробуйте запустить playbook на этом окружении с флагом `--check`. - _**[попробовал - не пошло](tmp/check.log)**_
7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены. - _**[убедился раз](tmp/run2.log)**_
8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен. - _**[убедился два](tmp/run1.log)**_
9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. - _**[README.md](playbook/README.md)**_
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-03-yandex` на фиксирующий коммит, в ответ предоставьте ссылку на него.
