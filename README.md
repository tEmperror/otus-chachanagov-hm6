# Homework №6 Sergey Chachanagov
## Теоретическая часть.
### Варианты взаимодействий:
1. Только HTTP взаимодействие
   
   ![alt text](scheme1.png)
   
2. Событийное взаимодействие с использованием брокера сообщений для уведомлений
   
   ![alt text](scheme2.png)
   
3. Event Collaboration
   
   ![alt text](scheme3.png)

Вариант, который мне кажется наиболее правильным для решения данной задачи:

№2. Событийное взаимодействие с использованием брокера сообщений для уведомлений



## Практическая часть
Схема приложения:

![alt text](scheme4.png)

Выше приведена схема взаимодействия сервисов.
Аутентификация реализована с использованием forward-auth на Ingress-NGINX.
Пользователю предоставляется REST API. М
ежсервисное взаимодействие используется комбинированного вида:
ORDER взаимодействует с BILLING по REST, а с NOTIFICATION асинхронно с помощью Kafka.
***
Установка приложений в неймспейс order-app

```
helm install app app-chart/ --namespace order-app --create-namespace
helm install auth auth-chart/ --namespace order-app
helm install billing billing-chart/ --namespace order-app
helm install order order-chart/ --namespace order-app
helm install notification notification-chart/ --namespace order-app
```
***
Коллекция постмана - **"Chachanagov-hm6.postman_collection.json"**

Команда для запуска:
```
newman run Chachanagov-hm6.postman_collection.json
```