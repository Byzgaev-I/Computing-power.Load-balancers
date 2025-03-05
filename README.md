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



**1.3.Настройка публичного доступа**

```bash
yc storage bucket update byzgaev-20250305 --public-read
```

![image](https://github.com/Byzgaev-I/Computing-power.Load-balancers/blob/main/1-3.png)


**1. Создание группы виртуальных машин**
**2.1. Создание Instance Group**

Конфигурация в файле instance-group.tf:

```hcl
resource "yandex_compute_instance_group" "ig-1" {
  name               = "fixed-ig-with-balancer-new"
  folder_id          = "b1gam4o6rj97es4peaq4"
  service_account_id = "ajeg971iui9o2i1ia9ai"
  
  instance_template {
    platform_id = "standard-v1"
    resources {
      memory = 2
      cores  = 2
    }
    boot_disk {
      initialize_params {
        image_id = "fd827b91d99psvq5fjit"
      }
    }
    network_interface {
      network_id = yandex_vpc_network.network.id
      subnet_ids = [yandex_vpc_subnet.subnet.id]
      nat       = true
    }

```




















































