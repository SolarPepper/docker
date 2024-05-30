---
layout: home
navname: Home

## HUB-DOCKER

### Прокси-сервер для Docker

Hub-Docker предоставляет удобный прокси-сервер для доступа к реестру Docker, помогая обходить региональные ограничения в России и других странах.

При попытке загрузки образа может возникнуть ошибка: "Error response from daemon: pull access denied for nginx, repository does not exist or may require 'docker login': denied: 403 Forbidden." Это связано с ограничениями США, блокирующими IP-адреса из определенных стран и регионов. Использование hub-docker помогает обойти эти ограничения.

### Инструкции по использованию

#### 1. Настройка через конфигурацию Docker

Отредактируйте файл конфигурации Docker, чтобы включить зеркало hub-docker:

- **Операционная система и путь к файлу конфигурации:**
  - Linux, стандартная установка: `/etc/docker/daemon.json`
  - Linux, rootless mode: `~/.config/docker/daemon.json`
  - Windows: `C:\ProgramData\docker\config\daemon.json`

```json
{
  "registry-mirrors": ["https://hub-docker.ru"]
}
```

Теперь при попытке загрузки образа Docker будет сначала использовать прокси.

#### 2. Прямая команда

Вы также можете извлекать образы напрямую, используя следующую команду:

```sh
docker pull hub-docker.ru/library/alpine:latest
```

### Другие доступные прокси

| Адрес                   | Описание |
|-------------------------|----------|
| https://mirror.gcr.io   | Google   |
| https://daocloud.io     | Китай    |
| https://c.163.com       | Китай    |
| https://registry.docker-cn.com | Китай |

### Почему Docker Hub недоступен в России

Docker Hub ушел из России из-за санкций США. Сайт сервиса больше недоступен с российских IP-адресов, при открытии сайта появляется надпись:

> «403 Forbidden Since Docker is a US company, we must comply with US export control regulations. In an effort to comply with these, we now block all IP addresses that are located in Cuba, Iran, North Korea, Republic of Crimea, Sudan, and Syria. If you are not in one of these cities, countries, or regions and are blocked».

Docker — сервис, позволяющий упаковать в контейнер приложение со всем окружением и зависимостями, а затем переместить и запустить его вне зависимости от того, в каком окружении будет работать приложение.

© 2024 hub-docker. Все права защищены.
