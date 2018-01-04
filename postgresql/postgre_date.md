# postgreでDATE型を扱うときの知識
date_part()を使うことによって、データを個別に取り出せる。

SELECT
    DATE_PART('YEAR',    insert_date) AS year,
    DATE_PART('MONTH', insert_date) AS month,
    DATE_PART('DAY',      insert_date) AS day
FROM hoge_table