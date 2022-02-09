# m6-Jenkins-Task-01


### Lint to repository

- Repository with Pet clinic CI/CD project: https://git.epam.com/bohdan_mukovozov/ci_cdtask
- IP addres where the application starts after the deployment http://15.188.246.227:<port witch u choise in deployment build>/

### Task Desription

1. Jenkins server address: http://15.236.202.220:8080/
``` 
Credential to Jenkins server
login: Reviewer
password: Reviewer
```

2. Part 1:
```
Поднять и настроить Jenkins сервер.
1. Настроить агенты
1.1 статический (windows vs linux)
1.2 динамический (например, https://www.jenkins.io/doc/book/pipeline/docker/ )
2. Поместить sensitive данные в credentials (github/gitlab connection details, etc)
3. Настроить права доступа. Создать три группы (dev, qa, devops и предоставить различные права доступа)

```

3. Part 2:
```
Создать мультибранч пайплайн, который бы:
1. Тригерился на изменение в любой ветке гит репозитория, для ветки создается отдельный пайплайн
2. Пайплайн состоит из шагов
a. Клонировать репозиторий с feature ветки
b. Опционально: проверить коммит сообщение на соответствие best practice (длина сообщения, вначале код джира тикета)
c. Линтинг Dockerfiles
3. В случае фейла пайплайна - заблокировать возможность мержа feature ветки в основную ветку.
```

4. Part 3:
```
Создать CI пайплайн:
1. Смотрит на основную ветку репозитория (main/master/whatever)
2. Тригерится на мерж в основную ветку
3. Клонирует репозиторий
4. Запускает статический анализ кода, Bugs, Vulnerabilities, Security Hotspots, Code Smells доступны на SonarQube сервере
5. Билдит Docker образ
6. Тегируем 2 раза образ (latest и версия билда)
7. Пушим образ в Docker Hub
```

5. Part 4:
```
Создать CD пайплайн:

Параметры при запуске:
Имя энва (dev/qa)
Номер версии (т.е. тег образа, версия или latest). Будет плюсом, если этот список будет динамически подтягиваться из Dockerhub
Деплой образа на выбранный энвайронмент
Стейдж с healthcheck задеплоенногоо энва (curl endpoint or smth else)
```