---
title: "Introduction"
permalink: /docs/s03-p01-introduction/
redirect_from:
  - /theme-setup/
---
In development...

##Эксперимент. 

Вычисление потребляемых реурсов при одинаковых условиях для каждой подключенной сети, а также поведение фоновой задачи системы проверки уведомлений при различных условиях на различных версиях операционной системы.

*Алгоритм вычисления времени запуска сервиса*

*Для каждого типа проверки вычисляется ожидаемое время следующей проверки: expected_check_timestamp* 

*равное текущему времени (timestamp) + интервалу между проверками для данного типа проверок*

*Следующий запуск сервиса производится интервале:*

*минимальный [expected_check_timestamp] - [текущий timestamp]* 

*Конец окна запуска:*

*[timestamp начала окна] + [ширина окна запуска]*

*Значение [начала окна запуска] не может быть меньше минуты* 

| Время эксперимента        | 2 часа   |
| ------------------------- | -------- |
| Минимальный интервал      | 1 минута |
| Ширина окна вызова        | 1 минута |
| Интервал между проверками | 5 минут  |

| Эксперимент | Состояние устройства | Состояние приложения | Версия android |
| ----------- | -------------------- | -------------------- | -------------- |
| try1(4.4)   | Всегда активно       | Открыто              | 4.4            |
| try2(4.4)   | Всегда активно       | Закрыто              | 4.4            |
| try3(4.4)   | Всегда активно       | Свернуто             | 4.4            |
| try4(4.4)   | Заблокировано(сон)   | Открыто              | 4.4            |
| try5(4.4)   | Заблокировано(сон)   | Закрыто              | 4.4            |
| try6(4.4)   | Заблокировано(сон)   | Свернуто             | 4.4            |
| try1(8.0)   | Всегда активно       | Открыто              | 8.0            |
| try2(8.0)   | Всегда активно       | Закрыто              | 8.0            |
| try3(8.0)   | Всегда активно       | Свернуто             | 8.0            |
| try4(8.0)   | Заблокировано(сон)   | Открыто              | 8.0            |
| try5(8.0)   | Заблокировано(сон)   | Закрыто              | 8.0            |
| try6(8.0)   | Заблокировано(сон)   | Свернуто             | 8.0            |

| **Общее**                         |             | try1(4.4) | try2(4.4) | try3(4.4) | try4(4.4) |
| --------------------------------- | ----------- | --------- | --------- | --------- | --------- |
| Время эксперимента                | (Минуты)    | 114,38    | 114,95    | 114,66    | 114,49    |
| Время работы сервиса              | (Минуты)    | 9,39      | 8,82      | 8,63      | 8,43      |
| Время проверок                    | (Минуты)    | 9,19      | 8,63      | 8,44      | 8,26      |
| Использованный трафик             | (Мегабайты) | 9,41      | 9,95      | 9,40      | 9,86      |
| Количество запусков сервиса       |             | 20,00     | 20,00     | 20,00     | 20,00     |
| **Количество проверок**           |             |           |           |           |           |
| facebook_messages                 |             | 20,00     | 20,00     | 20,00     | 20,00     |
| facebook_notifications            |             | 20,00     | 20,00     | 20,00     | 20,00     |
| google_plus_notifications         |             | 20,00     | 20,00     | 20,00     | 20,00     |
| instagram_notifications           |             | 20,00     | 20,00     | 20,00     | 20,00     |
| odnoklassniki_messages            |             | 20,00     | 20,00     | 20,00     | 20,00     |
| odnoklassniki_notifications       |             | 20,00     | 20,00     | 20,00     | 20,00     |
| tumblr_notifications              |             | 20,00     | 20,00     | 20,00     | 20,00     |
| twitter_messages                  |             | 20,00     | 20,00     | 20,00     | 20,00     |
| twitter_notifications             |             | 20,00     | 20,00     | 20,00     | 20,00     |
| **spend traffic (all)**           | (Мегабайты) |           |           |           |           |
| facebook_messages                 |             | 0,85      | 0,81      | 0,88      | 0,80      |
| facebook_notifications            |             | 1,31      | 1,45      | 1,20      | 1,52      |
| google_plus_notifications         |             | 2,15      | 2,59      | 2,47      | 2,74      |
| instagram_notifications           |             | 0,98      | 1,03      | 0,77      | 0,86      |
| odnoklassniki_messages            |             | 0,39      | 0,40      | 0,40      | 0,39      |
| odnoklassniki_notifications       |             | 0,21      | 0,21      | 0,21      | 0,22      |
| tumblr_notifications              |             | 1,65      | 1,64      | 1,64      | 1,61      |
| twitter_messages                  |             | 0,46      | 0,44      | 0,44      | 0,36      |
| twitter_notifications             |             | 1,40      | 1,39      | 1,39      | 1,36      |
| **spend traffic (average check)** | (Килобайты) |           |           |           |           |
| facebook_messages                 |             | 42,43     | 40,26     | 44,06     | 39,79     |
| facebook_notifications            |             | 65,65     | 72,70     | 60,14     | 76,01     |
| google_plus_notifications         |             | 107,68    | 129,48    | 123,39    | 137,10    |
| instagram_notifications           |             | 48,95     | 51,48     | 38,28     | 42,91     |
| odnoklassniki_messages            |             | 19,48     | 19,97     | 19,98     | 19,28     |
| odnoklassniki_notifications       |             | 10,47     | 10,50     | 10,49     | 10,89     |
| tumblr_notifications              |             | 82,60     | 81,75     | 82,19     | 80,73     |
| twitter_messages                  |             | 22,84     | 22,01     | 22,15     | 17,96     |
| twitter_notifications             |             | 70,23     | 69,47     | 69,55     | 68,25     |
| **spend time (all)**              | (Секунды)   |           |           |           |           |
| facebook_messages                 |             | 65,87     | 61,03     | 59,20     | 57,56     |
| facebook_notifications            |             | 69,86     | 65,26     | 63,04     | 74,72     |
| google_plus_notifications         |             | 48,05     | 52,14     | 46,52     | 49,85     |
| instagram_notifications           |             | 139,99    | 129,49    | 128,50    | 121,40    |
| odnoklassniki_messages            |             | 35,33     | 33,25     | 33,23     | 31,67     |
| odnoklassniki_notifications       |             | 19,49     | 19,26     | 17,30     | 17,81     |
| tumblr_notifications              |             | 84,22     | 76,13     | 75,71     | 78,87     |
| twitter_messages                  |             | 24,12     | 22,92     | 22,96     | 13,08     |
| twitter_notifications             |             | 64,67     | 58,33     | 59,87     | 50,49     |
| **spend time (average check)**    | (Секунды)   |           |           |           |           |
| facebook_messages                 |             | 3,29      | 3,05      | 2,96      | 2,88      |
| facebook_notifications            |             | 3,49      | 3,26      | 3,15      | 3,74      |
| google_plus_notifications         |             | 2,40      | 2,61      | 2,33      | 2,49      |
| instagram_notifications           |             | 7,00      | 6,47      | 6,42      | 6,07      |
| odnoklassniki_messages            |             | 1,77      | 1,66      | 1,66      | 1,58      |
| odnoklassniki_notifications       |             | 0,97      | 0,96      | 0,87      | 0,89      |
| tumblr_notifications              |             | 4,21      | 3,81      | 3,79      | 3,94      |
| twitter_messages                  |             | 1,21      | 1,15      | 1,15      | 0,65      |
| twitter_notifications             |             | 3,23      | 2,92      | 2,99      | 2,52      |

| **Общее**                         |             | try5(4.4) | try6(4.4) | try1(8.0) | try2(8.0) |
| --------------------------------- | ----------- | --------- | --------- | --------- | --------- |
| Время эксперимента                | (Минуты)    | 114,91    | 114,43    | 114,48    | 115,49    |
| Время работы сервиса              | (Минуты)    | 8,42      | 8,81      | 4,06      | 4,04      |
| Время проверок                    | (Минуты)    | 8,25      | 8,60      | 3,97      | 3,96      |
| Использованный трафик             | (Мегабайты) | 9,52      | 9,49      | 12,37     | 11,95     |
| Количество запусков сервиса       |             | 20,00     | 20,00     | 20,00     | 19,00     |
| **Количество проверок**           |             |           |           |           |           |
| facebook_messages                 |             | 20,00     | 20,00     | 20,00     | 19,00     |
| facebook_notifications            |             | 20,00     | 20,00     | 20,00     | 19,00     |
| google_plus_notifications         |             | 20,00     | 20,00     | 20,00     | 19,00     |
| instagram_notifications           |             | 20,00     | 20,00     | 20,00     | 19,00     |
| odnoklassniki_messages            |             | 20,00     | 20,00     | 20,00     | 19,00     |
| odnoklassniki_notifications       |             | 20,00     | 20,00     | 20,00     | 19,00     |
| tumblr_notifications              |             | 20,00     | 20,00     | 20,00     | 19,00     |
| twitter_messages                  |             | 20,00     | 20,00     | 20,00     | 19,00     |
| twitter_notifications             |             | 20,00     | 20,00     | 20,00     | 19,00     |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |
| **spend traffic (all)**           | (Мегабайты) |           |           |           |           |
| facebook_messages                 |             | 0,81      | 0,79      | 0,93      | 1,19      |
| facebook_notifications            |             | 1,49      | 1,56      | 1,15      | 1,20      |
| google_plus_notifications         |             | 2,19      | 2,39      | 3,85      | 3,32      |
| instagram_notifications           |             | 1,00      | 0,71      | 1,14      | 1,19      |
| odnoklassniki_messages            |             | 0,40      | 0,40      | 0,48      | 0,46      |
| odnoklassniki_notifications       |             | 0,21      | 0,21      | 0,22      | 0,22      |
| tumblr_notifications              |             | 1,64      | 1,65      | 1,76      | 1,79      |
| twitter_messages                  |             | 0,42      | 0,42      | 1,59      | 1,45      |
| twitter_notifications             |             | 1,36      | 1,36      | 1,26      | 1,13      |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |
| **spend traffic (average check)** | (Килобайты) |           |           |           |           |
| facebook_messages                 |             | 40,50     | 39,54     | 46,30     | 62,64     |
| facebook_notifications            |             | 74,63     | 77,93     | 57,36     | 63,19     |
| google_plus_notifications         |             | 109,48    | 119,45    | 192,25    | 174,49    |
| instagram_notifications           |             | 50,13     | 35,36     | 56,93     | 62,84     |
| odnoklassniki_messages            |             | 19,80     | 20,12     | 23,90     | 24,31     |
| odnoklassniki_notifications       |             | 10,52     | 10,67     | 10,92     | 11,66     |
| tumblr_notifications              |             | 82,10     | 82,38     | 88,22     | 94,37     |
| twitter_messages                  |             | 20,80     | 21,05     | 79,64     | 76,07     |
| twitter_notifications             |             | 67,93     | 67,87     | 63,21     | 59,55     |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |
| **spend time (all)**              | (Секунды)   |           |           |           |           |
| facebook_messages                 |             | 59,25     | 61,31     | 35,18     | 38,63     |
| facebook_notifications            |             | 71,93     | 75,66     | 25,54     | 25,33     |
| google_plus_notifications         |             | 46,09     | 47,97     | 10,11     | 13,37     |
| instagram_notifications           |             | 124,80    | 131,06    | 46,25     | 43,68     |
| odnoklassniki_messages            |             | 32,49     | 34,56     | 10,74     | 10,06     |
| odnoklassniki_notifications       |             | 17,46     | 18,95     | 7,57      | 7,52      |
| tumblr_notifications              |             | 76,78     | 77,64     | 28,57     | 27,92     |
| twitter_messages                  |             | 15,27     | 16,50     | 52,44     | 51,73     |
| twitter_notifications             |             | 51,00     | 52,53     | 21,93     | 19,32     |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |
| **spend time (average check)**    | (Секунды)   |           |           |           |           |
| facebook_messages                 |             | 2,96      | 3,07      | 1,76      | 2,03      |
| facebook_notifications            |             | 3,60      | 3,78      | 1,28      | 1,33      |
| google_plus_notifications         |             | 2,30      | 2,40      | 0,51      | 0,70      |
| instagram_notifications           |             | 6,24      | 6,55      | 2,31      | 2,30      |
| odnoklassniki_messages            |             | 1,62      | 1,73      | 0,54      | 0,53      |
| odnoklassniki_notifications       |             | 0,87      | 0,95      | 0,38      | 0,40      |
| tumblr_notifications              |             | 3,84      | 3,88      | 1,43      | 1,47      |
| twitter_messages                  |             | 0,76      | 0,83      | 2,62      | 2,72      |
| twitter_notifications             |             | 2,55      | 2,63      | 1,10      | 1,02      |

| **Общее**                         |             | try3(8.0) | try4(8.0) | try5(8.0) | try6(8.0) |
| --------------------------------- | ----------- | --------- | --------- | --------- | --------- |
| Время эксперимента                | (Минуты)    | 118,94    | 118,05    | 115,99    | 112,82    |
| Время работы сервиса              | (Минуты)    | 4,24      | 3,33      | 3,69      | 3,45      |
| Время проверок                    | (Минуты)    | 4,15      | 3,26      | 3,62      | 3,39      |
| Использованный трафик             | (Мегабайты) | 13,19     | 9,96      | 10,94     | 10,60     |
| Количество запусков сервиса       |             | 20,00     | 15,00     | 17,00     | 16,00     |
| **Количество проверок**           |             |           |           |           |           |
| facebook_messages                 |             | 20,00     | 15,00     | 17,00     | 16,00     |
| facebook_notifications            |             | 20,00     | 15,00     | 17,00     | 16,00     |
| google_plus_notifications         |             | 20,00     | 15,00     | 17,00     | 16,00     |
| instagram_notifications           |             | 20,00     | 15,00     | 17,00     | 16,00     |
| odnoklassniki_messages            |             | 20,00     | 15,00     | 17,00     | 16,00     |
| odnoklassniki_notifications       |             | 20,00     | 15,00     | 17,00     | 16,00     |
| tumblr_notifications              |             | 20,00     | 15,00     | 17,00     | 16,00     |
| twitter_messages                  |             | 20,00     | 15,00     | 17,00     | 16,00     |
| twitter_notifications             |             | 20,00     | 15,00     | 17,00     | 16,00     |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |
| **spend traffic (all)**           | (Мегабайты) |           |           |           |           |
| facebook_messages                 |             | 1,02      | 0,80      | 0,93      | 0,74      |
| facebook_notifications            |             | 1,36      | 1,03      | 1,04      | 0,83      |
| google_plus_notifications         |             | 3,87      | 2,62      | 2,82      | 3,14      |
| instagram_notifications           |             | 1,65      | 1,48      | 1,71      | 1,83      |
| odnoklassniki_messages            |             | 0,48      | 0,37      | 0,42      | 0,40      |
| odnoklassniki_notifications       |             | 0,22      | 0,16      | 0,19      | 0,18      |
| tumblr_notifications              |             | 1,78      | 1,42      | 1,58      | 1,46      |
| twitter_messages                  |             | 1,59      | 1,14      | 1,10      | 0,98      |
| twitter_notifications             |             | 1,22      | 0,95      | 1,15      | 1,04      |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |
| **spend traffic (average check)** | (Килобайты) |           |           |           |           |
| facebook_messages                 |             | 51,12     | 53,03     | 54,86     | 46,28     |
| facebook_notifications            |             | 67,91     | 68,39     | 61,13     | 52,11     |
| google_plus_notifications         |             | 193,53    | 174,35    | 165,86    | 196,32    |
| instagram_notifications           |             | 82,63     | 98,95     | 100,42    | 114,10    |
| odnoklassniki_messages            |             | 23,88     | 24,80     | 24,66     | 25,27     |
| odnoklassniki_notifications       |             | 11,03     | 10,94     | 11,12     | 11,28     |
| tumblr_notifications              |             | 88,93     | 94,38     | 93,05     | 91,41     |
| twitter_messages                  |             | 79,67     | 76,28     | 64,45     | 61,30     |
| twitter_notifications             |             | 60,75     | 63,11     | 67,77     | 64,73     |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |
| **spend time (all)**              | (Секунды)   |           |           |           |           |
| facebook_messages                 |             | 34,98     | 28,11     | 30,16     | 27,18     |
| facebook_notifications            |             | 26,87     | 21,96     | 23,10     | 21,13     |
| google_plus_notifications         |             | 18,01     | 14,25     | 13,88     | 17,23     |
| instagram_notifications           |             | 47,81     | 35,00     | 39,98     | 39,25     |
| odnoklassniki_messages            |             | 10,56     | 9,80      | 8,67      | 8,82      |
| odnoklassniki_notifications       |             | 7,43      | 5,06      | 5,31      | 5,46      |
| tumblr_notifications              |             | 27,21     | 21,00     | 37,49     | 24,82     |
| twitter_messages                  |             | 55,45     | 42,48     | 39,25     | 39,12     |
| twitter_notifications             |             | 20,91     | 18,08     | 19,13     | 20,09     |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |
| **spend time (average check)**    | (Секунды)   |           |           |           |           |
| facebook_messages                 |             | 1,75      | 1,87      | 1,77      | 1,70      |
| facebook_notifications            |             | 1,34      | 1,46      | 1,36      | 1,32      |
| google_plus_notifications         |             | 0,90      | 0,95      | 0,82      | 1,08      |
| instagram_notifications           |             | 2,39      | 2,33      | 2,35      | 2,45      |
| odnoklassniki_messages            |             | 0,53      | 0,65      | 0,51      | 0,55      |
| odnoklassniki_notifications       |             | 0,37      | 0,34      | 0,31      | 0,34      |
| tumblr_notifications              |             | 1,36      | 1,40      | 2,21      | 1,55      |
| twitter_messages                  |             | 2,77      | 2,83      | 2,31      | 2,45      |
| twitter_notifications             |             | 1,05      | 1,21      | 1,13      | 1,26      |
|                                   |             |           |           |           |           |
|                                   |             |           |           |           |           |



## Статистика

- количетсво запусков отдельной сети
- время использорвания сети
- получено уведомлений
- ...

