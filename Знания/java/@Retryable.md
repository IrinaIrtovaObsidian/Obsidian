
### Что такое «механизм повторных попыток»?

Это типовой [механизм](https://bootcamptoprod.com/spring-boot-retry/) обработки временных сбоев в распределенных системах. [](https://bootcamptoprod.com/spring-boot-retry/)А временный сбой  —  это временная ошибка, которая устраняется повторением операции. Механизмом повторных попыток неудачная операция повторяется, пока она не выполнится или не достигнуто максимальное число попыток.

Этот механизм применяется в следующих сценариях.

1. **Сбоя сети или связи:** взаимодействие приложения с внешними службами или базами данных по сети чревато сетевыми проблемами или недоступностью служб, при сетевых сбоях операция этим механизмом повторяется.
2. **Операции с базами данных:** при работе с БД случаются взаимоблокировки.
3. **Обработки пользовательских исключений:** специфических исключений, повторяемых при определенных условиях.
   
   ![[image.png]]
   
   #### **1) RetryableApplication**

```
@SpringBootApplication
@EnableRetry
public class RetryableApplication {    
	public static void main(String[] args) {        
		SpringApplication.run(RetryableApplication.class, args);    
	}
 }
```

`**@EnableRetry**`: этой аннотацией включается поддержка в Spring повторяемых методов, при выбрасывании исключения метод с помощью повторных попыток автоматически повторяется. Такое поведение активируется аннотацией `**@EnableRetry**`.

#### **2) TodoService**

В соответствии с полем **_content_** выбрасывается **SaveTodoException** или **IllegalArgumentException**, затем ожидается запуск методов восстановления:

```
@Service
@Slf4j
public class TodoService {

    @Retryable(
        retryFor = { SaveTodoException.class, IllegalArgumentException.class },
        maxAttempts = 3,
        backoff = @Backoff(delay = 800))
    public String saveTodo(Todo todo) throws SaveTodoException, IllegalArgumentException {

        if (todo.getContent().equals("SaveTodoException")) {
            log.error("Error when todo saving. [SaveTodoException]");
            throw new SaveTodoException("Todo did not save");
        } else if (todo.getContent().equals("IllegalArgumentException")) {
            log.error("Error when todo saving. [IllegalArgumentException]");
            throw new IllegalArgumentException("Todo did not save");
        }

        return "todo saved.";
    }

    @Recover
    public String recoverSaveTodo(SaveTodoException e, Todo todo){
        log.info(todo.getContent());
        return "recover save todo [SaveTodoException]";
    }

    @Recover
    public String recoverSaveTodo(IllegalArgumentException e, Todo todo){
        log.info(todo.getContent());
        return "recover save todo [IllegalArgumentException]";
    }
}
```

`**@Retryable**`: этой аннотацией метод обозначается как повторяемый, при выбрасывании определенных исключений он повторяется автоматически. Конфигурация этого поведения образуется такими параметрами аннотации:

- `retryFor`: этим атрибутом указывается массив типов исключений, для которых повторяется метод. В данном примере метод повторяется при выбрасывании `SaveTodoException` или `IllegalArgumentException`.
- `maxAttempts`: этим атрибутом задается максимум повторов, здесь метод повторяется до **трех раз.**
- `backoff`: этим атрибутом определяется стратегия задержки повторов. Здесь это фиксированная задержка в **800 миллисекунд** между повторами, значение по умолчанию  —  1000 мс.

`**@Recover**`: этой аннотацией обозначается метод восстановления для специфического исключения, который выполняется при невыполнении повторяемого метода. Так исключение обрабатывается и происходит восстановление после него.