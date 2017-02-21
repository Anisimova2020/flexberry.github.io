---
title: Проектирование информационных систем
sidebar: flexberry-designer_sidebar
keywords: 
toc: true
permalink: ru/fd_design.html
folder: products/flexberry-designer/about/
lang: ru
---

## Проектирование информационной системы


[`Проектирование`](fd_definition-of-design.html) (от латинского `projectus`, что означает "брошенный вперед") - это процесс составления описания, необходимого для создания в заданных условиях еще `не существующего` объекта по первичному описанию этого объекта путем его детализации, дополнения, расчетов и оптимизации.

В технологии CASEBERRY используется разработка приложения, управляемая моделями (англ. model-driven development). Это означает, что разработка и доработка приложения сводится к разработке и доработке `модели приложения`. В нашем случае в качестве модели приложения выступают [UML-диаграммы классов](fd_class-diagram.html), созданные с помощью Flexberry Designer.

При помощи CASEBERRY существует возможность создания работающих приложений при помощи проектирования и `без` использования программирования. Можно создавать как Windows-приложения, так и Web-приложения.

## Необходимый минимум инструментов

Для проектирования приложения с использованием CASEBERRY необходимо:

* Наличие на рабочем месте установленного и лицензированнго продукта [`Flexberry Designer`](flexberry.ru)
    * `AspNetPlugin` - PlugIn для генерации Web-приложений ([установка ASP.NET Generator](fa_asp-net-plugin.html)).
* `MS SQL Server` - система управления базами данных, в которых будет хранить данные проектируемое приложение. СУБД должна быть развернута на рабочем месте.

{% include note.html content="Во избежание возникновения множества ошибок, связанных с правами доступа к базе, следует убедиться, что доступна возможность создавать и изменять базы данных." %}

* Средства `[развертывания](gbt_deployment.html|)` Web-сайтов (если проектируется Web-приложение).

## Этапы проектирования с использованием CASEBERRY

Проектирование приложения можно условно разделить на 4 блока:
* `Моделирование приложения` - создание [Class-diagram|диаграммы классов) в нотации UML при помощи CASEBERRY Tool, настройка [View-definition|представлений) объектов, настройка форм приложения
* `Настройка генерации приложения` - связывание приложения с базой данных, на которой оно будет работать, а также настройка процесса генерации кода.
* `Генерация и развертывание приложения` - создание базы данных и приведение её к модели приложения, а также генерация приложения.
* `Настройка созданного прототипа приложения` - настройка пользовательских ограничений

__Результатом__ является прототип приложения.

### Моделирование приложения


Создание модели приложения при помощи CASEBERRY Tool путем описания [Class-diagram|диаграммы классов) в нотации UML. На основании [Class-diagram|диаграммы классов) впоследствии будут генерироваться классы приложения. Создание и настройка [View-definition|представлений). Настройка форм приложения.

* Проверка диаграммы классов.
#* Проверка связей классов ([MastersAndDetails.ashx?HL=%d0%b0%d0%b3%d1%80%d0%b5%d0%b3%d0%b0%d1%86%d0%b8%d1%8f#%D0%A0%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D0%B0%D1%86%D0%B8%D0%B8_%D0%BF%D0%BE_%D1%80%D0%B8%D1%81%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8E_%D0%B4%D0%B8%D0%B0%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D1%8B_%D0%BA%D0%BB%D0%B0%D1%81%D1%81%D0%BE%D0%B2_0|рекомендации по рисованию диаграммы классов))
#** Не должно быть связей типа "Агрегация" (может быть только ассоциация и композиция)
#** Не должно быть связей со множественностью "1 к 1"
#** Не должно быть связей со множественностью "* к *"
#* Проверка имен классов - имена классов `не должны` содержать пробелов
#* Подписывание связей между классами
#** Все связи должны иметь подписи со стороны "1"
#** Подписи не должны содержать пробелов
#* Проставление типов атрибутов классов (подробнее про [TypesMap|карту типов) и [Attributes-class-data|атрибуты классов))
#** Убедиться, что используются [NullableTypes|Nullable-аналоги) соответствующих типов (DateTime, int, bool, decimal...)
#* Проставление значений по умолчанию (подробнее про [FeaturesOfDafaultValueAssignment|значения по умолчанию)).

`__Примечание__: При несоблюдении вышеозначенных требований возможны ошибки при генерации прототипа. `Перед продолжением убедитесь, что требования соблюдены``


* Создание диаграммы с формами и приложением при помощи `[Using-Quick-Prototyping|быстрой прототипизации)`


* [AuditCaseberrySetup|Настройка аудита)
#* Включение или отключение аудита
#* Настройка хранения данных аудита
#* Настройка аудита для класса, его собственных полей, мастеров и детейлов


* Настройка представлений
#* Создание всех видов представлений (подробнее о [View-types|видах представлений))
#* Настройка наименований полей
#* Настройка видимых и скрытых полей ([Hidden-Properties-In-View|подробнее))


* Настройка приложения
#* Настройка класса «[Application|Application)»
#* Настройка [Формы-списка-классы-со-стереотипом-listform|форм списка)
#* Настройка [Формы-редактирования-классы-со-стереотипом-editform|форм редактирования)




### Настройка генерации приложения


Связывание приложения с базой MS SQL Server, а также настройка наименования создаваемого прототипа и пути к каталогу, в который будет сгенерировано приложение. После окончания настройки можно переходить непосредственно к генерации приложения.

* Путь к базе ([Configure-MS-SQL-Server-direct-generator|настройка MS SQL Direct Generator))
* Наименование продукта и путь к каталогу генерации проекта ([ProjectCustomization|настройки генератора кода))


### Генерация и развертывание приложения


Создание базы, привязка к которой была выполнена на предыдущем шаге, а также приведение её в соответствие с моделью проектируемого приложения. Сборка приложения и создание проекта Visual Studio. Развертывание приложения.

* Создание базы ([Matching-DB-Microsoft-SQL-Server|подробнее о создании базы), а также для [Flexberry-ASP-NET-Generator|Web))
* Сборка приложения ([Generate-code-and-other-function-module-CSharp|Win), [Flexberry-ASP-NET-Generator|Web))
* Развертывание приложения


### Настройка созданного прототипа приложения


После создания приложения его необходимо настроить. Первым этапом настройки созданного Windows-прототипа является настройка фильтров (подробнее о [FiltersandLimits|фильтрах) и их [FilterExample|настройке)).

Дальнейшая настройка приложения осуществляется путем доработки проекта Visual Studio, т.е. с применением программирования. Об этом будет рассказано в другой статье.

## Типовые сценарии доработки модели приложения


После того, как прототип приложения был создано с нуля, начинается основная работа по доведению его до нужного состояния. В процессе доработки часто возникает необходимость доработать модель (к примеру, добавить новую сущность для хранения каких-либо дополнительных данных). Технология CASEBERRY позволяет дорабатывать модель созданного прототипа без потери уже внесенных в него на этапе программирования изменений.

* [AppDesktop|Настройка рабочего стола)


* [ChangeModel|Добавление новых классов в модель)
#* Добавить новые классы на диаграмму
#* Перегенерировать объекты
#* Перегенерировать формы


* [ChangeModel|Внесение изменений в существующие классы): добавление полей в существующие классы, переименование классов, добавление новых связей
#* Внести изменения в диаграмму классов ([Class-diagram-editor-features-work|особенности работы с редактором диаграммы классов))
#* Перегенерировать объекты
#* Перегенерировать формы


* Изменение представления списковой формы
#* Внести изменения в [LView|L-представление)
#* Перегенерировать объекты
#* Перегенерировать формы


* Изменение представления формы редактирования
#* Внести изменения в [EView|E-представление)
#* Перегенерировать объекты
#* Перегенерировать формы


* Внесение изменений в полномочия ([RightManager-module|подробнее о подсистеме полномочий), [http://storm:2011/%d0%9f%d0%be%d0%b4%d1%81%d0%b8%d1%81%d1%82%d0%b5%d0%bc%d0%b0-%d0%bf%d0%be%d0%bb%d0%bd%d0%be%d0%bc%d0%be%d1%87%d0%b8%d0%b8.ashx#%D0%9A%D0%BE%D0%BD%D1%81%D0%BE%D0%BB%D1%8C_%D1%83%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F_%D0%BF%D0%BE%D0%BB%D0%BD%D0%BE%D0%BC%D0%BE%D1%87%D0%B8%D1%8F%D0%BC%D0%B8_Security_Console_4|Security Console))


* Внесение изменений в фильтры
#* Внести изменения в [TView|T-представление)
#* Перегенерировать объекты


* Добавление новых приложений
#* Добавление новых классов «Application» ([Several-classes-of-applications-in-a-single-stage|подробнее))
#* Настройка рабочего стола