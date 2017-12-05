---
title: "Пример генерации отчета"
permalink: /docs/s03-p02-example/
redirect_from:
  - /theme-setup/
toc: true
---
## Создание проекта

Сгенерируем проект `report-example` при помощи команды `sphinx-quickstart`.

[Создание проекта в Sphinx](/ABC-Unix-Guide/docs/s01-p03-sphinx/)

[Синтаксис reStructuredText](/ABC-Unix-Guide/rst-syntax/)

## Файл конфигурации

Отредактируем файл конфигурации `conf.py`:

```python
# -*- coding: utf-8 -*-
extensions = []
templates_path = ['_templates']
source_suffix = '.rst'
master_doc = 'index'
project = u'report-example'
copyright = u'2017, Ivan Ivanov'
author = u'Ivan Ivanov'
version = u'1'
release = u'1'
language = 'ru'
exclude_patterns = []
todo_include_todos = False

import sphinx_rtd_theme
html_theme = "sphinx_rtd_theme"
html_theme_path = [sphinx_rtd_theme.get_html_theme_path()]

html_static_path = ['_static']

htmlhelp_basename = 'report-exampledoc'

latex_elements = {

}

latex_documents = [
    (master_doc, 'report-example.tex', u'report-example Documentation',
     u'Ivan Ivanov', 'manual'),
]

man_pages = [
    (master_doc, 'report-example', u'report-example Documentation',
     [author], 1)
]

texinfo_documents = [
    (master_doc, 'report-example', u'report-example Documentation',
     author, 'report-example', 'One line description of project.',
     'Miscellaneous'),
]
```

## Файл Index

Отредактируем файл Index в соответствии с правилами оформления отчетов:

```
==============================
Операционные системы GNU/Linux
==============================

Отчет о лабораторной работе №13

**Интерфейс, файловая система, командная строка**

Выполнил: ``Иван Иванов, группа 4949XL``

Цель работы
===========

* создать контейнер
* запустить контейнер
* узнать, что это за магия
* написать отчет

Выполнение работы
=================

При выполнении работы был запущен следующий код:

.. code-block:: Java
    
        class Main {
            public static void main(String[] args) {
    
                String report = "отчет";
    
                Dog sharik = new Dog();
    
                report = sharik.eat(report);
    
                System.out.println(report);
    
            }
        }
    
        class Dog {
    
            public String eat(String food){            
                return "Ваш " + food + " съела собака";
            }
        }

    В результате, отчет по лабораторной работе был съеден собакой, уж извините.

Команда на запуск контейнера
============================

``docker run hello-world``

Выводы
======

В процессе выполнения лабораторной работы я создал контейнер и узнал, что там внутри **тёмная** магия.
```