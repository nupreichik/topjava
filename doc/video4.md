## Структура приложения (многоуровневая архитектура)
## ![video](https://cloud.githubusercontent.com/assets/13649199/13672715/06dbc6ce-e6e7-11e5-81a9-04fbddb9e488.png) 3. [Видео](https://drive.google.com/file/d/1UHzSy9i-uonmTMFoR5v69Y-vyWLCLQWd)

Приложение, которое мы будем разрабатывать это [программа для подсчета калорий](http://javaops-demo.ru/topjava).

В этом видео давайте обсудим структуру этого приложения.

---
Ссылки на отчеты, которые будут использоваться в этом уроке:

- [Многоуровневая архитектура (русскоязыная статья в Wikipedia)](https://ru.wikipedia.org/wiki/%D0%9C%D0%BD%D0%BE%D0%B3%D0%BE%D1%83%D1%80%D0%BE%D0%B2%D0%BD%D0%B5%D0%B2%D0%B0%D1%8F_%D0%B0%D1%80%D1%85%D0%B8%D1%82%D0%B5%D0%BA%D1%82%D1%83%D1%80%D0%B0)
- [Multitier architecture (англоязычная статья в Wikipedia)](https://en.wikipedia.org/wiki/Multitier_architecture)

---

<img src="https://javaops.ru/static/images/projects/top-scheme.jpg" />

На структурной схеме приложения вы видите, что оно условно разделено на 4 части - **Views**, 
**Controller**, **Service** и **Repository**.

Такой подход является реализацией многоуровневой архитектуры в программировании. 
По английски этот подход называется **_Multitier architecture_**.

Его суть заключение в разделении приложения на несколько слоев, 
каждый из которых ответственен за конкретную задачу.

### Слой отображения (view)
Views соответствует слою отображения (или presentation layer) - это user interface или 
фронтэнд - все то, что мы видим и с чем взаимодействуем в браузере.
В качестве View могут быть HTML страницы, созданные с использованием специальных 
движков шаблонов, например JSP (встроен в Tomcat) или 
Thymeleaf (шаблоны по умолчанию в Spring Boot) или отдельное frontend приложение, 
написанное на одном из JavaScript фреймворков. 

В случае с движками шаблонов, HTML страницы будут располагаться в одном проекте 
с основным кодом приложения. Для приложений с “небогатым UI используются именно шаблоны.
Этот подход отличается от так называемых RIA - rich internet application - приложений со сложным UI).

Главное отличие rich internet application от приложений с фронтендом 
на движках шаблонов заключается в том, что фронтенд, созданный на движке 
шаблонов работает на сервере и это что-то простое. 
В случае с rich internet application фронтэнд приложение загружается 
через интернет к вам на компьютер и запускается в браузере. 
Оно может быть максимально сложным и выполнять функции традиционных 
десктоп приложений.
Иногда в одном приложении смешиваются оба способа - например страница 
логина-пароля в RIA делаются на шаблонах.

Создание простого фронтэнда на движке шаблонов проще, поэтому 
в курсе мы будем использовать этот способ.

### Слой контроллеров (Controller)
Следующий слой, который мы видим - это **Controller**.

В многоуровневой архитектуре он соответствует слою, который 
называется “**_Слой приложения_**" или "**_Application layer_**"). 
В GRASP (General Responsibility Assignment Software Patterns) 
он так и называется - Controller layer.

Это слой приложения, который ответственен за обработку HTTP запросов и проверку корректности входных данных. Если мы открываем главную страницу на сайте или отправляем заполненную на сайте форму, фронтэнд приложение отправляет HTTP запрос к серверу (в нашем случае контейнеру сервлетов), который принимает запрос и перенаправляет его в контроллер, соответствующий введенному в браузере URL адресу, или к адресу, который вызывается при отправке формы через сайт.
Также контроллеры могут принимать запросы не только от фронтенда, но и от других приложений.

Слой контроллеров не имеет доступа к базе данных. Контроллеры общаются только с сервисами.

### Слой сервисов (Service layer)
Слой **Service** на схеме приложения соответствует слою 
бизнес-логики (или **_Business layer_**) в многоуровневой архитектуре.  
В слое service заключена (инкапсулирована) вся бизнес-логика нашего приложения. 
Если коммуникация с фронтендом или другими приложениями, 
то есть прием данных, это ответственность контроллеров, 
то обработка данных это ответственность сервисов.

### Слой доступа к данным (Data layer)
Слой сервисов общается со слоем, ответственным за работу с базами данных. 
Этот слой называют **Data layer** (также можно встретить 
названия **Persistence Layer** или **Data access layer**) и он 
представлен в виде **_Data Access Object_** классов 
(коротко **_DAO классы_**) или классов, реализующих паттерн репозиторий. 
С обоими видами классов вы попрактикуетесь в ходе курса.  
[Репозиторий это также один из архитектурных паттернов](https://martinfowler.com/eaaCatalog/repository.html)

Подобное разделение приложения на слои дает гибкость 
и существенно упрощает доработку и переиспользование приложения.
Например, создав по такому принципу приложение, 
содержащее слои репозиториев, сервисов и контроллеров 
мы в дальнейшем можем легко использовать это приложение 
с различными фронтенд приложениями или мобильными приложениями.
Если мы решим перейти на другую базу данных, мы можем 
переписать только слой репозиториев и нам не требуется 
вносить изменения в слои сервисов и контроллеров.

>Для маленького приложение такой подход может показаться 
>избыточно сложным, но по мере роста приложения это является спасением.

Подавляющее большинство реальных приложений построены с использованием именно этой архитектуры.

### Краткие итоги
В этом видео мы познакомились с концепцией многоуровневой архитектуры, 
которую мы применим при создании приложения на курсе.
Многоуровневая архитектура предполагает разделение приложения на слои:
- Views - слой отображения является фронтэндом;
- Controller - слой приложения ответственен за прием и валидацию входных данных;
- слой Service включает в себя весь код, отражающий бизнес логику;
- Repository или Data layer отвечает за взаимодействие с базой данных.

Также мы обсудили какие преимущества дает такой подход. 
Среди преимуществ в первую очередь возможность повторного 
использования различных слоев и упрощение их доработки и изменения.



