# Домашнее задание к занятию "`Основы Terraform. Yandex Cloud`" - `Бакулев Евгений`

### Задание 1

Скриншот ЛК Yandex Cloud

![Скриншот](https://github.com/garrkiss/terraform_1/blob/main/img/terraform_validate.png)

### Ошибки

1. 

![Скриншот](1.png)

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

![Скриншот](3.png)

Ответ:
Неправильный идентификатор платформы для resource "yandex_compute_instance" "platform"
Прописал platform_id = "standard-v3"

4. 
![Скриншот](4.png)

Ответ:
Неправильное значение ядра для resource "yandex_compute_instance" "platform"
Прописал core_fraction = 20

5. 
![Скриншот](5.png)

Ответ:
Неправильное значение числа ядер для resource "yandex_compute_instance" "platform"
cores = 2


### Исправленый код
```
resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = true
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "example_${random_password.random_string.result}"

  ports {
    internal = 80
    external = 9090
  }
}

```

![Dockeps](https://github.com/garrkiss/terraform_1/blob/main/img/dockerps.png)

![Dockeps](https://github.com/garrkiss/terraform_1/blob/main/img/dockerps_hello.png)

Опасность использования ключа -auto-approve:
Ключ -auto-approve в Terraform используется для того, чтобы пропустить шаг подтверждения перед применением изменений. Это может быть полезно в автоматизированных сценариях, где нужно избежать вмешательства пользователя, например, в CI/CD pipeline. Однако есть несколько рисков, связанных с его использованием:

Отсутствие проверки изменений: При использовании -auto-approve Terraform применяет все изменения без запроса подтверждения, что может привести к неожиданным последствиям, если изменения были неверными или несанкционированными.
Невозможность отката: Если что-то пошло не так, и были внесены изменения, которые повлияли на инфраструктуру или данные, откатить их будет сложнее, поскольку не было возможности вручную проверить план изменений.
Опасность при ошибках конфигурации: Если конфигурация содержит ошибку, которая может привести к сбоям (например, удаление ресурсов или создание новых с ошибками), Terraform автоматически применит эти изменения, что может привести к недоступности сервисов или потере данных.
Таким образом, ключ -auto-approve может быть полезен в автоматизированных процессах, но для ручных проверок лучше избегать его использования, чтобы удостовериться, что изменения не приведут к непредсказуемым последствиям.

![tfstate](https://github.com/garrkiss/terraform_1/blob/main/img/terraform-tfstate.png)


Keep_locally - (Необязательно, логическое значение) Если true, то образ Docker не будет удален при операции уничтожения. Если это ложь, он удалит изображение из локального хранилища докера при операции уничтожения.



