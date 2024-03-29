
# Домашнее задание к занятию 5. «Оркестрация кластером Docker контейнеров на примере Docker Swarm»

## Как сдавать задания

Обязательны к выполнению задачи без звёздочки. Их нужно выполнить, чтобы получить зачёт и диплом о профессиональной переподготовке.

Задачи со звёдочкой (*) — это дополнительные задачи и/или задачи повышенной сложности. Их выполнять не обязательно, но они помогут вам глубже понять тему.

Домашнее задание выполните в файле readme.md в GitHub-репозитории. В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории.

Любые вопросы по решению задач задавайте в чате учебной группы.

---


## Важно

1. Перед отправкой работы на проверку удаляйте неиспользуемые ресурсы.
Это нужно, чтобы не расходовать средства, полученные в результате использования промокода.
Подробные рекомендации [здесь](https://github.com/netology-code/virt-homeworks/blob/virt-11/r/README.md).

2. [Ссылки для установки открытого ПО](https://github.com/netology-code/devops-materials/blob/master/README.md).

---

## Задача 1

Дайте письменые ответы на вопросы:

- В чём отличие режимов работы сервисов в Docker Swarm-кластере: replication и global? - **_При global контейнеры будут разворачиваться на всех нодах в кластере, а при replication можно задать правила развертывания конейтнеров. Например количество реплик для развертывания 3 реплики._**
- Какой алгоритм выбора лидера используется в Docker Swarm-кластере? - **_Raft алгоритм, который подразумевает выборы по определенному таймауту._**
- Что такое Overlay Network? - **_Overlay Network - это распределенная сеть, в которой взаимодействуют узлы docker демона. При создании network, этот тип сети выбирается по умолчанию._**

## Задача 2

Создайте ваш первый Docker Swarm-кластер в Яндекс Облаке.

![Screenshot](https://github.com/Wollfik/Myrepoz/blob/main/12121212.png)

## Задача 3

Создайте ваш первый, готовый к боевой эксплуатации кластер мониторинга, состоящий из стека микросервисов.

Чтобы получить зачёт, предоставьте скриншот из терминала (консоли), с выводом команды:

![Screenshot](https://github.com/Wollfik/Myrepoz/blob/main/44444.png)
