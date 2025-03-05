**Домашнее задание "Организация проекта при помощи облачных провайдеров"**

**Задание**

Организовать отказоустойчивую инфраструктуру в облаке Yandex Cloud с использованием Object Storage, группы виртуальных машин и сетевого балансировщика нагрузки.

**Выполнение задания**

**1. Создание Object Storage и размещение файла**

**1.1. Создание бакета**
```bash
yc storage bucket create --name byzgaev-20250305
```
![image](https://github.com/Byzgaev-I/Computing-power.Load-balancers/blob/main/1-1.png)

**1.2. Загрузка файла в бакет**   

```bash
aws --endpoint-url=https://storage.yandexcloud.net \
    s3 cp "/home/dextron/Загрузки/netologyRobots.png" \
    s3://byzgaev-20250305/netologyRobots.png \
    --profile yc
```

![image](https://github.com/Byzgaev-I/Computing-power.Load-balancers/blob/main/загрузка%20картинки%20в%20бакет.png)































































