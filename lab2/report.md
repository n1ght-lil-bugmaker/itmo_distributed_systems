University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4112c\
Author: Grachev Alexandr Andreevich\
Lab: Lab2\
Date of create: 28.10.2023\
Date of finished: \

___

1) Создан [deployment](lab2_deployment.yaml) с 2 контейнерами ifilyaninitmo/itdt-contained-frontend:master
REACT_APP_USERNAME = '_testUserName', 
REACT_APP_COMPANY_NAME: = '_testCompanyName'
``kubectl apply -f lab2_deployment.yaml``

2) Получение имен созданных контейнеров: ``kubectl get pods``
3) Запуск режима проброса портов: ``kubectl port-forward frontend-deployment.. 3001:3000``
4) Смотрим через браузер веб-интерфейс:



5) Логи контейнеров: ``kubectl logs frontend-deployment..``


___

### Схема
