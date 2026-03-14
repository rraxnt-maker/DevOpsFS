---
tags:
  - DevOps
---
[[Docker]]

### Dockerfile 
Это инструкция по сборке образа Простой текстовый файл, где каждая строчка - комманда для docker 

## Все инструкции 

1)`FROM`- Базовый образ
обязательная команда, То с чего начинаем сборку  

```
FROM python:3.9-slim
FROM alpine:latest
FROM ubuntu:20.04
```

2)`WORKDIR` - Рабочая папка 
Создаёт и переходит в указанную директорию.
```
WORKDIR /app
# создаём и сразу попадаем в /app
```

3)`COPY` и `ADD` - Копируем файлы 
`COPY` - просто копирует файлы из контекста сборки в образ 
`ADD` - умеет распаковывать архивы и скачивать по URL

```
COPY app.py .                    # копируем app.py в текущую папку (/app)
COPY --chown=user:group configs/ ./configs/  # с правами

ADD archive.tar.gz /temp/        # распакует архив автоматом
ADD https://example.com/file /   # скачает (лучше использовать curl)
```

4)`RUN` - выполнить команду при сборке 
Запускается во время создания образа нужен для установки пакетов, создания папок и тд

```
RUN apt-get update && apt-get install -y curl
RUN pip install flask requests
RUN mkdir -p /app/data
RUN chmod +x /app/script.sh
```

5)`ENV` - Переменные окружения 

```
ENV APP_HOME=/app
ENV PORT=8080
ENV DB_HOST=localhost
```

6)`ARG` - Переменные сборки 

```
ARG VERSION=latest
RUN echo "Собираем версию ${VERSION}"
```

7)`EXPOSE` - Открыть порт

```
EXPOSE 5000
EXPOSE 80 443
```

8)`CMD` и `ENTRYPOINT` = 
`ENTRYPOINT` - входная точка комманда выполняющаяся при старте 
`CDM` - 

