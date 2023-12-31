<img src="images/git_icon.svg" width="40" style="float: left; margin-right: 20px"/> 

# Работа с Git. Инструкция по эксплуатации.
Матчасть по Git на русском языке - https://git-scm.com/book/ru/v2

[Home](readme.md) » Рабочие процессы
________________________

## Рабочие процессы

### Создание нового репозитория, первый коммит, привязка удалённого репозитория с gthub.com, отправка изменений в удалённый репозиторий.

`git init` - инициируем гит в этой папке

`touch readme.md` - создаем файл readme.md

`git add readme.md` - делаем этот файл отслеживаемым

`git commit -m "Первый коммит"` - создаем первый коммит с вменяемым названием

`git remote add origin git@github.com:sakhnov/sf-m3.git` - добавляем предварительно созданный пустой удаленный репозиторий

`git push origin master` - отправляем данные из локального репозитория в удаленный (в ветку master)

## Обычный рабочий процесс

Создание нового репозитория на github.com, клонирование к себе, работа, периодическая «синхронизация с github.com».

### указана последовательность действий:

- создаём на github.com репозиторий, копируем его URL клонирования (SSH)
- в консоли попадаем в свою папку для всех проектов

`git clone git@github.com:sakhnov/sf-m3.git module3` - клонируем удалённый репозиторий к себе на компьютер (если не указать "module3", будет создана папка, совпадающая по имени с названием репозитория)

`cd module3` - переходим в папку проекта

### редактируем файлы, добавляем файлы и/или папки

`git add .` - делаем все новые файлы в этой папке отслеживаемыми и готовыми к коммиту

`git commit -m "НАЗВАНИЕ_КОММИТА"` - создаем коммит с вменяемым названием

`git push origin master` - отправляем данные из локального репозитория в удаленный (в ветку master)

- снова вносим какие-то изменения (если удаляем файлы — см. про [удаление файлов](delete_file.md))
- возвращаемся к шагу с git add . и проходим цикл заново

Не обязательно после каждого коммита отправлять изменения в удаленный репозиторий, можно сделать это один раз в конце работы.

## Внесение изменений в коммит
### указана последовательность действий:
`subl inc/header.html` - редактируем и сохраняем разметку «шапки», так же редактирование файла можно делать в любом текстовом редакторе

`git add inc/header.html` - индексируем измененный файл

`git commit -m "Убрал телефон из шапки"` - делаем коммит

### Если коммит пока не был отправлен в удалённый репозиторий, но вспомнили, что нужно было еще что-то сделать в этом коммите
`subl inc/header.html` - вносим изменения

`git add inc/header.html` - индексируем измененный файл (можно git add .)

`git commit —amend -m "«Шапка»: выполнена задача №34"` - заново делаем коммит

## Работа с ветками
### Есть master (публичная версия сайта), хотим масштабно что-то поменять (переверстать «шапку»), но по ходу работ возникает необходимость подправить критичный баг (неправильно указан контакт в «подвале»).

#### указана последовательность действий:

`git checkout -b new_page_header` - создадим новую ветку для задачи изменения «шапки» и перейдём в неё

`subl inc/header.html` - редактируем и сохраняем разметку «шапки»

`git commit -a -m "Новая шапка: смена логотипа"` - делаем первый коммит (работа еще не завершена)

#### тут выясняется, что есть баг с контактом в «подвале»

`git checkout master` - возвращаемся к ветке master

`git checkout -b footer_hotfix` - создаём ветку (основанную на master) для решения проблемы

`subl inc/footer.html` - устраняем баг и сохраняем разметку «подвала»

`git commit -a -m "Исправление контакта в подвале"` - делаем коммит

`git checkout master` - переключаемся в ветку master

`git merge footer_hotfix` - вливаем в master изменения из ветки footer_hotfix

`git branch -d footer_hotfix` - удаляем ветку footer_hotfix

`git checkout new_page_header` - переключаемся в ветку new_page_header для продолжения работ над «шапкой»

`subl inc/header.html` - редактируем и сохраняем разметку «шапки»

`git commit -a -m "Новая шапка: смена навигации"` - делаем коммит (работа над «шапкой» завершена)

`git checkout master` - переключаемся в ветку master

`git merge new_page_header` - вливаем в master изменения из ветки new_page_header

`git branch -d new_page_header` - удаляем ветку new_page_header

## Работа с ветками, конфликт слияния

### Есть master (публичная версия сайта), в двух параллельных ветках (branch_1 и branch_2) было отредактировано одно и то же место одного и того же файла, первую ветку (branch_1) влили в master, попытка влить вторую вызывает конфликт.

#### указана последовательность действий, как это происходит:

`git checkout master` - переключаемся на ветку master

`git checkout -b branch_1` - создаём ветку branch_1, основанную на ветке master

`subl .` - редактируем и сохраняем файлы

`git commit -a -m "Правка 1"` - коммитим (теперь имеем 1 коммит в ветке branch_1)

`git checkout master` - возвращаемся к ветке master

`git checkout -b branch_2` - создаём ветку branch_2, основанную на ветке master

`subl .` - редактируем и сохраняем файлы

`git commit -a -m "Правка 2"` - коммитим (теперь имеем 1 коммит в ветке branch_2)

`git checkout master` - возвращаемся к ветке master

`git merge branch_1` - вливаем изменения из ветки branch_1 в текущую ветку (master), удача (автослияние)

`git merge branch_2` - вливаем изменения из ветки branch_2 в текущую ветку (master), КОНФЛИКТ автослияния

### Сообщение о конфликте: Automatic merge failed; fix conflicts and then commit the result.

`subl .` - выбираем в конфликтных файлах те участки, которые нужно оставить, сохраняем

`git commit -a -m "Устранение конфликта"` - коммитим результат устранения конфликта



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


