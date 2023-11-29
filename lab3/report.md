University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4111c\
Author: Grachev Alexandr Andreevich\
Lab: Lab3\
Date of create: 28.10.2023\
Date of finished:

___
1) Cоздание и применение configMap [configmap_3.yaml](configmap_3.yaml) ``kubectl apply -f configmap_3.yaml``

2) Cоздание и применение replicaSet [replicaset_3.yaml](replicaset_3.yaml) с 2 репликами контейнера ``ifilyaninitmo/itdt-contained-frontend:master`` 
(REACT_APP_USERNAME, REACT_APP_COMPANY_NAME подтягиваются из предыдущего файла): ``kubectl apply -f replicaset_3.yaml``

3) Создание и применение service [service_3.yaml](service_3.yaml): ``kubectl apply -f service_3.yaml``

4) Включение Ingress: ``minikube addons enable ingress``

5) Генерация TLS сертификата: ``openssl req -x509 -newkey rsa:4096 -sha256 -days 40 -nodes -keyout tls.key -out tls.crt -subj "/CN=lab3.front.com"``

6) Импорт сертификата в minikube: ``kubectl create secret tls lab3-local-tls --cert=tls.crt --key=tls.key``

7) Cоздание ingress [ingress_3.yaml](ingress_3.yaml) в minikube, где указан ранее импортированный сертификат, FQDN и имя сервиса и его применение: ``kubectl apply -f ingress.yaml``

8) Добавление адреса lab3.front.local в /etc/hosts: ``127.0.0.1 lab3.front.local``

9) Создаем туннель между локальной машиной и Minikube кластером: ``minikube tunnel``

10) Вход в веб приложение по FQDN используя HTTPS и проверка наличия сертификата: https://lab3.front.local

    ![certs](https://github.com/n1ght-lil-bugmaker/itmo_distributed_systems/blob/main/lab3/certinfo.png?raw=true)


### Схема

![schema](https://github.com/n1ght-lil-bugmaker/itmo_distributed_systems/blob/main/lab3/schema.png?raw=true)
