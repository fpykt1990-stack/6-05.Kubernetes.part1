***Домашнее задание к занятию «Kubernetes. Часть 1»***

Это задание для самостоятельной отработки навыков и не предполагает обратной связи от преподавателя. Его выполнение не влияет на завершение модуля. Но мы рекомендуем его выполнить, чтобы закрепить полученные знания.

**Задание 1**
Выполните действия:

Запустите Kubernetes локально, используя k3s или minikube на свой выбор.
Добейтесь стабильной работы всех системных контейнеров.

**Ответ 1**

Был установлен kubectl и minikube

![Ответ1](https://github.com/fpykt1990-stack/6-05.Kubernetes.part1/blob/main/img/img-kub-01.png)

**Задание 2**
Есть файл с деплоем:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis
spec:
  selector:
    matchLabels:
      app: redis
  replicas: 1
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
      - name: master
        image: bitnami/redis
        env:
         - name: REDIS_PASSWORD
           value: password123
        ports:
        - containerPort: 6379
Выполните действия:

Измените файл с учётом условий:
redis должен запускаться без пароля;
создайте Service, который будет направлять трафик на этот Deployment;
версия образа redis должна быть зафиксирована на 6.0.13.
Запустите Deployment в своём кластере и добейтесь его стабильной работы.

**Ответ 2**

Был изменен репо с bitnami на bitnamilegacy



![Ответ2](https://github.com/fpykt1990-stack/6-05.Kubernetes.part1/blob/main/img/img-kub-02.png)

![Ответ2](https://github.com/fpykt1990-stack/6-05.Kubernetes.part1/blob/main/img/img-kub-03.png)


**Задание 3**

Выполните действия:

Напишите команды kubectl для контейнера из предыдущего задания:
выполнения команды ps aux внутри контейнера;
просмотра логов контейнера за последние 5 минут;
удаления контейнера;
проброса порта локальной машины в контейнер для отладки.

**Ответ 3**

![Ответ2](https://github.com/fpykt1990-stack/6-05.Kubernetes.part1/blob/main/img/img-kub-04.png)

**Задание 4**

Есть конфигурация nginx:

location / {
    add_header Content-Type text/plain;
    return 200 'Hello from k8s';
}
Выполните действия:

Напишите yaml-файлы для развёртки nginx, в которых будут присутствовать:

ConfigMap с конфигом nginx;
Deployment, который бы подключал этот configmap;
Ingress, который будет направлять запросы по префиксу /test на наш сервис.

**Ответ 4**

В локлаьный minikube был добавлен ingress controller

minikube addons enable ingress

![Ответ4](https://github.com/fpykt1990-stack/6-05.Kubernetes.part1/blob/main/img/img-kub-05.png)

