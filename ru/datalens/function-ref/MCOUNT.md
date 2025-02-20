---
editable: false
sourcePath: ru/_api-ref/datalens/function-ref/MCOUNT.md
---


# MCOUNT (оконная)



#### Синтаксис {#syntax}


```
MCOUNT( value, rows_1 [ , rows_2 ] [ TOTAL | WITHIN ... | AMONG ... ] [ ORDER BY ... ] [ BEFORE FILTER BY ... ] )
```

#### Описание {#description}

{% note warning %}

Сортировка осуществляется на основе полей, перечисленных в области сортировки в чарте и в ORDER BY. При этом сначала берутся поля из `ORDER BY`.

{% endnote %}

Возвращает количество значений (не равных `NULL`) по окну записей, которое определяется порядком сортировки и аргументами:

| `rows_1`      | `rows_2`   | Окно                                                             |
|:--------------|:-----------|:-----------------------------------------------------------------|
| положительное | -          | Текущая запись и `rows_1` предшествующих.                        |
| отрицательное | -          | Текущая запись и -`rows_1` последующих.                          |
| любой знак    | любой знак | `rows_1` предшествующих записей, текущая и `rows_2` последующих. |



Аналогичное поведение у оконных функций [MSUM](MSUM.md), [MMIN](MMIN.md), [MMAX](MMAX.md), [MAVG](MAVG.md).

См. также [COUNT](COUNT.md), [RCOUNT](RCOUNT.md).

**Типы аргументов:**
- `value` — `Любой`
- `rows_1` — `Целое число`
- `rows_2` — `Целое число`


**Возвращаемый тип**: Совпадает с типом аргументов (`value`)

{% note info %}

Значения аргументов (`rows_1`, `rows_2`) должны быть константами.

{% endnote %}


#### Примеры {#examples}

```
MCOUNT([Profit], -2)
```

```
MCOUNT([Profit], 3)
```

```
MCOUNT([Profit] 5, 5 TOTAL)
```

```
MCOUNT([Profit], -5 WITHIN [Date])
```

```
MCOUNT([Profit], -5 AMONG [Date])
```


#### Поддержка источников данных {#data-source-support}

`Материализованный датасет`, `ClickHouse 19.13`, `Microsoft SQL Server 2017 (14.0)`, `MySQL 5.6`, `Oracle Database 12c (12.1)`, `PostgreSQL 9.3`.
