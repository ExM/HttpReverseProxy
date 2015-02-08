# HttpReverseProxy
Обучающий проект: HTTP реверс прокси с возможностью конфигурации по WebAPI

# WebAPI 
Формат сообщений JSON.
Авторизация basic-authentication (http://www.asp.net/web-api/overview/security/basic-authentication)
Пользователи должны храниться в БД. 

## GET api/route (auth)
возвращает список перенаправлений

## GET api/route/name1/log (auth)
возвращает список последних запросов принятых по перенаправлению "name1"

## POST api/route (auth)
{
	source: "name1",
	destination: "http:\\internaldevserver1.company.com\testServer"
}
замена перенаправления запроса.

## DELETE api/route/name1 (auth)
удаляет перенаправление и лог запросов

## * proxy/name1 (anonymus)

любые запросы начинающиеся данного адреса будут перенаправлены на указанный URL со всеми заголовками.
Например:
PUT proxy/name1 будет преобразован в
PUT http:\\internaldevserver1.company.com\testServer

GET proxy/name1/testApi?key=18724569187 будет преобразован в
GET http:\\internaldevserver1.company.com\testServer\testApi?key=18724569187

заголовок HOST будет заменен на "internaldevserver1.company.com"

ответ будет перенаправнен в текущем запросе.
запрос и ответ со всеми заголовками будут залогированы.

# Хранение в БД
Хранилище MongoDB. (версия драйвера - 2.0)
* перенапрвления
* пользователи
* лог запросов