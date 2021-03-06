---
title: Функциональность при работе с массивами детейловых объектов
sidebar: flexberry-orm_sidebar
keywords: DataObject, Flexberry ORM, детейл
summary: Особенности работы с массивом детейлов
toc: true
permalink: ru/fo_functionality-work-detail-array.html
lang: ru
---

## Базовая функциональность по работе с массивами детейловых объектов

`DetailArray` поддерживает базовую функциональность по работе с массивами [детейловых](fo_detail-associations-properties.html) объектов:

* Поддержка ссылки на [шапку (агрегатор)](fd_key-concepts.html).
* Поддержка коллекции: 
    * добавление (AddObject, AddRange), 
    * вставка (Insert), 
    * удаление (Remove, RemoveByIndex, RemoveByKey),
    * очистка (Clear), 
    * установка/взятие значения (GetByKey, SetByKey),
    * перемещение (Move),
    * количество объектов (Count),
    * перебор объектов в конструкции foreach.
* Поддержка упорядочения (порядка, в котором лежат [объекты данных](fo_data-object.html)).

### Агрегирующие функции

Чтобы среди объектов, находящихся в массиве [детейлов](fo_detail-associations-properties.html), посчитать какую-либо агрегирующую функцию (сумма, макс., мин., среднее значение, что-либо произвольное), необходимо в классе, унаследованном от `DetailArray`, определить функцию без параметров, которая возвращает некоторое значение. Далее, к этой функции необходимо приписать атрибут `AggregationFunction`. Параметрами являются: имя свойства, для которого эта агрегирующая функция, и строка формата (`String.Format`), в соответствии с которой значение будет выводиться пользователю. 

{% include important.html content="Агрегирующие функции должны обрабатываются визуальными компонентами редактирования массива детейлов. Атрибут `AggregationFunction` принято обрабатывать следующим образом: если указано имя свойства, то значение агрегирующей функции указывается непосредственно рядом со значениями объектов данных (например, внизу таблицы в соответствующем столбце) и тип возвращаемого функцией значения должен быть тем же или неявно приводимым к типу свойства. Если указана строка формата, тогда значение выводится отдельно, в этом формате.
" %}

### Упорядочивание

Объекты в массиве детейлов могут быть упорядочены (именно упорядочены, а не отсортированы), т.е. располагаться в каком-либо, строго определённом порядке.

Для того, чтобы ввести упорядочение, необходимо в [детейловый класс](fo_detail-associations-properties.html) данных ввести целочисленное (`System.Int32`) свойство с приписанным атрибутом `Order`. 

{% include important.html content="Упорядочение обрабатывается визуальными компонентами редактирования массива детейлов." %}

{% include note.html content="Без наличия Order-атрибутов детейлы могут возращаться в любом порядке, в отличном от того, в котором они были сохранены." %}

### Получение типа DetailArray по его наименованию

Чтобы получить тип детейла, имея тип агрегатора и наименование DetailArray, необходимо воспользоваться методом [Information](fo_methods-class-information.html).GetItemType.

Сигнатура метода:

```csharp
public static System.Type ICSSoft.STORMNET.Information.GetItemType (
        System.Type AgregatorType,
        string DetailPropertyName ) 	
```

где `AgregatorType` это тип класса-агрегатора, а `DetailPropertyName` это наименование списка детейлов, тип которых необходимо получить.

Метод возвращает объект типа `System.Type`, содержащий описание типа-детейла.

### Написание LINQ-запросов к уже полученному списку DetailArrayOf...

Чтобы написать LINQ-запрос к детейлам, необходимо сначала привести их к необходимому типу (т.к. DetailArrayOf... не поддерживает интерфейс `IEnumerable`, то непосредственно к нему LINQ-методы (такие как `Select`, `ToList` и пр.) не применятся).

Пусть есть класс `Aggregator`, имеющий детейловый класс `Det`, тогда конструкция ниже выдаст `ошибку`, т.к. ему необходимо указать тип, объектами которого будет заполнен новый список:

```csharp
Aggregator aggr = new Aggregator();
aggr.DetailArrayOfDet.ToList(); 
```

Если указать тип, то `ошибка` изменится на: `Невозможно привести тип DetailArrayOfDet к типу IEnumerable&lt<Det>`:

```csharp
Aggregator aggr = new Aggregator();
aggr.DetailArrayOfDet.ToList<Det>(); 
```

`Правильным способом` является следующий:

```csharp
Aggregator aggr = new Aggregator();
aggr.DetailArrayOfDet.Cast<Det>.ToList(); 
```
