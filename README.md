# Домашнее задание к занятию 14 «Средство визуализации Grafana» - `Мурчин Артем`

## Задание повышенной сложности

**При решении задания 1** не используйте директорию [help](./help) для сборки проекта. Самостоятельно разверните grafana, где в роли источника данных будет выступать prometheus, а сборщиком данных будет node-exporter:

- grafana;
- prometheus-server;
- prometheus node-exporter.

За дополнительными материалами можете обратиться в официальную документацию grafana и prometheus.

В решении к домашнему заданию также приведите все конфигурации, скрипты, манифесты, которые вы 
использовали в процессе решения задания.

**При решении задания 3** вы должны самостоятельно завести удобный для вас канал нотификации, например, Telegram или email, и отправить туда тестовые события.

В решении приведите скриншоты тестовых событий из каналов нотификаций.

## Обязательные задания

### Задание 1

1. Используя директорию [help](./help) внутри этого домашнего задания, запустите связку prometheus-grafana.
1. Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
1. Подключите поднятый вами prometheus, как источник данных.
1. Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

## Решение 1

Запустил связку prometheus-grafana:

![alt text](https://github.com/artmur1/20-02-grafana-hw/blob/main/img/20-02-01-01-hw.png)

Зашел в веб-интерфейс grafana:

![alt text](https://github.com/artmur1/20-02-grafana-hw/blob/main/img/20-02-01-02-hw.png)

Внес правки указав порты прометеус. Подключи поднятый prometheus, как источник данных:

![alt text](https://github.com/artmur1/20-02-grafana-hw/blob/main/img/20-02-01-03-hw.png)

## Задание 2

Изучите самостоятельно ресурсы:

1. [PromQL tutorial for beginners and humans](https://valyala.medium.com/promql-tutorial-for-beginners-9ab455142085).
1. [Understanding Machine CPU usage](https://www.robustperception.io/understanding-machine-cpu-usage).
1. [Introduction to PromQL, the Prometheus query language](https://grafana.com/blog/2020/02/04/introduction-to-promql-the-prometheus-query-language/).

Создайте Dashboard и в ней создайте Panels:

- утилизация CPU для nodeexporter (в процентах, 100-idle);
- CPULA 1/5/15;
- количество свободной оперативной памяти;
- количество места на файловой системе.

Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.

## Решение 2

Утилизация CPU для nodeexporter (в процентах, 100-idle):

    100 - avg(irate(node_cpu_seconds_total{job="nodeexporter", mode="idle"}[1m])) * 100

![alt text](https://github.com/artmur1/20-02-grafana-hw/blob/main/img/20-02-02-01-hw.png)

Средняя нагрузка на процессор CPULA 1/5/15;

    node_load1
    node_load5
    node_load15

![alt text](https://github.com/artmur1/20-02-grafana-hw/blob/main/img/20-02-02-02-hw.png)

количество свободной оперативной памяти;

    node_memory_MemTotal_bytes
    node_memory_MemFree_bytes

![alt text](https://github.com/artmur1/20-02-grafana-hw/blob/main/img/20-02-02-03-hw.png)

количество места на файловой системе.

    node_filesystem_avail_bytes

![alt text](https://github.com/artmur1/20-02-grafana-hw/blob/main/img/20-02-02-04-hw.png)

## Задание 3

1. Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
1. В качестве решения задания приведите скриншот вашей итоговой Dashboard.

## Решение 3

Скриншот итоговой Dashboard:

![alt text](https://github.com/artmur1/20-02-grafana-hw/blob/main/img/20-02-03-01-hw.png)

## Задание 4

1. Сохраните ваш Dashboard. Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
1. В качестве решения задания приведите листинг этого файла.

## Решение 4

листинг «JSON MODEL» файла: https://github.com/artmur1/20-02-grafana-hw/blob/main/img/JSON%20Model.txt

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
