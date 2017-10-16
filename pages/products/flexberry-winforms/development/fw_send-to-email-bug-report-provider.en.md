---
title: Отправка сообщения об ошибке по электронной почте
sidebar: flexberry-winforms_sidebar
keywords: Windows UI (формы)
toc: true
permalink: en/fw_send-to-email-bug-report-provider.html
folder: products/flexberry-winforms/
lang: en
---

В стандартном окне сообщения об ошибке появилась возможность отправить письмо с сообщением об ошибке.

![](/images/pages/products/flexberry-winforms/development/error-form.png)

При выборе пункта меню "Отправить по электронной почте..." запускается почтовый клиент по умолчанию. Письмо содержит вложение с архивом, в котором находятся снимок экрана, описание ошибки и информация о текущей системной конфигурации.
![](/images/pages/products/flexberry-winforms/development/letter.png)

Для запуска почтового клиента используется интерфейс MAPI.
Адрес отправки, заголовок и текст сообщения могут быть настроены в конфигурационном файле приложения с помощью ключей BugReportEmailAddress, BugReportEmailTitle, BugReportEmailBody.

__Пример:__

```
<add key="BugReportEmailAddress" value="user@perm.ru" />
<add key="BugReportEmailTitle" value="Ошибка в Кошках или Лапах" />
<add key="BugReportEmailBody" value="Текст сообщения" />
```
Если указанный ключи не определены в конфигурационном файле, используются значение по умолчанию.

''Адрес'': пробел (пустую строку MAPI не принимает).

''Тема'': Ошибка {ИмяИсполнимогоФайла}.

''Текст сообщения'': В процессе работы пользователя {ИмяWindowsПользователя} в программе { ИмяИсполнимогоФайла} произошла ошибка. Дополнительная информация находится во вложении.

__Замечание:__

Для временного хранения архива используется папка Environment.SpecialFolder.InternetCache. Однако файл автоматически не удаляется, т.к. он не может быть удален до отправки сообщения.