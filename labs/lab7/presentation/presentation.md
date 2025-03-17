---
## Front matter
lang: ru-RU
title: Лабораторная работа 7
subtitle: Модель $M|M|1|\infty$
author:
  - Хватов М.Г.
institute:
  - Российский университет дружбы народов, Москва, Россия

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="60%"}

  * Хватов Максим Григорьевич
  * студент
  * Российский университет дружбы народов
  * [1032204364@pfur.ru](mailto:1032204364@pfur.ru)

:::
::: {.column width="25%"}

![](./image/mgkhvatov.jpg)

:::
::::::::::::::

## Цель работы

Рассмотреть пример моделирования в *xcos* системы массового обслуживания типа $M|M|1|\infty$.

## Задание

1. Реализовать модель системы массового обслуживания типа $M|M|1|\infty$;
2. Построить график поступления и обработки заявок;
3. Построить график динамики размера очереди.

## Выполнение лабораторной работы

![Задание переменных окружения в xcos для модели](image/1.png){#fig:001 width=70%}

## Выполнение лабораторной работы

![Суперблок, моделирующий поступление заявок](image/2.png){#fig:002 width=50%}

## Выполнение лабораторной работы

![Суперблок, моделирующий обработку заявок](image/3.png){#fig:003 width=50%}

## Выполнение лабораторной работы

![Модель $M|M|1|\infty$ в xcos](image/4.png){#fig:004 width=50%}

## Выполнение лабораторной работы

![Динамика размера очереди](image/5.png){#fig:005 width=60%}

## Выполнение лабораторной работы

![Поступление и обработка заявок](image/6.png){#fig:006 width=50%}

## Выводы

В процессе выполнения данной лабораторной работы я рассмотрел пример моделирования в *xcos* системы массового обслуживания типа $M|M|1|\infty$.