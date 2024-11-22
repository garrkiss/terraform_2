# Домашнее задание к занятию "`Основы Terraform. Yandex Cloud`" - `Бакулев Евгений`

### Задание 1

Скриншот ЛК Yandex Cloud

![Скриншот](https://github.com/garrkiss/terraform_2/blob/main/img/task1/task1.png)

### Ошибки

1. 
![Скриншот](https://github.com/garrkiss/terraform_2/blob/main/img/task1/error%20task1/1.png)

Ответ:
Прописать правильный путь расположения файла authorized_key.json

2. 
```
Error: Error getting zone while creating instance: cannot determine zone: please set 'zone' key in this resource or at provider level

with yandex_compute_instance.platform,
on main.tf line 15, in resource "yandex_compute_instance" "platform":
15: resource "yandex_compute_instance" "platform" {
```
Ответ:
В файле "main.tf" нужно указать 'zone' для resource "yandex_compute_instance" "platform"
zone = var.default_zone

3. 
![Скриншот](https://github.com/garrkiss/terraform_2/blob/main/img/task1/error%20task1/3.png)

Ответ:
Неправильный идентификатор платформы для resource "yandex_compute_instance" "platform"
Прописал platform_id = "standard-v3"

4. 
![Скриншот](https://github.com/garrkiss/terraform_2/blob/main/img/task1/error%20task1/4.png)

Ответ:
Неправильное значение ядра для resource "yandex_compute_instance" "platform"
Прописал core_fraction = 20

5. 
![Скриншот](https://github.com/garrkiss/terraform_2/blob/main/img/task1/error%20task1/5.png)

Ответ:
Неправильное значение числа ядер для resource "yandex_compute_instance" "platform"
Прописал cores = 2

Параметр preemptible = true
Описание: Указывает, что ВМ является прерываемой. Это значит, что облачный провайдер может остановить или удалить такую ВМ, если потребуется освободить ресурсы для других задач.

Параметр core_fraction = 5
Описание: Задает процент вычислительных ресурсов одного виртуального ядра, которые ВМ может использовать. Значение 5 означает, что ВМ будет использовать только 5% мощности одного ядра.

SSH и CURL
![Скриншот](https://github.com/garrkiss/terraform_2/blob/main/img/task1/task1-1.png)

### Задание 4

![Скриншот](https://github.com/garrkiss/terraform_2/blob/main/img/task4/task4.png)


По остальным заданиям [Ссылка на репозиторий](https://github.com/garrkiss/terra2)

