# Домашнее задание к занятию «Установка Kubernetes»

### Цель задания

Установить кластер K8s.

### Задание 1. Установить кластер k8s с 1 master node

1. Подготовка работы кластера из 5 нод: 1 мастер и 4 рабочие ноды.
2. В качестве CRI — containerd.
3. Запуск etcd производить на мастере.
4. Способ установки выбрать самостоятельно.

Происходит провижен через terraform, необходимо запускать сначала без провижена, потом с ним (раскоментировать)

[Код описан тут](https://github.com/Wollfik/devops-netology/blob/main/automation_infra/homeworks/homeworks/terraform/modules/m1-w4-k8s-cluster/vpc.tf)

[Директория с остальными файлами](https://github.com/Wollfik/devops-netology/tree/main/automation_infra/homeworks/homeworks/terraform/modules/m1-w4-k8s-cluster)

![image](https://github.com/malkops/nah/assets/44001733/28578aab-8cd3-4ce4-a096-313d3a563654)

## Дополнительные задания (со звёздочкой)

**Настоятельно рекомендуем выполнять все задания под звёздочкой.** Их выполнение поможет глубже разобраться в материале.   
Задания под звёздочкой необязательные к выполнению и не повлияют на получение зачёта по этому домашнему заданию. 

------
### Задание 2*. Установить HA кластер

1. Установить кластер в режиме HA.
2. Использовать нечётное количество Master-node.
3. Для cluster ip использовать keepalived или другой способ.
