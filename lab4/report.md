University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4112c\
Author: Grachev Alexandr Andreevich\
Lab: Lab4\
Date of create: 28.10.2023\
Date of finished: 

___
1) Запуск Minikube с плагином CNI Calico  ``minikube start --cni=calico --nodes=2``

2) Проверка работы CNI плагина Calico и количество нод командами:
- ``kubectl get nodes``
- ``kubectl get pods -n kube-system -l k8s-app=calico-node``

  ![nodes](https://github.com/n1ght-lil-bugmaker/itmo_distributed_systems/blob/main/lab4/nodes.png?raw=true)

[nodes]

Для проверки IPAM (IP Address Management), назначим метки узлам. Присвоем метку географического расположения: location=us-east и location=us-west, для соответсвующих нод.\
``kubectl label nodes minikube location=us-east``\
``kubectl label nodes minikube-m02 location=us-west``

3) Манифест с определениями IP Pool'ов: [ippool.yaml](ippool.yaml)

4) Манифест [Deployment.yaml](deployment.yaml)
5) Манифест [service.yaml](service.yaml) 
6) Установка calicoctl: ``kubectl create -f calicoctl.yaml``
7) Создание IP пулов: ``kubectl exec -i -n kube-system calicoctl -- /calicoctl create -f - < ippool.yaml --allow-version-mismatch``
8) Вывод информации о пулах: ``kubectl exec -i -n kube-system calicoctl -- /calicoctl get ippool -o wide   --allow-version-mismatch``
9) Открываем доступ к сервису Minikube: ``minikube service frontend-service``
10) Проброс портов: ``kubectl port-forward service/frontend-service 9090:9090``

11) Получение IP и пинг:
- ``kubectl get pods -o wide``
- ``kubectl exec -it frontend-<first_pod> -- /bin/sh``
- ``ping 10.244.120.67``

  ![ping](https://github.com/n1ght-lil-bugmaker/itmo_distributed_systems/blob/main/lab4/ping.png?raw=true)
___

### Схема

![schema](https://github.com/n1ght-lil-bugmaker/itmo_distributed_systems/blob/main/lab4/schema.png?raw=true)

