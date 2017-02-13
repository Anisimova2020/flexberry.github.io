---
title: Вариант 08 - «Управление проектами - Календарь»
keywords: Tasks
sidebar: guide-tasks_sidebar
toc: true
permalink: ru/gt_full-stack-task-case-08.html
folder: guides/tasks/
lang: ru
---

## Задание

В рамках выполнения практической части курса вами будет разработан сквозной пример: приложение «Управление проектами - Календарь» (модуль ИС для проектного управления).

Первая часть практического задания будет посвящена освоению базовых технологий, таких как C#, базы данных, клиентские технологии и т.п., вторая часть будет включать изучение возможностей платформы Flexberry для эффективного создания приложений.

## Общее описание предметной области

Требуется разработать модуль для системы управления проектами. Проект состоит из набора задач, каждая из которых имеет исполнителя и срок исполнения. Задача имеет определённую длительность, дату начала и дату окончания. Информационная система должна позволять вести учёт задач с контролем времени исполнения задач в соответствии с загруженностью и доступностью исполнителей. Иными словами, при попытке запланировать задачу так, что время её выполнения выпадает на выходной или праздничный день, пользователю должно выдаваться предупреждение, блокирующее данное действие. Информация о том, какие дни являются праздничными и выходными и является основной для данного модуля. Следует учитывать, что выходные дни могут быть как общегосударственными (праздники), так и корпоративными (по той или иной причине, указываемой руководством). Данный модуль должен позволять указывать нерабочие дни и они должны учитываться при планировании работ.

Технические требования:

*	Приложение реализуется в виде ASP.NET WebForms-приложения.
*	Данные хранятся в БД MSSQL Server.

## Практическое задание №1 - Серверная разработка (C#, .NET, ASP.NET)

Для реализации потребуется:

* Microsoft Visual Studio 2015
* Git for Windows

### Задание. Часть 1.

Требуется реализовать алгоритмы для работы с производственным календарем. На основе информации о стандартной рабочей неделе, днях-исключениях и промежутках рабочих часов в этой неделе/днях (может быть несколько) нужно вычислять следующую информацию:

* суммарная длительность рабочего времени на указанный интервал дат от ... и до ..., включая границы (в часах/минутах);
* дата и время окончания временного промежутка с заданными началом и заданной продолжительностью, учитывая выходные и нерабочее время (например, `57` рабочих часов отсчёт от `01.02.2017`).

Предпочтительно в первую очередь создать создать заглушки для классов, реализующих алгоритмы и модульные тесты, проверяющие работу вышеописанных функций (изначально не выполняющиеся); после этого реализовывать логику для исправления работы модульных тестов.

Реализацию следует сделать в виде .net-библиотеки и подготовить модульные тесты для неё (дополняющие написанные в начале, для более полного покрытия кода), продемонстрировать процент покрытия кода модульными тестами (чем больше, тем лучше). Источник данных о рабочих днях сделать подменяемым.

### Задание. Часть 2.

Реализовать простое ASP.NET WebForms-приложение (на данном этапе без БД), которое содержит компоненты (ascx-контролы), реализующиие:

1. Вычисление даты окончания временного промежутка на основе введенных пользователем даты начала и длительности промежутка (компонент должен использовать библиотеку из задания выше).
2. Отображение дней заданного месяца в виде таблицы, где цветом выделены выходные дни.

### Предоставление результатов выполнения работы на проверку

Реализованное решение (Visual Studio Solution) полностью разместить в репозитории на GitHub (решение должно компилироваться и запускаться). Ссылку на репозиторий предоставить преподавателям курса.

## Практическое задание №2 - Клиентская разработка (HTML, CSS, JS, jQuery)

Для реализации потребуется:

* Редактор кода для клиентской разработки: Visual Studio Code, Atom, Sublime Text и т.п.
* Git for Windows

### Задание

С использованием возможностей HTML, CSS, JS, jQuery сверстать форму, которая будет отображать таблицу с днями конкретного месяца (как в календаре). При клике на ячейку таблицы во всплывающем окне (или рядом) должна отображаться форма, на которой можно выбрать тип дня (стандартный/исключение), задать набор временных промежутков и настроить повторение, если выбран тип «исключение».

Вид календаря:  
![Вид календаря](/images/pages/guides/tasks/full-stack/case8-task2-sample1.png)

Примерный вид формы редактирования дня:  
![Примерный вид формы редактирования дня](/images/pages/guides/tasks/full-stack/case8-task2-sample2.png)

Отображаемые и редактируемые данные должны храниться в объекте javascript.


### Предоставление результатов

Реализованный проект разместить в репозитории на GitHub в виде встроенных страниц [GitHub Pages](https://pages.github.com/), позволяющих просматривать готовый результат. Ссылку на репозиторий и опубликованный таким образом проект предоставить преподавателям курса.

## Практическое задание №3 - Базы данных

Для реализации потребуется:

*	Microsoft SQL Server
*	Microsoft SQL Server Management Studio
*	Git for Windows

### Задание


### Предоставление результатов

Реализованные скрипты закоммитить в GitHub-репозиторий. Ссылку на репозиторий предоставить преподавателям курса.

## Практическое задание №4 - Проектирование ИС

Для реализации потребуется:

*	Flexberry Designer

### Задание

Нарисовать UML-диаграммы для обозначенной предметной области. Состав диаграмм определяется самим слушателем курсов, но должен обеспечивать полноценное описание предметной области.

### Предоставление результатов

Результатом работы является выгруженная в формате CRP стадия из Flexberry Designer. Стадию (файл с расширением *.CRP) следует закоммитить в репозиторий на GitHub, ссылку предоставить преподавателям курса.

## Практическое задание №5 - Объектный дизайн и генерация приложений

Для реализации потребуется:

*	Flexberry Designer
*	Microsoft Visual Studio 2015
*	Microsoft SQL Server
*	Git for Windows

### Задание

Выполнить объектный дизайн и генерацию ASP.NET-приложения для описанной предметной области. В качестве основы использовать реализованные ранее UML-модели. Генерация приложения и БД должна быть выполнена средствами Flexberry Designer приложение должно соответствовать требованиям и быть полностью работоспособным. Представления должны быть качественно настроены, подписи к классам и атрибутам на формах должны быть адекватными. Перечень форм и атрибутивный состав должны соответствовать предметной области и покрывать все требуемые бизнес-функции.

### Предоставление результатов

Сгенерированное приложение и скрипты создания БД следует выложить в репозиторий на GitHub. Предоставить преподавателям ссылку на репозиторий.

## Практическое задание №6 - Разработка бизнес-логики приложений

Для реализации потребуется:

* Flexberry Designer
* Microsoft Visual Studio 2015
* Microsoft SQL Server
* Git for Windows

### Задание

В сгенерированном при помощи Flexberry Designer приложении требуется реализовать следующую бизнес-логику.

1. 
2. 

### Предоставление результатов

Доработанная бизнес-логика должна быть включена в разрабатываемое приложение и закоммичена в соответствующий репозиторий. Ссылка на репозиторий предоставляется для проверки преподавателям курса.

## Практическое задание №7 - Разработка UI-логики приложения

Для реализации потребуется:

*	Microsoft Visual Studio 2015
*	Microsoft SQL Server
*	Редактор кода для клиентской разработки: Visual Studio Code, Atom, Sublime Text и т.п.
*	Git for Windows

### Задание


### Предоставление результатов

Доработанная UI-логика должна быть включена в разрабатываемое приложение и закоммичена в соответствующий репозиторий. Ссылка на репозиторий предоставляется для проверки преподавателям курса.

## Практическое задание №8 - Функциональные подсистемы Flexberry

Для реализации потребуется:

*	Flexberry Designer
*	Microsoft Visual Studio 2015
*	Microsoft SQL Server
*	Git for Windows

### Задание

Для реализованного приложения настроить подсистему полномочий. Пользователи должны заводиться администратором приложения. Авторизация на основе форм. Создать иерархию ролей, добавить операции на просмотр данных и выдать права только определённым пользователям. Настроить несколько ролей и назначить эти роли пользователям.
Настроить подсистему аудита. В разрабатываемом приложении все изменения объектов данных должно фиксироваться в подсистеме аудита. В навигационное меню следует добавить формы аудита, которые должны показываться только администраторам.

### Предоставление результатов

Доработанное приложение должно быть закоммичено в соответствующий репозиторий. Дополнительно в репозиторий должны быть добавлены SQL-скрипты, которые нужно выполнить для функционирования приложения с подсистемой полномочий и аудита. Ссылка на репозиторий предоставляется для проверки преподавателям курса.