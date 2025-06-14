**Java Scheduler** — это компонент, который позволяет выполнять задачи в Java в определённое время или с фиксированным интервалом. Он позволяет автоматизировать задачи, например, резервное копирование данных, обновление информации или периодический поиск данных. [golinuxcloud.com](https://www.golinuxcloud.com/java-scheduler/)[builtin.com](https://builtin.com/software-engineering-perspectives/java-scheduler)

### Типы планирования

В Java Scheduler выделяют два основных типа планирования:

1. **На основе времени**. Задачи выполняются с определёнными интервалами или в определённые моменты.
2. **На основе событий**. Планирование запускается при возникновении определённых событий.

 [golinuxcloud.com](https://www.golinuxcloud.com/java-scheduler/)

### Инструменты для реализации

Для реализации Java Scheduler используются, например:

- **Класс 
    
    Timer
    
    ** из пакета 
    
    java.util
    
    . Позволяет планировать задачи для однократного или повторного выполнения с фиксированным интервалом. [golinuxcloud.com](https://www.golinuxcloud.com/java-scheduler/)[redwood.com](https://www.redwood.com/article/job-scheduling-with-java/)
- **Интерфейс 
    
    ScheduledExecutorService
    
    ** из пакета 
    
    java.util.concurrent
    
    . Обеспечивает гибкий подход к планированию задач, поддерживает однопоточное и многопоточное выполнение. [golinuxcloud.com](https://www.golinuxcloud.com/java-scheduler/)[redwood.com](https://www.redwood.com/article/job-scheduling-with-java/)
- **Библиотека 
    
    Quartz Scheduler
    
    **. Поддерживает сложные сценарии планирования, включая выражения cron, и предоставляет такие функции, как сохранение задач, кластеризация и распределённое планирование. [redwood.com](https://www.redwood.com/article/job-scheduling-with-java/)[advsyscon.com](https://www.advsyscon.com/blog/job-scheduling-with-java/)
- **Аннотация 
    
    @Scheduled
    
    ** в Spring Framework. Позволяет планировать выполнение методов с фиксированным интервалом, задержкой или с помощью выражений cron. [medium.com](https://medium.com/@priyaroul99/lets-talk-about-schedulers-in-java-d6ba3004de7c)

### Примеры использования

Некоторые примеры использования Java Scheduler:

- **Планирование задачи, повторяющейся каждые 5 секунд**, с помощью класса 
    
    Timer
    
    . Для этого нужно создать экземпляр 
    
    Timer
    
    , вызвать метод 
    
    schedule(Task, delay, period)
    
     и определить задачу, которая расширяет 
    
    TimerTask
    
    . [golinuxcloud.com](https://www.golinuxcloud.com/java-scheduler/)[sky.pro](https://sky.pro/wiki/java/zapusk-funktsii-java-po-taymeru-primer-bez-javax-swing-timer/)[sky.pro](https://sky.pro/wiki/java/raspisanie-periodicheskikh-zadach-v-java-metod-schedule-at-fixed-rate/)
- **Планирование задачи с задержкой** с помощью 
    
    ScheduledExecutorService
    
    . Например, можно вызвать метод 
    
    schedule(Function, delay, TimeUnit.SECONDS)
    
     для запуска функции через заданное время. [sky.pro](https://sky.pro/wiki/java/zapusk-funktsii-java-po-taymeru-primer-bez-javax-swing-timer/)

### Где скачать Java Scheduler

Некоторые библиотеки и фреймворки для Java Scheduler доступны на следующих сайтах:

- **SourceForge**. На сайте представлены проекты с открытым исходным кодом, включая 
    
    j-scheduler
    
     — планировщик задач на Java.
- **Java-source.net**. На ресурсе можно найти информацию о библиотеках для планирования задач в Java, например, 
    
    Quartz
    
     и 
    
    J2EE Scheduler
    
    .