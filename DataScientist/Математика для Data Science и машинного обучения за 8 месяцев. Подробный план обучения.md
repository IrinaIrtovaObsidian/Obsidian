
Простой

7 мин

120K

[Data Mining*](https://habr.com/ru/hubs/data_mining/)[Big Data*](https://habr.com/ru/hubs/bigdata/)[Математика*](https://habr.com/ru/hubs/maths/)[Машинное обучение*](https://habr.com/ru/hubs/machine_learning/)[Учебный процесс в IT](https://habr.com/ru/hubs/study/)

Роадмэп

[Технотекст 2022](https://habr.com/ru/technotext/2022/)

[Из песочницы](https://habr.com/ru/sandbox/)

Беспилотные автомобили, продвинутые голосовые ассистенты, рекомендательные системы – это только малая часть тех классных продуктов, которые создаются с помощью инженеров по машинному обучению и, думаю, не для кого не секрет, что за кулисами сего чуда стоит математика. Именно она играет главную роль в понимании алгоритмов машинного и глубокого обучения.

> **🔔** **_Несколько полезных ссылок перед тем как продолжить:_**
> 
> - _другие планы обучения:_ [_Python_](https://habr.com/ru/articles/709102/)_,_ [_SQL_](https://habr.com/ru/articles/709116/)
>     
> - [_объяснение и реализация ML-алгоритмов с нуля на Python_](https://habr.com/ru/articles/804605/)
>     

### Машинное обучение держится на трёх основных столпах:

- линейная алгебра и аналитическая геометрия;
    
- математический анализ;
    
- теория вероятностей и статистика.
    

Теперь может возникнуть несколько вопросов: можно ли всё это изучить самостоятельно и если да, то сколько это займёт времени, и насколько это будет больно?

![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/982/1bd/f95/9821bdf951292eff471aea0c09ef2e6b.jpg)

Исходя из собственного опыта, могу сказать, что конечно же можно, однако будет немного больно, и чтобы понизить тот самый «градус боли» я решил написать эту статью в помощь таким же новичкам, как и я. Ну что....поехали!

> _Вся литература, приведённая ниже, содержит упражнения для самостоятельной работы._

### Школьная математика (1 неделя и больше)

Какие темы стоит изучить:

- числа и действия с ними;
    
- уравнения и неравенства;
    
- функции и графики;
    
- тригонометрия;
    
- логарифмы;
    
- геометрия.
    

Если нет проблем со школьным курсом, то предлагаю обратить внимание на [Кратчайший курс школьной математики](https://mathter.pro/pesochnica/index.html) – всё описано кратко и очень понятным языком.

Если есть пробелы и хочется углубиться, то есть хорошие плейлисты на канале [Видеокурсы DA VINCI](https://www.youtube.com/@da_vinci_center/playlists) – здесь найдёте не только объяснение школьной математики, но и линейной алгебры с математическим анализом.

В качестве задачника можно использовать «Сборник задач по математике для поступающих во втузы», Сканави М.И.

![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/39c/7ff/074/39c7ff07421ebaf6475e3b0e36b26929.jpg)

### Линейная алгебра и аналитическая геометрия (1,5 месяца)

Какие темы стоит изучить:

- вектора и операции над ними;
    
- системы координат;
    
- матрицы, ранг и определители;
    
- системы линейных уравнений;
    
- пространства (линейное, евклидово, аффинное) и их преобразования;
    
- линейные и самосопряжённые операторы;
    
- собственные векторы и значения;
    
- квадратичные формы;
    
- кривые и поверхности второго порядка;
    
- матричные факторизации (LU, QR, SVD);
    
- понятие тензоров (по желанию).
    

Начнём с плейлистов [Linear algebra](https://www.youtube.com/playlist?list=PLBh2i93oe2quLc5zaxD0WHzQTGrXMwAI6) и [Linear algebra (English)](https://www.youtube.com/playlist?list=PLBh2i93oe2qtXb7O-kPaEhAtFEb3n9Huu) канала The bright sight of mathematics – лучшего объяснения линейной алгебры и численных методов к ней я не видел.

Литература для дополнительного изучения:

- «Introduction to Linear and Matrix Algebra», Nathaniel Johnston
    
    ![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/081/3b9/193/0813b91937661b081af1a7a696c0456f.jpg)
    
- «Advanced Linear and Matrix Algebra», Nathaniel Johnston
    
    ![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/f4d/8c4/f39/f4d8c4f39ab28620284e93b252860964.jpg)
    

Хорошая серия книг, где читателя постепенно знакомят со всеми необходимыми разделами линейной алгебры, включая матричные факторизации и тензоры.

Неплохие книги на русском:

- «Линейная алгебра и аналитическая геометрия», Киркинский А.С.
    
    ![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/8d8/ac9/04d/8d8ac904dd9d71b6a03029e5b661adbe.jpg)
    

- «Вычислительная линейная алгебра», Вержбицкий В.М.
    
    ![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/ea7/248/b66/ea7248b66d77768399201c171cb4c624.jpg)
    

Первая книга – классический университетский курс линейной алгебры и аналитической геометрии, вторая – учебник по матричным факторизациям.

### Математический анализ (3 месяца)

Какие темы стоит изучить:

- множества и комплексные числа;
    
- пределы и производные;
    
- функции одной и нескольких переменных;
    
- интегралы (неопределённые и определённые);
    
- дифференциальные уравнения;
    
- ряды (числовые, функциональные, степенные, Тейлора, Маклорена, Фурье);
    
- преобразование Фурье.
    

Далее переходим к [плейлистам](https://www.youtube.com/@NEliseeva/playlists) канала N Eliseeva – объёмный, но очень хороший курс с кучей примеров и понятным объяснением.

Литература для дополнительного изучения:

- «Calculus for Scientists and Engineers», Martin Brokate, Pammy Manchanda, Abul Hasan Siddiqi
    
    ![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/0c4/4c5/b80/0c44c5b80765a7dd276d4c7dd26cc098.jpg)
    
- «Математический анализ», Киркинский А.С.
    
    ![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/59b/abd/009/59babd0098d4b29cba01a583527b89d0.jpg)
    

Хорошие книги плюс-минус об одном и том же, содержат все необходимые темы, включая преобразование Фурье.

> _В качестве задачника я использовал учебное пособие БГТУ «Высшая математика в 2-х частях» (Марченко В.М.) – простой вузовский учебник, однако его плюс заключается в том, что после каждой главы имеются упражнения сразу же с ответами, что очень удобно._

### Теория вероятностей и математическая статистика (3 месяца)

Какие темы стоит изучить по теории вероятностей:

- комбинаторика;
    
- события и их вероятности;
    
- теоремы сложения и умножения вероятностей;
    
- формулы Байеса, Пуассона и Бернулли;
    
- локальная и интегральная теоремы Лапласа;
    
- дискретные случайные величины;
    
- дискретные распределения (геометрическое, биномиальное, Пуассона);
    
- непрерывные случайные величины;
    
- непрерывные распределения (равномерное, показательное, нормальное).
    

Какие темы стоит изучить по статистике:

- генеральная совокупность и выборка;
    
- вариационные ряды (дискретные и интервальные);
    
- основные показатели статистики (мода, медиана, среднее и т.д.);
    
- графическое представление данных;
    
- оценки параметров генеральной совокупности;
    
- статистические гипотезы и методы их оценки;
    
- виды группировок данных;
    
- бутстрэп;
    
- дисперсионный (ANOVA) и ковариационный (ANCOVA) анализы;
    
- корреляция и регрессия (линейная, логистическая).
    

Приступим к [теории вероятностей](http://www.mathprofi.ru/teorija_verojatnostei.html) на mathprofi и учебнику БГТУ «Теория вероятностей» (Блинова Е.И., Марченко В.М., Можей Н.П.), в котором содержится необходимый набор упражнений с кратким теоретическим описанием.

Далее, переходя к статистике, стоит обратить внимание на раздел [математическая статистика](http://www.mathprofi.ru/matematicheskaya_statistika.html) также на mathprofi и плейлист [Statistics Fundamentals](https://www.youtube.com/playlist?list=PLblh5JKOoLUK0FLuzwntyYI10UQFUhsY9) на канале StatQuest with Josh Starmer.

Литература для дополнительного изучения:

- «Modern Mathematical Statistics with Applications», Jay L. Devore, Kenneth N. Berk, Matthew A. Carlton
    
    ![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/ba3/870/754/ba3870754394b5ebac025a3daa10514e.jpg)
    
    Объемная книга, содержащая в себе и теорию вероятностей, и статистику с огромным количеством продвинутых тем.
    
- «Теория вероятностей и математическая статистика», Гмурман В.Е.
    
    ![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/d70/67e/3b3/d7067e3b3fdcf67c591966814140c6a4.jpg)
    
    Ещё один неплохой учебник, но с меньшим количеством тем.
    

### Дыхание машинного обучения (по желанию)

Переходя в дальнейшем к машинному обучению, было бы неплохо иметь представление о том, как в нём применяется только что изученная математика, и здесь я предлагаю ознакомиться с книгой «Data-Driven Science and Engineering», Steven L. Brunton, J. Nathan Kutz.

![](https://habrastorage.org/r/w1560/getpro/habr/upload_files/bc2/179/406/bc2179406546be6b77f1dcc225786d97.jpg)

Отсюда вы узнаете о сжатии изображений с помощью сингулярного разложения матриц, как преобразование Фурье помогает избавляться от шума в аудиофайлах и изображениях, как найти коэффициенты регрессий через градиентный спуск и многое другое.

### Что в итоге

Занимаясь по 10 часов практически каждый день, на изучение всего вышеперечисленного уйдёт порядка 8 месяцев – такой результат был получен, исходя из собственного опыта и возможностей. Возможно, у вас будут другие цифры, главное – пробовать и всё получится.

Надеюсь, данный план оказался для вас полезным, в будущем планирую написать планы обучения и по другим темам в машинном обучении.

Всем успехов!

### Дополнительные источники

_Школьная математика:_

- «Краткий курс школьной математики» Битнер В.А.;
    
- «Справочник школьника по математике», Маслова Т.Н., Суходский А.М.;
    
- [ЕГЭ по базовой математике](https://stepik.org/course/19059/promo) – курс от школы BEEGEEK;
    
- [Подготовка к ЕГЭ по математике (интенсивный курс)](https://stepik.org/course/735/promo?search=1824335789) – курс от Pelican Education.
    

_Линейная алгебра и аналитическая геометрия:_

- «Linear Algebra Done Right», Sheldon Axler;
    
- «Introduction to Linear Algebra», Gilbert Strang;
    
- «Matrix Algebra» (second edition), James E. Gentle;
    
- «Linear Algebra and Matrix Analysis for Statistics», Sudipto Banerjee, Anindya Roy;
    
- «Линейная алгебра», Попов В.С.;
    
- «Линейная алгебра» (в трёх частях), Кострикин А.И.;
    
- «Матричный анализ и линейная алгебра», Тартышников Е.Е.;
    
- «Линейная алгебра», «Аналитическая геометрия», Ильин В.А., Позняк Э.Г.;
    
- «Линейная алгебра», «Аналитическая геометрия», Канатников А.Н., Крищенко А.П.;
    
- [Линейная алгебра](https://stepik.org/course/2461/promo) – курс от Computer Science Center;
    
- [Linear Algebra: Problems and Methods](https://stepik.org/course/79/info) – ещё один неплохой курс;
    
- [Linear Algebra Basics](https://www.coursera.org/learn/linear-algebra-basics) – курс от Индийского института технологий Рурки;
    
- [Linear Algebra for Data Science Using Python](https://www.coursera.org/specializations/linear-algebra-data-science-python) – специализация от Говардского университета;
    
- [Math for AI beginner: part 1. Linear Algebra](https://www.coursera.org/learn/math-for-ai-beginner-part-1-linear-algebra) – курс от Корейского передового института науки и технологий.
    

_Дискретная математика:_

- «Дискретная математика», Новиков Ф.Н.;
    
- «Discrete Mathematics with Applications» (fifth edition), Susanna S. Epp;
    
- Логика: [курс от БФУ им. И. Канта](https://stepik.org/course/4598/promo?search=1825967811), [курс от ТУСУР](https://stepik.org/course/48679/promo?search=1825967815);
    
- [Дискретные структуры](https://stepik.org/course/83/promo) – курс от Александра Дайняка;
    
- [Введение в дискретную математику](https://stepik.org/course/902/promo?search=1825840557) – курс от института биоинформатики;
    
- [Introduction to Discrete Mathematics for Computer Science](https://www.coursera.org/specializations/discrete-mathematics) – курс от University of California San Diego;
    
- [Основы теории графов](https://stepik.org/course/126/promo?search=1825840562), [Основы перечислительной комбинаторики](https://stepik.org/course/125/promo), [Основы дискретной математики](https://stepik.org/course/1127/promo?search=1825840554), [Ликбез по дискретной математике](https://stepik.org/course/91/promo?search=1825840553) – курсы от Computer Science Center.
    

_Математический анализ:_

- «Calculus», James Stewart;
    
- «Calculus», Michael Spivak;
    
- «Calculus Made Easy», Silvanus P. Thompson, Martin Gardner;
    
- «Математический анализ» (в двух частях), Зорич В.А.;
    
- «Курс математического анализа» (в трёх томах), Кудрявцев Л.Д.;
    
- «Основы математического анализа» (в двух томах), Фихтенгольц Г.М.;
    
- [Математический анализ](https://www.youtube.com/playlist?list=PLCx14LDfH033RANLVFVAdFIxFHhy1VXHr) – видеокурсы DA VINCI;
    
- [Математический анализ для инженеров](https://stepik.org/course/108897/promo) – курс от НГТУ;
    
- [Introduction to Calculus](https://www.coursera.org/learn/introduction-to-calculus) – курс от Сиднейского университета;
    
- [Введение в математический анализ](https://stepik.org/course/95/promo) – курс от Computer Science Center.
    

_Теория вероятностей и статистика:_

- «Statistics», Robert S. Witte, John S. Witte;
    
- «A First Course in Probability», Sheldon Ross;
    
- «Elementary Probability Theory», Kai Lai Chung, Farid AitSahlia;
    
- «All of Statistics: A Concise Course in Statistical Inference», Larry Wasserman;
    
- «Статистика для всех», Сара Бослаф;
    
- «Вероятность» (в двух томах), Ширяев А.Н.;
    
- «Наглядная математическая статистика», Лагутин М.Б.;
    
- «Теория вероятностей и математическая статистика», Кремер Н.Ш.;
    
- «Практическая статистика для специалистов Data Science» (второе издание), Питер Брюс, Эндрю Брюс, Питер Гедек;
    
- [Статистика](https://stepik.org/course/74096/promo) – курс от БФУ им. И. Канта;
    
- Теория вероятностей: [часть 1](https://stepik.org/course/2911/promo?search=1811821373), [часть 2](https://stepik.org/course/3209/promo?search=1811821374) – курсы от ТГУ;
    
- [Introduction to statistics](https://www.coursera.org/learn/stanford-statistics) – курс по статистике от Стэнфорда;
    
- [Introductory Econometrics a Practical Approach](https://stepik.org/course/128816/info) – курс от РУДН;
    
- Основы статистики: [часть 1](https://stepik.org/course/76/info), [часть 2](https://stepik.org/course/524/info), [часть 3](https://stepik.org/course/2152/info) – курсы от института биоинформатики;
    
- [Теория вероятностей](https://stepik.org/course/3089/promo), [Математическая статистика](https://stepik.org/course/326/info) – курсы от Computer Science Center.
    

_Вся математика в одном месте:_

- «Essential Math for Data Science», Thomas Nield;
    
- «Modern Engineering Mathematics», Glyn James, Phil Dyke;
    
- «Mathematics for Machine Learning», Marc Peter Deisenroth, A. Aldo Faisal, Cheng Soon Ong;
    
- «Конспект лекций по высшей математике», Письменный Д.Т.;
    
- «Высшая математика для экономического бакалавриата» (четвёртое издание), Кремер Н.Ш.;
    
- «Вся высшая математика» (в семи томах), Краснов М.Л., Киселёв А.И., Макаренко Г.И. и другие;
    
- «Высшая математика для гуманитарных направлений», Седых И.Ю., Гребенщиков Ю.Б., Шевелев А.Ю.;
    
- [Math](https://www.khanacademy.org/math) – все темы по математике от Khan Academy;
    
- [Mathematics](https://www.youtube.com/playlist?list=PLWKjhJtqVAbl5SlE6aBHzUVZ1e6q1Wz0v) – вся математика в одном плейлисте от freeCodeCamp;
    
- [Mathematics for Machine Learning](https://www.coursera.org/specializations/mathematics-machine-learning) – специализация от Imperial College London;
    
- [Mathematics for Machine Learning and Data Science](https://www.coursera.org/specializations/mathematics-for-machine-learning-and-data-science) – специализация от DeepLearning.AI;
    
- [Expressway to Data Science: Essential Math](https://www.coursera.org/specializations/expressway-to-data-science-essential-math) – специализация от University of Colorado Boulder;
    
- [Mathematics for Engineers](https://www.coursera.org/specializations/mathematics-engineers) – специализация от The Hong Kong University of Science and Technology.
    

_Ещё несколько полезных ссылок:_

- [3Blue1Brown](https://www.youtube.com/@3blue1brown) – все разделы математики;
    
- [Stabelm](https://www.youtube.com/@stabelm/featured) – хорошее объяснение сложных тем;
    
- [The Math Sorcerer](https://www.youtube.com/@TheMathSorcerer) – обзор книг по математике;
    
- [Маткульт-привет!](https://www.youtube.com/@user-rb8ux1no6j) – канал Алексея Савватеева;
    
- [Точки Лагранжа](https://www.youtube.com/@user-so6eo6pg9v/featured) – видеокурсы по высшей математике;
    
- [Борис Трушин](https://www.youtube.com/@trushinbv) – ещё один полезный канал по математике;
    
- [Математик МГУ](https://www.youtube.com/@hitman_math) – интересный канал со множеством полезных видео;
    
- [MIT OpenCourseWare](https://www.youtube.com/@mitocw/featured) – море лекций от небезызвестного университета;
    
- [Oxford Mathematics](https://www.youtube.com/@OxfordMathematics) – лекции от ещё одного очень известного университета;
    
- [dUdVstud](https://www.youtube.com/@dudvstud9081) – много нужной инфы касаемо математики и Data Science в целом;
    
- [Sergej Kuts](https://www.youtube.com/@SergejKuts) (присутствует мат). Автор по-пацански объясняет математику – весело и полезно.