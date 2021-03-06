# Задание #3 Key-value хранилище, очередь сообщений, паттерн publish-subscribe.

Задание делается на базе задания #2 и задания #1.

Компонент *Backend* теперь должен помещать принятые данные в **Redis**-хранилище по сгенерированному идентификатору в качестве ключа и помещать сообщение **TextCreated** в брокер очередей *RabbitMQ* (в сообщении содержится ид-р текста). Название очереди (exchange в терминах *RabbitMQ*) – **backend-api**.

Добавляется новый компонент - консольное приложение **TextListener**. При запуске компонент начинает слушать сообщения, отправляемые компонентом *Backend* (необходимо в *RabbitMQ* настроить привязки очереди к exchange **backend-api**). Получив сообщение **TextCreated**, компонент извлекает из *Redis*-хранилища текст по идентификатору, полученному в сообщении, и выводит в консоль значение идентификатора и текст.

Скрипты автоматизации должны быть модифицированы для запуска и остановки системы с учётом нового компонента.

Ссылки на библиотеки:

1. RabbitMQ https://www.nuget.org/packages/RabbitMQ.Client/
2. Redis https://www.nuget.org/packages/StackExchange.Redis/
