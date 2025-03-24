---
## Front matter
lang: ru-RU
title: Лабораторная работа №8
subtitle:  Модель TCP/AQM
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

Реализовать модель TCP/AQM в xcos и OpenModelica.

## Задание

1. Построить модель TCP/AQM в xcos;
2. Построить графики динамики изменения размера TCP окна $W(t)$ и размера очереди $Q(t)$;
3. Построить модель TCP/AQM в OpenModelica;

## Выполнение лабораторной работы

![Установка контекста](image/1.png){#fig:001 width=70%}

## Выполнение лабораторной работы

![Модель TCP/AQM в xcos](image/2.png){#fig:002 width=70%}

## Выполнение лабораторной работы

```
parameter Real N=1;
parameter Real R=1;
parameter Real K=5.3;
parameter Real C=1;

Real W(start=0.1);
Real Q(start=1);

equation

der(W)= 1/R - W*delay(W, R)/(2*R)*K*delay(Q, R);
der(Q)= if (Q==0) then max(N*W/R-C,0) else (N*W/R-C);
```
## Выполнение лабораторной работы

![Динамика изменения размера TCP окна W (t) и размера очереди Q(t). OpenModelica](image/8.png){#fig:007 width=70%}

## Выполнение лабораторной работы

![Фазовый портрет (W, Q). OpenModelica](image/9.png){#fig:008 width=70%}

## Выводы

В процессе выполнения данной лабораторной работы я реализовал модель TCP/AQM в xcos и OpenModelica.