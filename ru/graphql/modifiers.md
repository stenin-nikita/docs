# Модификаторы

Помимо непосредственно самих типов, GraphQL предоставляет 
два модификатора, которые описывают их характеристики.

## Non-Null

По-умолчанию все типы в GraphQL имеют значение `NULL`; 
Нулевое значение является допустимым ответом для всех вышеперечисленных типов. 
Чтобы объявить тип, который запрещает `NULL`, надо использовать модификатор Non-Null. 

Этот модификатор "обертывает" базовый тип, и действует идентично  
содержимому, за исключением того, что `NULL` не является допустимым. 
Заключительный восклицательный знак используется для обозначения поля, которое 
использует тип Non-Null, например: `name: ID!`.

## List

Список представляет собой специальный модификатор коллекции, который объявляет тип каждого 
элемента в списке (называемый типом элемента списка). 
Значения сериализуются как упорядоченные списки, где каждый элемент сериализуется 
в соответствии с типом этого элемента. Чтобы обозначить, что поле содержит список, 
тип элемента должен быть заключен в квадратные скобки следующим образом: `pets: [Pet]`.

## Примеры

То что мы прочитали ранее - довольно очевидно, но есть небольшие нюансы.
Как можно заметить - синтаксис модификаторов Non-Null и List можно 
компановать и изменения порядка модификатора Non-Null с `[Type]!` на 
`[Type!]` влечёт за собой изменения в поведении и соответсвенно в результате.

Давайте на примере скалярного типа `String` посмотрим как будет 
выглядеть результат в зависимости от декларации:  

- `String` - Строка, допускающая значение `NULL`.
- `String!` - Строка.
- `[String]` - Значение `NULL`, либо коллекция строк, допускающий значения `NULL`. 
- `[String!]` - Значение `NULL`, либо коллекция строк.
- `[String]!` - Список строк, допускающий значения `NULL`.
- `[String!]!`- Список строк.
