<img src="images/git_icon.svg" width="40" style="float: left; margin-right: 20px"/> 

# Работа с Git. Инструкция по эксплуатации.
Матчасть по Git на русском языке - https://git-scm.com/book/ru/v2

[Home](readme.md) » Удаление файла
________________________

## Удаление файла

`git rm text.txt` - удалить из отслеживаемых неиндексированный файл (файл будет удален из папки)

`git rm -f text.txt` - удалить из отслеживаемых индексированный файл (файл будет удален из папки)

`git rm -r log/` - удалить из отслеживаемых всё содержимое папки log/ (папка будет удалена)

`git rm ind*` - удалить из отслеживаемых все файлы с именем, начинающимся на «ind» в текущей папке (файлы будут удалены из папки)

`git rm --cached readme.txt` - удалить из отслеживаемых индексированный файл (файл останется на месте)



______________________________

## Содержание

1. [Создание нового репозитория](add_repo.md)
1. [Клонирование репозитория](clone_repo.md)
1. [Добавление файлов к отслеживанию, индексация отслеживаемых](add_file.md)
1. [Убирание файла или папки из отслеживаемых](rm_file.md)
1. [Отмена индексации](reset_index.md)
1. [Просмотр изменений](diff.md)
1. [Отмена изменений](checkout.md)
1. [Коммиты](commit.md)
1. [Отмена коммитов](revert.md)
1. [Переключиться на другой коммит](switch.md)
1. [Удаление файла](delete_file.md)
1. [Перемещение/переименование файлов](mv_file.md)
1. [История изменений](log.md)
1. [Ветки](branch.md)
1. [Удалённые репозитории](remote_repo.md)
1. [Примеры рабочих процессов](other.md)





