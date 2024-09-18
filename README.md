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

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-01-04.png)

Ответ: curl: (52) Empty reply from server - curl: (52) Пустой ответ от сервера. Наверное надо как-то по другому получить ответ от echoserver:2.2.

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-01-05.png)

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

    kubectl port-forward hello-world 31000:80

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-07.png)

Ответ: curl: (52) Empty reply from server - curl: (52) Пустой ответ от сервера. Всё-таки надо как-то по другому получить ответ от echoserver:2.2.

![](https://github.com/artmur1/22-02-kuber-base/blob/main/img/22-02-02-08.png)

------

### Правила приёма работы

1. Домашняя работа оформляется в своем Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода команд `kubectl get pods`, а также скриншот результата подключения.
3. Репозиторий должен содержать файлы манифестов и ссылки на них в файле README.md.

------

### Критерии оценки
Зачёт — выполнены все задания, ответы даны в развернутой форме, приложены соответствующие скриншоты и файлы проекта, в выполненных заданиях нет противоречий и нарушения логики.

На доработку — задание выполнено частично или не выполнено, в логике выполнения заданий есть противоречия, существенные недостатки.
