## Домашнее задание к блоку "Работа с Playbook"

# Подготовка к выполнению

1. Изучаю документацию по vector и clickhouse
2. Использую новую директорию в предыдущем репозитории netology-ansible. Подготавливаю окружение - создаю новый компоуз-файл:

<img width="363" alt="Снимок экрана 2024-08-24 в 18 14 53" src="https://github.com/user-attachments/assets/3caaa2b4-20dd-4c6e-bb9d-97c3312229be">

3. Поднимаю окружение в docker из образов pycontribs fedora с предустановленным python:

<img width="797" alt="Снимок экрана 2024-08-24 в 18 15 40" src="https://github.com/user-attachments/assets/40374391-a247-46a9-9dee-0912e2dc7f31">

# Основная часть

1. Подготавливаю свой inventory-файл prod.yml.

<img width="322" alt="Снимок экрана 2024-08-24 в 18 17 09" src="https://github.com/user-attachments/assets/4bbb4661-ac42-4170-997f-a1294065e00d">

2/3/4. Дописываю playbook: добавляю play c task с использованием модулей ansible.builtin.get_url, ansible.builtin.template, ansible.builtin.anarchive, ansible.builtin.file, ansible.builtin.copy:

Произвожу необходимые изменения для play с clickhouse:
<img width="951" alt="Снимок экрана 2024-08-24 в 18 18 44" src="https://github.com/user-attachments/assets/47dcaf7c-2036-4784-b96d-cc23792703df">

Создаю play для vector:

<img width="676" alt="Снимок экрана 2024-08-24 в 18 20 01" src="https://github.com/user-attachments/assets/78a46585-bbce-4acb-bd6b-a6e8f94b8186">

Создаю необходимые group_vars и services:
<img width="891" alt="Снимок экрана 2024-08-24 в 18 21 33" src="https://github.com/user-attachments/assets/17f2c93a-d3ea-4108-93a4-79e897b293f5">
<img width="896" alt="Снимок экрана 2024-08-24 в 18 22 19" src="https://github.com/user-attachments/assets/c8550875-6abb-476f-82a2-f8a150f81244">

5. Запускаю ansible-lint site.yml и исправляю ошибки:
<img width="737" alt="Снимок экрана 2024-08-24 в 15 55 31" src="https://github.com/user-attachments/assets/eca9880b-b1dd-400c-9c84-8fb00d0f6274">

6. Запускаю playbook с флагом --check:
<img width="813" alt="Снимок экрана 2024-08-24 в 18 28 05" src="https://github.com/user-attachments/assets/249163e0-4db0-4b5e-abb6-dc4a28992760">

7. Запускаю playbook с флагом --diff:
<img width="817" alt="Снимок экрана 2024-08-24 в 18 27 36" src="https://github.com/user-attachments/assets/1d67bfc5-de70-4151-ba91-1f7a25cde5d5">

Ошибка возникает в самом ansible из-за проблем с совместимостью и багов docker desktop с процессорами M1. Ранее неоднократно встречался с подобной проблемой. В качестве решения требуется переход на ОС Linux с процессорной архитектурой x86-64.

9. Подготовливаю README.md-файл по своему playbook. Далее вставил документацию:
-----

# netology-ansible/clickhouse-vector-app
## Инфраструктура
* Сервер clickhouse-01 для сбора логов;
  > https://clickhouse.com/docs/ru
* Сервер vector-01 для обработки логов.
  > https://vector.dev/docs/setup/installation/

## Playbook
Playbook производит установку и приложений на серверах. По умолчанию развертывание приложений предусмотрено для rpm-based образов.
Рекомендуется установка на fedora:latest, pycontribs/fedora:latest
  > https://hub.docker.com/r/pycontribs/fedora <br>
  > https://hub.docker.com/_/fedora <br>

В playbook используются следующие модули:
 * ansible.builtin.get_url,
 * ansible.builtin.template,
 * ansible.builtin.anarchive,
 * ansible.builtin.file
 * ansible.builtin.copy
  
### Clickhouse
* установка clickhouse
* создание базы данных и таблицы в ней

### Vector
* установка vector
* изменение конфигов приложения
  
### Variables
В каталоге group_vars задаются следующие переменные.

|vars|value|
|-|--------|
|clickhouse_version|версия clickhouse|
|vector_version|версия vector|
|vector_config|директория конфига vector|
|vector_service_config|директория systemd юнита|

## Install Clickhouse
1. Скачивание rpm-пакетов
2. Установка Clickhouse
3. Создание базы данных logs.

Через group_vars можно задать следующие параметры:
* clickhouse_version - версия clickhouse

## Install Vector

1. Скачивание rpm-пакетов
2. Установка Clickhouse
3. Создание базы данных logs.

Через group_vars можно задать следующие параметры:
* vector_version - версия vector
* vector_config - директория конфига vector
* vector_service_config - директория systemd юнита

## Установка и развертывание
* Для развертывания серверов использовать следующую команду:
  ```
  docker-compose up -d
  ```
* Для установки приложений:
  ```
  ansible-playbook inventory/prod.yml site2.yml
  ```
* Для проверки конфигурации:
  ```
  ansible-playbook inventory/prod.yml site2.yml --check
  ```
  ```
  ansible-playbook inventory/prod.yml site2.yml --diff
  ```
-----
10. Готовый README.md размещаю в личном репозитории github.

