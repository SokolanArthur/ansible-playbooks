# Infrastructure as Code: Server Provisioning & Deployment

This repository contains Ansible playbooks for automated infrastructure provisioning (VDS/VPS) and project deployment using Docker Compose. 

The repository is designed with a security-first approach: real credentials and IP addresses are decoupled from the code and are not stored publicly.

## 📁 Repository Structure

* `inventory.example.ini` — Inventory file template. Contains server groups and connection parameters.
* `secrets.example.yml` — Secret variables template (passwords, usernames, SSH keys).
* `bootstrap/bootstrap.yml` — Playbook for initial fresh server provisioning (user creation, SSH hardening, basic dependencies installation).
* `web-crm/deploy.yml` — Project deployment playbook (installs Git, Docker, pulls the repository, and starts containers).

## 🚀 Quick Start

### Step 1. Configuration Setup (Security)
Before running the playbooks, you need to create local files with your actual data based on the provided templates.

1. Create a copy of `inventory.example.ini`, rename it to **`inventory.ini`**, and fill in your server's actual IP address.
2. Create a copy of `secrets.example.yml`, rename it to **`secrets.yml`**, and fill in your real passwords (do not change the variable keys).

*(Note: `inventory.ini` and `secrets.yml` should already be included in your `.gitignore` to prevent accidental data leaks during commits).*

### Step 2. Server Bootstrapping
This step is executed once on a fresh server to prepare a secure environment:

`ansible-playbook -i inventory.ini bootstrap/bootstrap.yml`

### Step 3. Project Deployment
Command to set up the Docker environment and spin up containers (can be run multiple times to apply configuration updates):

`ansible-playbook -i inventory.ini web-crm/deploy.yml`

---

Этот репозиторий содержит Ansible-плейбуки для автоматизированной настройки инфраструктуры (VDS/VPS) и деплоя проектов с использованием Docker Compose. 

Архитектура репозитория построена с упором на безопасность: реальные пароли и IP-адреса вынесены за пределы кода и не хранятся в публичном доступе.

## 📁 Структура репозитория

* `inventory.example.ini` — шаблон файла инвентаризации. Содержит группы серверов и параметры подключения.
* `secrets.example.yml` — шаблон файла с секретными переменными (пароли, имена пользователей, SSH-ключи).
* `bootstrap/bootstrap.yml` — плейбук для первичной настройки «голого» сервера (создание пользователя, настройка SSH, установка базовых зависимостей).
* `web-crm/deploy.yml` — плейбук для развертывания проекта (установка Git, Docker, загрузка кода и запуск контейнеров).

## 🚀 Быстрый старт (Quick Start)

### Шаг 1. Подготовка конфигурации (Безопасность)
Перед запуском скриптов вам необходимо создать локальные файлы с вашими реальными данными на основе предоставленных шаблонов. 

1. Создайте копию файла `inventory.example.ini`, назовите её **`inventory.ini`**, впишите туда IP-адрес вашего сервера и имя пользователя.
2. Создайте копию файла `secrets.example.yml`, назовите её **`secrets.yml`** и заполните её своими реальными паролями (названия переменных менять нельзя).

*(Примечание: файлы `inventory.ini` и `secrets.yml` уже должны быть добавлены в ваш `.gitignore`, чтобы предотвратить случайную утечку данных при коммите).*

### Шаг 2. Базовая настройка сервера (Bootstrap)
Этот шаг выполняется один раз на новом сервере, чтобы подготовить безопасное окружение:

`ansible-playbook -i inventory.ini bootstrap/bootstrap.yml`

### Шаг 3. Деплой проекта (Deploy)
Команда для установки Docker-окружения и запуска контейнеров (можно запускать повторно для обновления конфигурации):

`ansible-playbook -i inventory.ini web-crm/deploy.yml`
