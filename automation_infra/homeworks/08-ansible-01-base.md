# Домашнее задание к занятию "08.01 Введение в Ansible"

## Основная часть
1. Попробуйте запустить playbook на окружении из `test.yml`, зафиксируйте какое значение имеет факт `some_fact` для указанного хоста при выполнении playbook'a.

```bash
ok: [localhost] => {
    "msg": "12"
}
```

1. Найдите файл с переменными (group_vars) в котором задаётся найденное в первом пункте значение и поменяйте его на 'all default fact'. - _**[all/examp.yml_origin](https://github.com/Wollfik/devops-netology/blob/main/automation_infra/homeworks/tmp/ans%20/01/group_vars/all/examp.yml_origin)**_
2. Воспользуйтесь подготовленным (используется `docker`) или создайте собственное окружение для проведения дальнейших испытаний.
3. Проведите запуск playbook на окружении из `prod.yml`. Зафиксируйте полученные значения `some_fact` для каждого из `managed host`.

```bash
ok: [centos7] => {
    "msg": "el"
}
ok: [ubuntu] => {
    "msg": "deb"
```

5. Добавьте факты в `group_vars` каждой из групп хостов так, чтобы для `some_fact` получились следующие значения: для `deb` - 'deb default fact', для `el` - 'el default fact'. - _**[deb](https://github.com/Wollfik/devops-netology/blob/main/automation_infra/homeworks/tmp/ans%20/01/group_vars/deb/examp.yml) и [el](https://github.com/Wollfik/devops-netology/blob/main/automation_infra/homeworks/tmp/ans%20/01/group_vars/el/examp.yml)**_
6. Повторите запуск playbook на окружении `prod.yml`. Убедитесь, что выдаются корректные значения для всех хостов.

```bash
ok: [centos7] => {
    "msg": "el default fact"
}
ok: [ubuntu] => {
    "msg": "deb default fact"
}
```

7. При помощи `ansible-vault` зашифруйте факты в `group_vars/deb` и `group_vars/el` с паролем `netology`. - _**`ansible-vault encrypt nah/automation_infra/homeworks/tmp/ans/01/group_vars/deb/examp.yml tmp/ans/01/group_vars/el/examp.yml`**_
8. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь в работоспособности. - _**`ansible-playbook -i tmp/ans/01/inventory/prod.yml tmp/ans/01/site.yml --ask-vault-pass`**_
9.  Посмотрите при помощи `ansible-doc` список плагинов для подключения. Выберите подходящий для работы на `control node`.
10.  В `prod.yml` добавьте новую группу хостов с именем  `local`, в ней разместите localhost с необходимым типом подключения. - _**[prod.yml](https://github.com/Wollfik/devops-netology/blob/main/automation_infra/homeworks/tmp/ans%20/01/inventory/prod.yml)**_
11.  Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь что факты `some_fact` для каждого из хостов определены из верных `group_vars`. - _**ansible-playbook -i tmp/ans/01/inventory/prod.yml tmp/ans/01/site.yml --ask-vault-pass**_

```bash
ok: [centos7] => {
    "msg": "el default fact"
}
ok: [ubuntu] => {
    "msg": "deb default fact"
}
ok: [localhost] => {
    "msg": "all default fact"
}
```

12.  Заполните `README.md` ответами на вопросы. Сделайте `git push` в ветку `master`. В ответе отправьте ссылку на ваш открытый репозиторий с изменённым `playbook` и заполненным `README.md`.
