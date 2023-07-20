# Домашнее задание к занятию 2 «Работа с Playbook»

## Подготовка к выполнению

1. * Необязательно. Изучите, что такое [ClickHouse](https://www.youtube.com/watch?v=fjTNS2zkeBs) и [Vector](https://www.youtube.com/watch?v=CgEhyffisLY).
2. Создайте свой публичный репозиторий на GitHub с произвольным именем или используйте старый.
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.

![0  download](https://github.com/malkops/ansible-practice/assets/44001733/a699882e-c891-4f38-a676-db8451b7149b)

4. Подготовьте хосты в соответствии с группами из предподготовленного playbook.

![image](https://github.com/malkops/ansible-practice/assets/44001733/f1db14cb-4728-46c7-8961-a361cfdab563)

## Основная часть

1. Подготовьте свой inventory-файл `prod.yml`. - _**[подготовил](playbook/inventory/prod.yml)**_
2. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает [vector](https://vector.dev).
3. При создании tasks рекомендую использовать модули: `get_url`, `template`, `unarchive`, `file`.
4. Tasks должны: скачать дистрибутив нужной версии, выполнить распаковку в выбранную директорию, установить vector.
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.

![5 lint](https://github.com/malkops/ansible-practice/assets/44001733/41c347be-23f8-4a0f-ba1f-cdf4fe52923b)

6. Попробуйте запустить playbook на этом окружении с флагом `--check`.

![6  check](https://github.com/malkops/ansible-practice/assets/44001733/c09d3f4d-6744-4eb7-960c-2b6381901f16)

7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены. - _**[убедился раз](tmp/ansible-log1)**_
8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен. - _**[убедился два](tmp/ansible-log2)**_
9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. - _**[README.md](playbook/README.md)**_
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-02-playbook` на фиксирующий коммит, в ответ предоставьте ссылку на него.
