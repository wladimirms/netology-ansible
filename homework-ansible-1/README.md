## Домашнее задание к блоку "Введение в Ansible"

# Подготовка к выполнению

1. Устанавливаю ansible версии 2.17 на macOS через brew install

<img width="1039" alt="Снимок экрана 2024-08-20 в 20 25 51" src="https://github.com/user-attachments/assets/d953510c-cab9-4937-8a56-382622e742e1">

2. Создаю публичный репозиторий

<img width="921" alt="Снимок экрана 2024-08-20 в 20 26 51" src="https://github.com/user-attachments/assets/b3fa4f84-2597-428e-9a2e-0bb336a7e49b">

3. Скачиваю и переношу playbook в свой репозиторий

<img width="726" alt="Снимок экрана 2024-08-20 в 20 30 04" src="https://github.com/user-attachments/assets/b07674b3-9c88-4866-9d65-0b3fcc30b3ae">
<img width="764" alt="Снимок экрана 2024-08-20 в 20 29 39" src="https://github.com/user-attachments/assets/60113652-0d50-46fa-a88c-a62799538bb1">

# Задание 1

1.Запускаю playbook на окружении из test.yml. Фиксирую значение:

<img width="929" alt="Снимок экрана 2024-08-20 в 20 39 24" src="https://github.com/user-attachments/assets/c5995178-a3e8-4376-b5bd-801225ba53df">

2.Нахожу файл с переменными и меняю его на all default fact:

<img width="942" alt="Снимок экрана 2024-08-20 в 20 43 09" src="https://github.com/user-attachments/assets/382f414a-d89f-4c22-9677-5c34d760d680">

3.Подготавливаю окружение в docker при помощи docker pull. Скачиваю образы с предустановленным python3 из репозитория pycontribs:

<img width="674" alt="Снимок экрана 2024-08-20 в 21 03 41" src="https://github.com/user-attachments/assets/122407cf-9ab0-43a7-98b5-49fc75f498b0">
<img width="654" alt="Снимок экрана 2024-08-20 в 21 03 55" src="https://github.com/user-attachments/assets/a5dc8851-68cb-47d7-bf28-c83a75eb45e2">

Создаю компоуз файл и поднимаю ВМ:

<img width="467" alt="Снимок экрана 2024-08-20 в 21 48 14" src="https://github.com/user-attachments/assets/daf34ea9-593c-4680-ac1c-ea4890d30666">
<img width="903" alt="Снимок экрана 2024-08-20 в 21 54 23" src="https://github.com/user-attachments/assets/5948d204-d16d-4eca-acd4-0275b3354459">

По итогу пришлось повысить версии python до 3.7/3.8 вручную на обе ВМ.

4. Провожу запуск playbook на окружении из prod.yml. Фиксирую полученные значения:

<img width="790" alt="Снимок экрана 2024-08-20 в 21 53 32" src="https://github.com/user-attachments/assets/3b47ec75-7f58-4531-abba-4eb635b845d9">

5. Добавляю факты в group_vars каждой из групп хостов так, чтобы для some_fact получились значения: для deb — deb default fact, для el — el default fact:

<img width="881" alt="Снимок экрана 2024-08-20 в 21 59 19" src="https://github.com/user-attachments/assets/01a31399-ea8e-4b6f-b92f-4287cb80fa4a">

6. Повторяю запуск playbook
<img width="941" alt="Снимок экрана 2024-08-20 в 21 59 56" src="https://github.com/user-attachments/assets/0287eb92-8b81-4f49-81ce-bb927b42fd05">

7. 


