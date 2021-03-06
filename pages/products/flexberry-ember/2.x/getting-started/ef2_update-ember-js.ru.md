---
title: Обновление EmberJS на проектах
keywords: ember, ember-cli, update, version, upgrade
tags: [EmberJS]
sidebar: flexberry-ember-2_sidebar
toc: true
permalink: ru/ef2_update-ember-js.html
lang: ru
summary: Инструкция по обновлению EmberJS на проектах, которые используют Flexberry Ember.
---

## Общий подход к обновлению ember-cli

Обновление рекомендуется выполнять последовательно переключая версии `ember-cli`, выполнять на каждой новой версии инициализацию проекта и контролируя собираемость проекта и прохождение тестов. Также следует внимательно следить за `DEPRECATIONS`, поскольку от версии к версии они превращаются в ошибки.  
Самым удобным вариантом использования `ember-cli` со множеством версий является использование [Docker-контейнера с ember-cli](ef2_docker-for-ember-cli.html).

## Обновление с версии 2.4.3 до 3.0.0

Таблица, которая поможет при обновлении Ember.js до 3.x в плане замены имён в импортах на новые с «собаками»  
<https://github.com/emberjs/rfcs/blob/master/text/0176-javascript-module-api.md#addenda>

Хорошая новость ещё в том, что в Ember есть так называемые «кодмоды» - это пакеты, которые в автоматическом режиме позволяют в коде заменить старый синтаксис на новый при обновлении версий Ember.js.  
Вот соответствующий codemod для обновления имён в импортах (инструкция по использованию там в описании):  
<https://github.com/ember-codemods/ember-modules-codemod>

После запуска кодмода, возможно, что-то нужно будет ещё доправить руками.
