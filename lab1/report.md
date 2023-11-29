University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4112c\
Author: Grachev Alexandr Andreevich\
Lab: Lab1\
Date of create: 28.10.2023\
Date of finished: 

___

### Установка окружения
1) Установка minikube:

``curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64``\
``sudo install minikube-linux-amd64 /usr/local/bin/minikube``\

2) Запуск: ``minikube start --driver=docker``.\
3) Установка псевдонима kubectl: ``alias kubectl="minikube kubectl --"``\

### Основная часть
1) Создан [манифест](./vault-pod.yaml)\
2) Применение манифеста: ``kubectl apply -f vault-pod.yaml``\
3) Создание cервиса для доступа к поду: ``kubectl expose pod vault --type=NodePort --port=8200``\
4) Проброс портов: ``kubectl port-forward service/vault 8200:8200``\
5) Получение данных для входа в Vault (RootToken): ``kubectl logs vault``\
6) Сервис доступен по адресу http://127.0.0.1:8200\

[8200]

### Завершение
1) Удаление пода: ``kubectl delete pod vault``\
2) Удаление сервиса:  ``kubectl delete service vault``\
3) Остановка работы кластера: ``minikube stop``\

___

### Схема организации контейеров и сервисов
