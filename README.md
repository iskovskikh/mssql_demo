# mssql в докере

Для запуска mssql сервера из docker-compose нужно создать файл `.env`(как пример `.env.example`), а затем выполнить:

```shell
docker-compose up -d
```

Посмотреть лог:
```shell
docker-compose logs -f
```

---

Никогда не сталкивался с Synology, но судя по мануалу, можно запустить контейнер и через gui:

[https://kb.synology.com/ru-ru/DSM/help/Docker/docker_container?version=6](https://kb.synology.com/ru-ru/DSM/help/Docker/docker_container?version=6)

Нужно будет: 
- обьявить env переменные `ACCEPT_EULA`, `MSSQL_SA_PASSWORD`, `MSSQL_PID`
- прокинуть порт `1134`
- примонтировать volume, где будет храниться информация из БД, чтобы не терять ее при перезапуске`<путь_на_хосте>:<путь_в_контейнере>`

Проверить работу можно через cli утилиту:

[https://hub.docker.com/r/microsoft/mssql-tools](https://hub.docker.com/r/microsoft/mssql-tools)

```shell

docker run -it mcr.microsoft.com/mssql-tools

# внутри контейнера:

sqlcmd -S 

```