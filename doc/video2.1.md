## Обзор наиболее востребованных технологий, которые будут изучаться на курсе TopJava. Часть 1

## ![video](https://cloud.githubusercontent.com/assets/13649199/13672715/06dbc6ce-e6e7-11e5-81a9-04fbddb9e488.png) 2.1. [Видео](https://drive.google.com/file/d/1foI_YIiQWM3Q3h928Fj8eqykY4NSx7Yp)

В курсе TopJava предпочтение отдается наиболее востребованным
технологиям, используемым Java Enterprise разработчиками.  
В этом уроке мы приведем результаты некоторых популярных опросов,
после чего у вас появится общая картина того, инструменты каких 
типов используются в Java мире и какие из них наиболее востребованы.  

---

Ссылки на отчеты, которые будут использоваться в этом уроке:

- [JVM Ecosystem Report 2021](https://snyk.io/jvm-ecosystem-report-2021/)
- [Jetbrains Java Dev Ecosystem Report 2021](https://www.jetbrains.com/lp/devecosystem-2021/java/)
- [JRebel 2021 Java Technology Repost](https://www.jrebel.com/blog/2021-java-technology-report)
- [Top 5 Java ORM tools - 2022](https://www.knowledgefactory.net/2021/09/top-java-orm-tools-20XX.html)

---

### Языки программирования

#### 1. Java
Java по прежнему является абсолютным лидером как среди языков, 
работающих на Java Virtual Maсhine, так и в целом среди 
строго-типизированных backend языков, что показывают нам все рейтинги.

#### 2. Kotlin
Kotlin показывает впечатляющий рост, но Java по прежнему 
существенно опережает его. JVM ecosystem report за 2021 показывает, 
что  91% опрошенных разработчиков используют Java и 17.7% используют Kotlin.

#### 3. Groovy
Groovy занимает третье место в рейтинге.   
Groovy это дополнение к Java. Его особенность заключается 
в том, что он поддерживает не только статическую, 
но и динамическую типизацию. Он отлично подходит для 
написания скриптов. Например на нем пишут скрипты для 
сборки проектов на Gradle. Но также для него разработан 
ряд фреймворков, что позволяет использовать его для 
самых разнообразных задач.

#### 4. Scala
Scala это статически типизированный язык с поддержкой 
функционального программирования, разработанный с целью 
решить ряд проблем, за который Java подвергается критике. 
Однако на сегодняшний день Scala сильно отстает от Java 
и занимает всего 10%.   
Очевидно, что для максимизации шансов на трудоустройство мы учим Java.
---
Если речь идет о бэкэнд разработке, то Kotlin обычно изучается 
после освоения Java. Иначе может обстоять дело с мобильной разработкой, 
где Kotlin выходит на первое место. 

Кстати у нас готовится курс [TopKotlin](https://javaops.ru/view/topkotlin), 
который будет являться продолжением курса TopJava.

Scala существенно сложнее Java, для ее полного освовения 
требуется 2-3 года и ей на замену идет Kotlin. 

### Среда разработки
IntelliJ Idea является абсолютным лидером среди IDE 
и занимает более чем 70%. При этом более 50% опрошенных используют
платную версию IntelliJ IDEA Ultimate.   
Безусловно полезно познакомиться с функциями, которые 
предоставляет платная версия. Например в платной версие есть 
встроенный модель для того, чтобы вручную взаимодействовать
с базой данных.   
Однако, бессплатная Community версия также используется компаниями.
На ней можно полноценно работать со спрингом и другими фреймворками, 
но некоторые полезные интеграции например клиент для 
баз данных приходится заменять отдельными программами, 
например можно использовать DBeaver.

### Инструменты для сборки (building tools)
Для того, чтобы быстро и эффективно работать с библиотеками 
и фреймворками, которые мы используем в проекте - а это 
часто десятки или даже сотни java архивов, которые мы 
должны скачать из интернета и подключить к проекту, 
используются средства сборки или building tools. 
Они также позволяют быстро собрать все используемые 
нами файлы в один джава архив (jar файл) или вэб-архив (war файл), 
готовый для запуска.   

Помимо упомянутых функций средства сборки также позволяют 
запускать тесты перед сборкой, проверять покрытие кода тестами, 
использовать различные дополнительные плагины, которые могут 
генерировать отчеты, документацию и выполнять множество других полезных функций.
Наиболее популярными средствами сборки для Java являются Maven и Gradle.

Несмотря на то, что Gradle является более гибким инструментом, 
Maven по прежнему опережает его почти вдвое, занимая 76%.  
В курсе мы отдаем предпочтение ему.

Для общего понимания. Различия между Maven и Gradle заключаются 
в том, что в Maven используется XML файлы, в которых прописывается 
вся конфигурация для сборки.  
XML это структурированный документ, в котором мы можем писать элементы 
в соответствии с ранее заданной схемой.
Существует проект maven polyglot, где конфигурация сборки 
прописывается в формате json, но на продакшене мы его не 
встречали, видимо проект не взлетел. Поэтому в случае с 
Maven обычно используется традиционный XML формат.

В случае с Gradle вместо XML файлов используются скрипты 
для сборки, написанные на языках программирования Groovy DSL 
или Kotlin DSL. Это позволяет писать более сложные и гибкие алгоритмы сборки.  

На наш взгляд Maven более понятен и последователен, 
чем Gradle, IntelliJ IDEA с ним лучше интегрирована и 
он подходит для подавляющего большинства проектов.

### Application server
Мы переходим к секции с наиболее популярными апликейшен серверами 
и видим, что первое место занимает Tomcat.   
Технически Tomcat это не аппликейшен сервер, а контейнер 
сервлетов - Java программа, реализующая Java Servlet API 
и - обеспечивающая взаимодействие с внешним миром с помощью HTTP протокола. 

Контейнер сервлетов принимает HTTP запросы, возвращать ответы. 
Работает непрерывно за исключением каких то технических работ, 
что дает возможность обращаться к приложению через сеть в любое время. 
Application server расширяет функциональность контейнера сервлетов.

Tomcat занимает наибольший вес среди контейнеров сервлетов 
(TomEE- application server на его основе). 
Он может быть установлен на компьютер , после чего 
в нем может быть развернут  или задеплоен web archive файл 
с вашим приложением. 
Также Spring Boot предоставляет Tomcat в качестве 
встроенного, или embeded сервера, что позволяет запускать 
приложение как обычный java процесс -  локально, на сервере или в облаке.

### Обзор пройденных тем
Давайте подведем промежуточные итоги по результатам этого урока.

- В этом уроке мы познакомились с текущими позициями Java и 
других языков программирования - Java уверенно сохраняет лидерство.  

- Также поговорили о средах разработки, где IntelliJ Idea занимает
лидирующие позиции.


- Обсудили что что такое средства для сборки или Build tools и 
подтвердили статистикой популярности наш выбор в пользу Maven, 
а также поговорили о контейнерах сервлетов и аппликейшен серверах, 
где Tomcat выглядит как очевидный выбор.







