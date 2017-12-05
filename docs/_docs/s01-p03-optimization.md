---
title: "Optimization of used resources"
permalink: /docs/s01-p03-optimization/
redirect_from:
  - /theme-setup/
toc: true
---
## Проблемы оптимизации мультисервеного приложения

В большинстве клиентов для социальных сетей присутствуют функции для оповещения пользователей о различных событиях, например, получении новых личных сообщений. Чтобы мультисерверное клиентское приложение для социальных сетей могло конкурировать с клиентскими приложениями для отдельных социальных сетей, в нем должны быть реализованы такие функции. При этом оповещения должны срабатывать при событиях в любых из активных социальных сетей независимо от других.

Для проверки наличия уведомлений обычно используется интерфейс прикладного программирования (далее API). Сначала выполняется API-запрос, содержащий адрес социальной сети, название метода , при необходимости, ключ доступа (access token) и другие параметры. Пример запроса для проверки наличия уведомлений в социальной сети Вконтакте[[7]](/afflyas/docs/s01-p06-references/) приведен на рисунке 2.1. Ответом на API-запрос обычно является json или xml документ, из которого извлекаются необходимые данные.

Во многих социальных сетях такие API-запросы не доступны для сторонних разработчиков, либо доступны, но не в полном объеме. Поэтому, для получения нужных данных приходится применять другие способы, например, загружать и анализировать(парсить) web-страницы. На рисунке 2.1 приведен пример методики полученияуведомлений в сети Facebook [[8]](/afflyas/docs/s01-p06-references/). Так как вэтой сети, для сторонних разработчиков,недоступны методы проверки уведомлений,для получения значения переменной,хранящей состояние наличия новых уведомлений, нужно загрузить и проанализировать web-страницу, отображающую уведомления на сайте социальной сети. Затем, в зависимости от полученных данных, изменить значение переменной.

![alt]({{ "/assets/images/s01-check-methods.png" | absolute_url }})

Рисунок 2.1 — методы проверки наличия уведомлений

Такие методы получения данных намного более затратны по потреблению интернет трафика и ресурсов устройства. Следовательно частоту использования таких функций следует оптимизировать для комфортной работы с приложением. 

Такая система, способная проверять наличие уведомлений в различных социальных сетях, использующая для этого затратные по ресурсам методы является объектом для оптимизации вданной научно-исследовательской работе.

## Варианты решения проблемы оптимизации

Так как методы, используемые в приложении для проверки наличия уведомлений, потребляют в несколько раз больше интернет трафика и ресурсов устройства, нужно рассмотреть способы ограничения использования этих ресурсов.

Одним из вариантов может быть ограничение на количествои пользуемого интернет трафика за определенный промежуток времени (например, за месяц). 

При этом варианте следует учесть сколько ресурсов будет использовать каждая социальная сеть. Для этого нужно составить модели, показывающие, сколько ресурсов должна потреблять отдельная социальная сеть при разных обстоятельствах.

Допустим, установлено ограничение на потребление трафика в 500 Мбайт в месяц. Одним из вариантов поведения может быть то, что для каждой подключенной социальной сети отводится равное количество трафика (рисунок2.2а). Когда пользователь отключает одну из социальных сетей, количество используемого оставшимися социальными сетями трафика может остаться прежним, а остаток выделенных ресурсов не использоваться (рисунок 2.2б). Освободившиеся ресурсы также можно распределить между подключенными сетями (рисунок 2.2в).

Другим вариантом может быть то, что количество ресурсов, выделяемой для отдельной социальной сети, зависит отчастоты её использования. Если пользователь работает в основном с сетью VK и Twitter, то нет необходимости тратить лишние ресурсы и часто проверять обновления в сетях, которыми он реже пользуется. Лучше выделить эти ресурсы для проверки обновлений в часто используемых сетях (рисунок 2.2г). 

![alt]({{ "/assets/images/s01-traffic-usage-methods.png" | absolute_url }})

Рисунок 2.2 — варианты использования трафика

Составленные модели поведения можно сравнить ивыбрать из них самую оптимальную. Для сравнения моделей следует рассчитать их характеристики, такие как: среднее время получения сообщения; количество проверок за определенный промежуток времени; и другие.