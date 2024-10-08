# Домашнее задание к занятию «Базовые объекты K8S» - `Мурчин Артем`

### Цель задания

В тестовой среде для работы с Kubernetes, установленной в предыдущем ДЗ, необходимо развернуть Pod с приложением и подключиться к нему со своего локального компьютера. 

------

### Чеклист готовности к домашнему заданию

1. Установленное k8s-решение (например, MicroK8S).
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключенным Git-репозиторием.

------

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. Описание [Pod](https://kubernetes.io/docs/concepts/workloads/pods/) и примеры манифестов.
2. Описание [Service](https://kubernetes.io/docs/concepts/services-networking/service/).

------

### Задание 1. Создать Pod с именем hello-world

1. Создать манифест (yaml-конфигурацию) Pod.
2. Использовать image - gcr.io/kubernetes-e2e-test-images/echoserver:2.2.
3. Подключиться локально к Pod с помощью `kubectl port-forward` и вывести значение (curl или в браузере).

### Решение 1. Создать Pod с именем hello-world

Написал конфигурацию pod с именем hello-world - https://github.com/artmur1/22-02-kuber-base/blob/main/files/pod-hw.yaml:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-01-01.png)

Под запущен:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-01-02.png)

Описание пода:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-01-03.png)

    kubectl port-forward hello-world 31000:31080

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-01-06.png)

    curl -sS http://127.0.0.1:31000 || echo "Ответ получен!"

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-01-07.png)

------

### Задание 2. Создать Service и подключить его к Pod

1. Создать Pod с именем netology-web.
2. Использовать image — gcr.io/kubernetes-e2e-test-images/echoserver:2.2.
3. Создать Service с именем netology-svc и подключить к netology-web.
4. Подключиться локально к Service с помощью `kubectl port-forward` и вывести значение (curl или в браузере).

### Решение 2. Создать Service и подключить его к Pod

Написал конфигурацию pod с именем netology-web - https://github.com/artmur1/22-02-kuber-base/blob/main/files/pod-netology-web.yaml:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-01.png)

Написал конфигурацию Service с именем netology-svc - https://github.com/artmur1/22-02-kuber-base/blob/main/files/ser-netology-web.yaml:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-02.png)

pod с именем netology-web создан:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-03.png)

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-04.png)

Описание pod с именем netology-web:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-05.png)

Описание Service с именем netology-svc:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-06.png)

    kubectl port-forward svc/netology-svc 31000:80

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-09.png)

    curl -sS http://127.0.0.1:31000 || echo 1

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-10.png)

------

## Доработка 

### Доработка задания 1

Поменял порт в pod с именем hello-world на 8080. Старый под удалил, новый запустил.

![](https://github.com/artmur1/22-02-kuber-base/blob/main/22-02-01-08.png)

    kubectl port-forward hello-world 31000:8080

![](https://github.com/artmur1/22-02-kuber-base/blob/main/22-02-01-09.png)

    curl 127.0.0.1:31000

Видно, что ответ от сервера получен:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/22-02-01-10.png)

### Доработка задания 2

Поменял порт в pod с именем netology-web на 8080. Старый под удалил, новый запустил.

![](https://github.com/artmur1/22-02-kuber-base/blob/main/22-02-02-11.png)

Поменял порт в Service с именем netology-svc на 8080. Старый сервис удалил, новый запустил.

![](https://github.com/artmur1/22-02-kuber-base/blob/main/22-02-02-12.png)

    kubectl port-forward svc/netology-svc 31000:80

![](https://github.com/artmur1/22-02-kuber-base/blob/main/22-02-02-13.png)

    curl 127.0.0.1:31000

Видно, что ответ от сервера получен:

![](https://github.com/artmur1/22-02-kuber-base/blob/main/22-02-02-14.png)

------

### Правила приёма работы

1. Домашняя работа оформляется в своем Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода команд `kubectl get pods`, а также скриншот результата подключения.
3. Репозиторий должен содержать файлы манифестов и ссылки на них в файле README.md.

------

### Критерии оценки
Зачёт — выполнены все задания, ответы даны в развернутой форме, приложены соответствующие скриншоты и файлы проекта, в выполненных заданиях нет противоречий и нарушения логики.

На доработку — задание выполнено частично или не выполнено, в логике выполнения заданий есть противоречия, существенные недостатки.
