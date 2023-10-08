<img src="images/git_icon.svg" width="40" style="float: left; margin-right: 20px"/> 

# Работа с Git. Инструкция по эксплуатации.
Матчасть по Git на русском языке - https://git-scm.com/book/ru/v2

[Home](readme.md) » Ветки
________________________

## Ветки

`git branch` - показать список веток

`git branch -v` - показать список веток и последний коммит в каждой

`git branch new_branch` - создать новую ветку с указанным именем

`git checkout new_branch` - перейти в указанную ветку

`git checkout -b new_branch` - создать новую ветку с указанным именем и перейти в неё

`git merge hotfix` - влить в ветку, в которой находимся, данные из ветки hotfix

`git branch -d hotfix` - удалить ветку hotfix (если её изменения уже влиты в главную ветку)

`git branch --merged` - показать ветки, уже слитые с активной (их можно удалять)

`git branch --no-merged` - показать ветки, не слитые с активной

`git branch -a` - показать все имеющиеся ветки (в т.ч. на удаленных репозиториях)

`git branch -m old_branch_name new_branch_name` - переименовать локально ветку old_branch_name в new_branch_name

`git branch -m new_branch_name` - переименовать локально ТЕКУЩУЮ ветку в new_branch_name

`git push origin :old_branch_name new_branch_name` - применить переименование в удаленном репозитории

`git branch --unset-upstream` - завершить процесс переименования




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




