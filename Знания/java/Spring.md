**Сразу напишу список источников, из которых автор брал материалы**

- Spring 5 Design Patterns
- Spring in Action 4th edition
- Spring Security — Third Edition
- Core Spring 5 Certification in Detail by Ivan Krizsan
- Spring Documentation and Spring API javadocs

И так, начнем.

**Что такое внедрение зависимостей(DI) и в чем его преимущества?**

Внедрение зависимостей — это специальный паттерн, который уменьшает связь между Spring компонентами. Таким образом, при применении DI, ваш код становится чище, проще, его становится легче понять и тестировать.   
Согласно паттерну DI, создание объектов для зависимостей переходит на фабрику или отдается третьей стороне. Это означает, что мы можем сосредоточиться на использовании этих объектов вместо их создания.

**Преимущества DI**

- Уменьшенная связь между частями приложения
- Улучшенное тестирование
- Улучшенная архитектура приложения
- Уменьшает шаблонный код
- Стандартизирует разработку приложения

**Почему для создания Spring beans рекомендуются интерфейсы?**

- Улучшенное тестирование. В тестах бин может быть заменен специальным объектом(mock или stub), который реализует интерфейс бина.
- Позволяет использовать механизм динамических прокси из JDK(например, при создании репозитория через Spring Data)
- Позволяет скрывать реализацию

**Что такое application context?**

В Spring Framework интерфейс`org.springframework.factory.BeanFactory`предоставляет фабрику для бинов, которая в то же время является IoC контейнером приложения. Управление бинами основано на конфигурации(java или xml).

Интерфейс`org.springframework.context.ApplicationContext`— это обертка над bean factory, предоставляющая некоторые дополнительные возможности, например AOP, транзакции, безопасность, i18n, и т.п.

**Что такое контейнер и какой у него жизненный цикл?**

Основа Spring Framework — контейнер, и наши объекты "живут" в этом контейнере.  
Контейнер обычно создает множество объектов на основе их конфигураций и управляет их жизненным циклом от создания объекта до уничтожения.

Контейнер — это объект, реализующий интерфейс **ApplicationContext**.

**Жизненный цикл контейнера**

1. Контейнер создается при запуске приложения
2. Контейнер считывает конфигурационные данные
3. Из конфигурационных данных создается описание бинов
4. BeanFactoryPostProcessors обрабатывают описание бина
5. Контейнер создает бины используя их описание
6. Бины инициализируются — значения свойств и зависимости внедряются в бин
7. BeanPostProcessor запускают методы обратного вызова(callback methods)
8. Приложение запущено и работает
9. Инициализируется закрытие приложения
10. Контейнер закрывается
11. Вызываются callback methods

**Как создать экземпляр ApplicationContext?**

Spring обеспечивает несколько разновидностей контекста. 

Есть несколько основных реализаций интерфейса ApplicationContext:

- FileSystemXmlApplicationContext
- ClassPathXmlApplicationContext
- AnnotationConfigApplicationContext
- XmlWebApplicationContext
- AnnotationConfigWebApplicationContext

Примеры создания контекста:

```
ApplicationContext ctx = new FileSystemXmlApplicationContext(
                                     "c:/bean_properties.xml");

ApplicationContext ctx = new AnnotationConfigApplicationContext(
                            "com.springdemoapp.JavaConfig.class");
```

**Можете ли вы описать жизненный цикл бина в контейнере?**

1. Загрузка описаний бинов, создание графа зависимостей(между бинами)
2. Создание и запуск`BeanFactoryPostProcessors`
3. Создание бинов
4. Spring внедряет значения и зависимости в свойства бина
5. Если бин реализует метод`setBeanName()`из интерфейса NameBeanAware, то ID бина передается в метод
6. Если бин реализует BeanFactoryAware, то Spring устанавливает ссылку на bean factory через`setBeanFactory()`из этого интерфейса.
7. Если бин реализует интерфейс ApplicationContextAware, то Spring устанавливает ссылку на ApplicationContext через`setApplicationContext()`.
8. `BeanPostProcessor`это специальный интерфейс(о нем ниже), и Spring позволяет бинам имплементировать этот интерфейс. Реализуя метод`postProcessBeforeInitialization()`, можно изменить экземпляр бина перед его(бина) инициализацией(установка свойств и т.п.)
9. Если определены методы обратного вызова, то Spring вызывает их. Например, это метод, аннотированный`@PostConstruct`или метод`initMethod`из аннотации`@Bean`.
10. Теперь бин готов к использованию. Его можно получить с помощью метода`ApplicationContext#getBean()`.
11. После того как контекст будет закрыт(метод`close()`из ApplicationContext), бин уничтожается.
12. Если в бине есть метод, аннотированный`@PreDestroy`, то перед уничтожением вызовется этот метод. Если бин имплементирует DisposibleBean, то Spring вызовет метод`destroy()`, чтобы очистить ресурсы или убить процессы в приложении. Если в аннотации`@Bean`определен метод`destroyMethod`, то вызовется и он.  
    ![Подготовка к Spring Professional Certification. Контейнер, IoC, бины - 2](https://www.pvsm.ru/images/2019/10/06/podgotovka-k-Spring-Professional-Certification-konteiner-IoC-biny-2.png "Подготовка к Spring Professional Certification. Контейнер, IoC, бины - 2")

**Как получить ApplicationContext в интеграционном тесте?**

Если вы используете JUnit 5, то вам нужно указать 2 аннотации:

- ```@ExtendWith(TestClass.class)``` — используется для указания тестового класса
- ```@ContextConfoguration(classes = JavaConfig.class)``` — загружает java/xml конфигурацию для создания контекста в тесте

Можно использовать аннотацию[`@SpringJUnitConfig`](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/test/context/junit/jupiter/SpringJUnitConfig.html), которая сочетает обе эти аннотации.  
Для теста веб-слоя можно использовать аннотацию[`@SpringJUnitWebConfig`](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/test/context/junit/jupiter/web/SpringJUnitWebConfig.html).

**Как завершить работу контекста в приложении?**

Если это не веб-приложение, то есть 2 способа:

- Регистрация shutdown-hook с помощью вызова метода`registerShutdownHook()`, он также реализован в классе AbstractApplicationContext. Это предпочтительный способ.
- Можно вызвать метод`close()`из класса AbstractApplicationContext.

В Spring Boot приложении:

- Spring Boot самостоятельно зарегистрирует shutdown-hook за вас.

**Что такое Java-конфигурация? Как она применяется?**

Чтобы создать класс с конфигурацией на основе Java-кода, нужно аннотировать его с помощью  
`@Configuration`.   
Этот класс будет содержать фабричные методы для создания бинов в контейнере.  
Эти методы должны быть аннотированы аннотацией`@Bean`.

Пример:

```
@Configuration
public class DSConfig {
  @Bean
  public DataSource dataSource() {
      return DataSourceBuilder
          .create()
          .username("")
          .password("")
          .url("")
          .driverClassName("")
          .build();
  }
}
```

Этот класс поместит в контейнер экземпляр класса DataSource. Позднее его можно будет использовать при доступе к базе данных.

**DI используя аннотации, сканирование классов**

Component scanning(сканирование компонентов) — Spring автоматически обнаруживает бины, которые будут находиться в контейнере. Это бины с аннотациями-стереотипами.

Однако сканирование компонентов не включено по умолчанию.  
Чтобы включить сканирование, аннотируйте @Configuration-класс аннотацией`@ComponentScanning`. Spring будет автоматически сканировать тот пакет, в котором находится этот класс и все его подпакеты.  
Можно указать и другие пакеты для сканирования, и даже классы:

```
//сканирует 2 пакета
@Configuration(<i>basePackages</i> = {"soundsystem", "video"})
```

```
//сканирует класс
@Configuration(<i>basePackageClasses</i> = "MyClass.class")
```

Autowiring(внедрение) — Spring автоматически внедрит зависимости во время сканирования или помещения бина в контейнер.  
Для внедрения зависимостей используется аннотация`@Autowire`.

**Что такое stereotypes(аннотации-стереотипы)?**

Стереотипы — это аннотации, обозначающие специальную функциональность.  
Все стереотипы включают в себя аннотацию`@Component`.

|   |   |
|---|---|
|[Component](https://habr.com/ru/users/component/)|Корневая аннотация, которая помечает класс как кандидат для автовнедрения|
|[Controller](https://habr.com/ru/users/controller/)|Указывает, что класс является контроллером для отправления данных на фронт.|
|@RestController|Указывает, что класс является контроллером для REST.   <br>Содержит аннотации [Controller](https://habr.com/ru/users/controller/) и @ResponseBody|
|[Service](https://habr.com/ru/users/service/)|Указывает, что класс является сервисом для выполнения бизнес-логики|
|[Repository](https://habr.com/ru/users/repository/)|Указывает, что класс является репозиторием для работы с бд|
|@Configuration|Указывает, что класс содержит Java-конфигурацию(@Bean-методы)|

**Какие существуют области видимости у бинов? Какая у них видимость по умолчанию?**

Область видимости — scope, скоуп. Существует 2 области видимости по умолчанию.

|   |   |
|---|---|
|Singleton|Область видимости по умолчанию. В контейнере находится всего 1 экземпляр бина|
|Prototype|В контейнере может находится любое количество экземпляров бина|

И 4 области видимости в веб-приложении.

|   |   |
|---|---|
|Request|Область видимости — 1 HTTP запрос. На каждый запрос создается новый бин|
|Session|Область видимости — 1 сессия. На каждую сессию создается новый бин|
|Application|Область видимости — жизненный цикл ServletContext|
|WebSocket|Область видимости — жизненный цикл WebSocket|

**Как создаются бины: сразу или лениво? Как изменить это поведение?**

Singleton-бины обычно создаются сразу при сканировании.  
Prototype-бины обычно создаются только после запроса.

Чтобы указать способ инициализации, можно использовать аннотацию`@Lazy`.   
Она ставится на @Bean-методы, на @Configuration-классы, или на @Component-классы.  
В зависимости от параметра(true или false), который принимает аннотация, инициализация будет или ленивая, или произойдет сразу. По умолчанию(т.е. без указания параметра) используется true.

**Что такое BeanFactoryPostProcessor и когда он используется?**

- `BeanFactoryPostProcessor`работает над описаниями бинов или конфигурационными метаданными перед тем, как бин будет создан.
- Spring поставляет несколько полезных реализаций`BeanFactoryPostProcessor`, например, читающий property-файлы и получающий из них свойства бинов.
- Вы можете написать собственную реализацию BFPP.

**Зачем вам может понадобится static @Bean-метод?**

Для того чтобы использовать кастомный BFPP. Вы можете переопределить механизм получения данных из метафайлов.

```
@Bean
public static PropertySourcesPlaceholderConfigurer pspc() {
    //создать, сконфигурировать и вернуть pspc
}
```

**Опишите свойства аннотации @Bean**

- `destroyMethod`— указывает на метод обратного вызова. Метод находится в бине.
- `initMethod`— указывает на метод обратного вызова. Метод находится в бине.
- `name`— имя бина. По умолчанию именем бина является имя метода.
- `value`— алиас для name()

**Что такое BeanPostProcessor и чем он отличается от BeanFactoryPostProcessor?**

Spring использует несколько BeanPostProcessor’ов.   
Например,[`CommonAnnotationPostProcessor`](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/context/annotation/CommonAnnotationBeanPostProcessor.html)или[`AutowiredAnnotationBeanPostProcessor`](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/beans/factory/annotation/AutowiredAnnotationBeanPostProcessor.html).  
BPP работает с экземплярами бинов, т.е. контейнер создает бин, а затем начинает работать BPP.

![Подготовка к Spring Professional Certification. Контейнер, IoC, бины - 3](https://www.pvsm.ru/images/2019/10/06/podgotovka-k-Spring-Professional-Certification-konteiner-IoC-biny-3.png "Подготовка к Spring Professional Certification. Контейнер, IoC, бины - 3")

**Что такое callback methods и как их использовать?**

Есть 3 варианта для создания таких методов:

- `@PreDestroy`и`@PostConstruct`[аннотации](https://www.baeldung.com/spring-postconstruct-predestroy)
- [Параметры](https://www.boraji.com/spring-bean-life-cycle-beans-initmethod-and-destroymethod-attributes-example)`initMethod`и`destroyMethod`в аннотации`@Bean`, указывающие на методы в классе бина
- Переопределенные`InitializingBean#afterPropertiesSet()`и`DisposableBean#destroy()`. Для переопределения этих методов нужно имплементировать соответствующие интерфейсы.

![Подготовка к Spring Professional Certification. Контейнер, IoC, бины - 4](https://www.pvsm.ru/images/2019/10/06/podgotovka-k-Spring-Professional-Certification-konteiner-IoC-biny-4.png "Подготовка к Spring Professional Certification. Контейнер, IoC, бины - 4")

**Как можно использовать аннотацию @Autowire и в чем отличие между способами?**

Ниже перечислены типы DI, которые могут быть использованы в вашем приложении:

- Constructor DI
- Setter DI
- Field DI

DI через конструктор считается самым лучшим способом, т.к. для него не надо использовать рефлексию, а также он не имеет недостатков DI через сеттер.  
DI через поле не рекомендуется использовать, т.к. для этого применяется рефлексия, снижающая производительность.  
DI через конструктор может приводить к [циклическим зависимостям](https://ru.wikipedia.org/wiki/Dependency_hell). Чтобы этого избежать, можно использовать ленивую инициализацию бинов или DI через сеттер.

**Опишите поведение аннотации @Autowired**

1. Контейнер определяет тип объекта для внедрения
2. Контейнер ищет бины в контексте(он же контейнер), которые соответствуют нужному типу
3. Если есть несколько кандидатов, и один из них помечен как`@Primary`, то внедряется он
4. Если используется аннотации`@Autowire`+`Qualifier`, то контейнер будет использовать информацию из`@Qualifier`, чтобы понять, какой компонент внедрять
5. В противном случае контейнер попытается внедрить компонент, основываясь на его имени или ID
6. Если ни один из способов не сработал, то будет выброшено исключение

Контейнер обрабатывает DI с помощью [AutowiredAnnotationBeanPostProcessor](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/beans/factory/annotation/AutowiredAnnotationBeanPostProcessor.html). В связи с этим, аннотация не может быть использована ни в одном BeanFactoryPP или BeanPP.

Если внедряемый объект массив, коллекция, или map с дженериком, то Spring внедрит все бины подходящие по типу в этот массив(или другую структуру данных). В случае с map ключом будет имя бина.

```
//параметр указывает, требуется ли DI
@Authowired(required = true/false)
```

**Как произвести DI в private поле?**

Вы можете использовать разные типы внедрения:

- Конструктор
- Сеттер
- Field-injection
- [Value](https://habr.com/ru/users/value/)

**Как использование @Qualifier дополняет @Autowired?**

Spring предоставляет аннотацию [Qualifier](https://habr.com/ru/users/qualifier/), чтобы преодолеть проблему неоднозначности при DI.

```
@Bean
@Qualifier("SomeClass1")
public SomeClass getField() {...}

//…

@Autowire
@Qualifier("SomeField1")
public SomeClass someField;
```

Если в контейнере есть несколько бинов одного типа(SomeClass), то контейнер внедрит именно тот бин, над @Bean-методом которого стоит соответствующий квалификатор. Также можно не ставить квалификатор на метод, а использовать имя бина в качестве параметра квалификатора.  
Имя бина можно можно указать через параметр аннотации [Bean](https://habr.com/ru/users/bean/), а по умолчанию это имя фабричного метода.

**Что такое прокси-объекты и какие типы прокси-объектов может создавать Spring?**

Прокси это специальный объект, который имеет такие же публичные методы как и бин, но у которого есть дополнительная функциональность.   
Два вида прокси:

- JDK-proxy — динамическое прокси. API встроены в JDK. Для него необходим интерфейс
- CGLib proxy — не встроен в JDK. Используется когда интерфейс объекта недоступен

Плюсы прокси-объектов:

- Позволяют добавлять доп. логику — управление транзакциями, безопасность, логирование
- Отделяет некоторый код(логирование и т.п.) от основной логики

**Как внедряется singleton-бин?**

Если в контейнере нет экземпляра бина, то вызывается @Bean-метод. Если экземпляр бина есть, то возвращается уже созданный бин.

**Что такое профили? Какие у них причины использования?**

При использовании Java-конфигурации вы можете использовать аннотацию[`@Profile`](https://www.baeldung.com/spring-profiles).  
Она позволяет использовать разные настройки для Spring в зависимости от указанного профиля.  
Ее можно ставить на @Configuration и [Component](https://habr.com/ru/users/component/) классы, а также на [Bean](https://habr.com/ru/users/bean/) методы.

```
@Bean("dataSource")
@Profile("production")
public DataSource jndiDataSource() {...}

@Bean("dataSource")
@Profile("development")
public DataSource standaloneDataSource() {...}
```

**Как внедрить простые значения в свойства в Spring?**

Для этого можно использовать аннотацию`@Value`.  
Такие значения можно получать из property файлов, из бинов, и т.п.

```
@Value("$some.key")
public String stringWithDefaultValue;
```

В эту переменную будет внедрена строка, например из property или из view.

  
[https://www.pvsm.ru/java/332301](https://www.pvsm.ru/java/332301)