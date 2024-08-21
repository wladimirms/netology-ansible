## Домашнее задание к блоку "Работа с Playbook"

# Подготовка к выполнению

1. Изучаю документацию по vector и clickhouse
2. Использую новую директорию в предыдущем репозитории netology-ansible. Подготавливаю окружение - создаю новый компоуз-файл:

<img width="383" alt="Снимок экрана 2024-08-21 в 22 10 45" src="https://github.com/user-attachments/assets/4893ceaf-6b46-4a6f-a3b4-c369819a045f">

3. Поднимаю окружение в docker и устанавливаю python3.8

<img width="981" alt="Снимок экрана 2024-08-21 в 22 11 02" src="https://github.com/user-attachments/assets/5415305e-cdde-466f-831a-ac904d9d48b9">

# Основная часть

1. Подготавливаю свой inventory-файл prod.yml.

<img width="354" alt="Снимок экрана 2024-08-21 в 22 12 16" src="https://github.com/user-attachments/assets/52fba09c-94f3-45ad-ba27-843cf912ba43">

2/3/4. Дописываю playbook: добавляю play c task с использованием модулей ansible.builtin.get_url, ansible.builtin.template, ansible.builtin.anarchive, ansible.builtin.file:

5. 
