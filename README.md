# Spring_WebProgramming
Spring



# Испитна задача

Потребно е да развиете апликација за менаџирање на продукти која ќе овозможи прегледување, додавање, уредување и бришење 
на продукти. 

## Функционални барања

- **(20 поени)** Потребно е на патеките `/` и `/products` да прикажете листа од сите креирани продукти со користење на 
темплејтот `list.html`. 
  - Имплементацијата на оваа функционалност може да ја проверите со тестот `test1_list`.  
- **(20 поени)** Потребно е да се  имплементира додавање на продукти. При клик на копчето **Add new product** од темплејтот
`list.html`, потребно е да се прикаже темплејтот `form.html` на патеката `/products/add`, каде при клик на **Submit** ќе
се креира и запише нов продукт во базата на податоци. Потоа треба да се прикаже страната `/products`.
  - Имплементацијата на оваа функционалност може да ја проверите со тестот `test3_create`.    
- **(10 поени)** Потребно е да се  имплементира бришење на продукти. При клик на копчето **Delete** од темплејтот
`list.html`, потребно е да се избрише продуктот од базата на податоци. Потоа треба да се прикаже страната `/products`.
  - Имплементацијата на оваа функционалност може да ја проверите со тестот `test5_delete`.
- **(20 поени)** Потребно е да се  имплементира променување на продукти. При клик на копчето **Edit** од темплејтот
`list.html`, потребно е да се прикаже темплејтот `form.html` на патеката `/products/[id]/edit`, при што во `<input>` 
елементите ќе се прикажат вредностите за продуктот кој се променува. При клик на **Submit** треба да се запише промената 
на продуктот во базата на податоци. Потоа треба да се прикаже страната `/products`.
  - Имплементацијата на оваа функционалност може да ја проверите со тестот `test4_edit`.  
- **(20 поени)** Потребно е да конфигурирате најава на `/login` и одјава на `/logout`. Притоа, јавна треба да биде само 
страницата `/`, додека сите останати страници треба да се видливи само за `ROLE_ADMIN`. Дополнително, кај`list.html` 
копчињата **Edit**, **Delete** и **Add new product** треба да се видливи само за `ROLE_ADMIN`.
  - Имплементацијата на оваа функционалност може да ја проверите со тестовите `test6_security_urls` и `test7_security_buttons`. 
- **(20 поени)** Потребно е да овозможите пребарување на продукти според име и категорија преку формата со `id="filter-form"` 
во темплејтот `list.html`. Резултатите од пребарувањето треба да се прикажат на истата страница, при што ќе се прикажат 
само продуктите кои го содржат текстот внесен во полето за име и припаѓаат во селектиранта категорија. Филтрирањето се 
извршува само според внесените полиња (ако се празни, се игнорира филтрирањето по тој критериум).  
  - Имплементацијата на оваа функционалност може да ја проверите со тестот `test2_filter`. 

**ВАЖНО:** Сите споменати тестови се наоѓаат во класата `mk.ukim.finki.wp.exam.example.SeleniumScenarioTest`.


## Поставување на решението
Тестовите мора задолжително да ги извршите, затоа што на тој начин го испраќате вашето решение за прегледување. За проверка
дали успешно е поставено вашето решение пристепете на патеката [env4health.finki.ukim.mk/submit/[index]](http://env4health.finki.ukim.mk/submit/index), 
каде наместо `[index]` ќе го наведете вашиот индекс, кој претходно ќе го поставите во `TODO` вредноста на текстот. 

Тие ќе ви помогнат да ја проверите точноста на вашата имплементација, но и ќе испратат информации до нашиот сервер за тоа 
до каде функционира вашата апликација. Ќе се гледа кодот само на студентите кај кои барем една проверка (`ExamAssert`) 
ќе помине успешно. 

**НЕ Е ДОЗВОЛЕНО МЕНУВАЊЕ НА ТЕСТОВИТЕ, освен внесување на вашиот индекс**

## Техничко упатство: 
- Во пакетот `mk.ukim.finki.wp.exam.example.model` веќе се креирани класите кои го репрезентираат моделот. 
Потребно е да извршите нивно мапирање со соодветните JPA анотации за моделот успешно да се сними во базата на податоци. 
Притоа важат следните услови: 
  - Продуктите може да припаѓаат во повеќе категории, а во секоја категорија може да има повеќе продукти.
  - Еден корисник може да биде `creator` на повеќе продукти. 
  - Идентификаторите за `Product` и `Category` треба да бидат генерирани. 
- Во пакетот `mk.ukim.finki.wp.exam.example.service` се веќе дефинирани интерфејсите за сервисната логика. 
За секој од методите имате опис што треба да биде имплементирано. Потребно е да се имплементираат овие интерфејси во 
соодветните класи во пакетот `mk.ukim.finki.wp.exam.example.service.impl`. Во коментарите на методите се објаснети 
дополнителни услови (доколку ги има) кои треба да ги исполни методот. 
- Класите од пакетот `mk.ukim.finki.wp.exam.example.repository` треба да ги дополните со потребните методи 
кои ви се потребни за да ја овозможите функционалноста на имплементацијата на сервисниот слој. Тие треба да се изведат 
од класата `JpaRepository` од Spring Data. 
- Потребно е да ја анотирате класата `mk.ukim.finki.wp.exam.example.config.DataInitializer` и нејзините 
соодветни методи, така што при стартување на апликацијата ќе се изврши методот `initData`.
- Во класата `mk.ukim.finki.wp.exam.example.web.ProductsController` се дефинирани сите методи кои се 
потребни за да се имплементира менаџирањето со продуктите. Потребно е овие handler методи да ги мапирате со користење 
само на HTTP GET и POST барања. Во продолжение е подетален опис за секој од методите:  
     - `showProducts` треба да го искористи `list.html` темплејтот за приказ на сите продукти. Овој handler метод треба да 
     се мапира на патеките `/` и `/products`. 
       - Аргументите на овој метод не се задолжителни и може да бидат `null`. 
       - Во случај кога не се испратени аргументите (кога се `null`) треба да се прикажат сите продукти од базата. 
       - Ако некој, или двата, од аргументите е различен од `null`, тогаш треба да се прикажат продуктите кои ги враќа 
       `ProductService.listProductsByNameAndCategory`.  
     - `showAdd` треба да го прикаже темплејтот `form.html`. Овој handler метод треба да се мапира на патеката `/products/add`. 
     - `showEdit` треба да го прикаже темплејтот `form.html`, меѓутоа во секој од `input` елементите треба да биде пополнета 
     соодветната вредност за продуктот кој се уредува. Овој handler метод треба да се мапира на патеката `/products/[id]/edit`
     - `create` треба да го креира продуктот според аргументите на методот (патека `/products`). Потоа треба да се прикажат сите продукти.
     - `update` треба да се уреди продуктот според аргументите на методот (патека `/products/[id]`). Потоа треба да се прикажат сите продукти.
     - `delete` треба да се избрише продуктот со дадениот идентификатор (патека `/products/[id]/delete`). Потоа треба да се прикажат сите продукти. 
 - Дополнете ги темплејтите со соодветните **Thymeleaf** атрибути за да се постигнат бараните функционалности. 
Притоа, ако недостасуваат одредени елементи и атрибути, може да ги додадете, но **НЕ СМЕЕ** да ги менувата `id` и 
`class` својствата на тековните елементи. Во коментари се дадени описи за елементите кои треба да се повторуваат, како 
и кои методи од контролерот треба да се повикаат.   
 - Потребно е да конфигурирате најава на `/login` и одјава на `/logout` со Spring Security во класата 
`mk.ukim.finki.wp.exam.example.config.SecurityConfig`. Притоа, јавна треба да биде само страницата `/`, додека сите 
останати страници треба да се видливи само за `ROLE_ADMIN`. Дополнително, кај`list.html` копчињата **Edit**, **Delete** 
и **Add** треба да се видливи само за `ROLE_ADMIN`.
    - Доколку го имплементирате ова барање, потребно е да ја закоментирате означената линија во кодот со `TODO:` делот.
    - За најава, потребно е да се споредува со корисниците од базата на податоци, репрезентирани со класата `User`. 
 
