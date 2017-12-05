---
title: "Создание и публикация отчетов"
permalink: /docs/s03-p00-intro/
redirect_from:
  - /theme-setup/
toc: true
---
## Создание репозитория

Создадим репозиторий на GitHub с названием `report-example` и загрузим в него созданный ранее проект Sphinx.

Подробнее о том, как это сделать написано в разделе [git](/ABC-Unix-Guide/docs/s01-p02-git/)

## Настройка репозитория

Чтобы происходила автоматическая перегенерация отчета в службе `Read the Docs` при изменении репозитория на GitHub, нужно добавить эту службу в настройках репозитория.

Для этого нужно перейти в репозитории во вкладку `Settings` и выбрать вкладку `Integrations & services`. Далее нажать на `Add service` и добавить службу `ReadTheDocs`.

![alt]({{ "/assets/images/git1.png" | absolute_url }})

Рисунок 1 - Добавление сервиса ReadTheDocs

