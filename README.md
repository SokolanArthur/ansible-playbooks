# Infrastructure as Code: Server Provisioning

This repository contains Ansible playbooks for automated infrastructure configuration and project deployment.

## Repository Structure

- `inventory.ini` — Configuration file containing target server IP addresses and connection parameters.
- `bootstrap.yml` — Primary server initialization playbook. Transforms a bare VDS into a secure, ready-to-use machine (SSH configuration, user creation, installation of basic utilities).
- `deploy.yml` — Project deployment playbook. Handles dependency installation (e.g., Docker) and container/application startup.

## Quick Start

**1. Configure the inventory** 
Edit the `inventory` file, specifying your server's actual IP address and connection user.

**2. Run the initial setup (Bootstrap)**
This is executed once on a new server to prepare the environment:

`ansible-playbook -i inventory bootstrap.yml`

**3. Deploy the project**
Run this to roll out the infrastructure or apply new changes:

`ansible-playbook -i inventory deploy.yml`

---

Этот репозиторий содержит Ansible-плейбуки для автоматизированной настройки инфраструктуры и деплоя проектов.

##  Структура репозитория

- `inventory` — конфигурационный файл, содержащий IP-адреса целевых серверов и параметры подключения.
- `bootstrap.yml` — плейбук первичной инициализации сервера. Превращает «голую» VDS в безопасную и готовую к работе машину (настройка SSH, создание пользователей, установка базовых утилит).
- `deploy.yml` — плейбук развертывания проекта. Отвечает за установку зависимостей (например, Docker) и запуск контейнеров/приложений.

##  Быстрый старт

**1. Настройка инвентаря**
Отредактируйте файлы `inventory.ini`, `bootstrap.yml`, `deploy.yml` указав актуальные данные вашего сервера и пользователей.

**2. Первичная настройка (Bootstrap)**
Выполняется один раз на новом сервере для подготовки окружения:

`ansible-playbook -i inventory bootstrap.yml`

**3. Деплой проекта (Deploy)**
Запускается для раскатки инфраструктуры или выкатки новых изменений:

`ansible-playbook -i inventory deploy.yml`
