# Template method (Шаблонный метод)

Шаблонный метод - паттерн, позволяющий создать шаблон по выполнению действий, включающий общие и уникальные для каждой сущности. Паттерн помогает не дублировать одинаковый код при создании похожих сущностей. 

- Шаблон - абстрактный класс, где абстрактными являются некоторые методы, которые должны реализовать дочерние классы. Другие методы реализованы внутри шаблона. Также в этом классе есть метод (некий _creator_), в котором вызываются все другие методы.
- Дочерние классы от шаблона - реализуют абстрактные методы. При создании их экземпляра доступен только метод creator-а, другие - недоступны.

В данном приложении шаблоном является `TemlateSoup` - принцип приготовления второго блюда. От него созданы классы `ChickenNoodlesSoup`, `OkroshkaSoup` и `TheSoup`.В них описаны шаги, уникальные для каждого блюда: подготовка ингридиентов (`prepareIngridients`), готовка мяса(`cookTheMeat`), добавление ингридиентов в кастрюлю(`addIngridientsToPot`) и томление (`languor`). 
Также в шаблоне есть и общий шаг - разлитие по тарелкам (`pourIntoPlase`). 
Из шаблона будет доступен лишь один метод - приготовление второго блюда - `cookSoup`, в котором все шаги выполняются в определенном порядке. 

В каждом из блюд, основанных на `TemplateSoup` реализованы все уникальные методы. Если же в блюде не предусмотрен данный шаг, то метод будет пустой (н-р, как в `OkroshkaSoup.languor()`).

Благодаря использованию шаблона получилось инкапсулировать последовательность шагов (`cookSoup`) и разлитие по тарелкам (`pourIntoPlase`) из каждого класса супа, т.к. они идтичны для всех них.