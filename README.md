# Мониторинг и настройка Linux-сервера

Проект по системному администрированию на Ubuntu. Здесь собраны скрипт мониторинга системы и конфигурации Docker, Nginx, systemd, RAID1 и LVM.

## Что настроено

- **Bash**  сбор информации о нагрузке, памяти и дисковом пространстве.
- **Docker**  запуск скрипта и тестового HTTP-сервера.
- **Nginx**  reverse proxy и перенаправление HTTP на HTTPS.
- **TLS**  HTTPS с самоподписанным сертификатом.
- **systemd**  управление контейнером `my-app`.
- **RAID1 и LVM**  настройка и монтирование хранилища.

## Структура проекта

- `script.sh`  скрипт мониторинга.
- `sample_output.txt`  пример вывода.
- `docker/`  Dockerfile и скрипт для контейнера.
- `nginx/my-app.conf`  конфигурация Nginx.
- `systemd/my-app.service`  systemd-сервис.

## Полезные команды

Скрипт мониторинга:

```bash
./script.sh 2 2
```

Сборка Docker-образа из корня репозитория:

```bash
sudo docker build -t sysadmin-monitor -f docker/Dockerfile docker
```

Проверка Nginx и HTTPS:

```bash
sudo nginx -t
curl -kI https://localhost
```

Проверка сервиса и логов:

```bash
systemctl status my-app
sudo journalctl -u my-app -n 30 --no-pager
```

Проверка RAID1 и LVM:

```bash
cat /proc/mdstat
sudo lvs
findmnt /mnt/raid
findmnt /mnt/logs
```

## Результат

Проверены запуск контейнера, работа systemd, конфигурация Nginx и HTTPS-ответ `200 OK`. RAID1 и LVM созданы и смонтированы. Диски для хранилища представлены loop-устройствами.

[Репозиторий на GitHub](https://github.com/paraumir/my-sysadmin-scripts)
