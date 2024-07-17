# Руководство по работе с Git

### Весь перечень команд для консоли:

+ **echo ""** - выводит в консоль то, что было написано в кавычках
  + **echo "" >> file.txt** - добавляет строку, которая написана в ковычках в конец файла file.txt
  + **echo "" > file.txt** - удаляет всё содержимое файла file.txt и добавляет в него строку, которая написана в ковычках
+ **cd** - переместиться в папку
  + **cd ~** - переместиться в домашнюю директорию
  + **cd ..** - переместиться на уровень выше в родительскую папку
  + **cd /** - переместиться в корневую папку
+ **pwd** - вывести путь к папке, в которой вы сейчас находитесь
+ **ls** - отобразить файлы и папи в текущей дериктории
  + **ls -a** - отобразить все файлы и папки в текущей дериктории, включая скрытые
+ **touch** - создать файл
+ **mkdir** - создать папк
  + **mkdir -p** - создать целую структуру дериктории одной командой
+ **cp** - скопировать файлы
+ **mv** - переместить файлы
+ **cat** - вывести содержимое файла
+ **rm** - удалить файл
  + **rmdir** - удалить пустую папку
  + **rm -r** - удалить папку с файлами
  + **rm -rf .git** - разгитить папку
+ **log** - просмотреть историю коммитов
  + **--oneline** - сокращённо отобразить всех коммитов
+ **git add** - присвоить определённому файлу состояние *staged* 
  + **--all** -  присвоить всем файлом в git репозитории состояние *staged*
+ **git commit** - выполнить коммит
  + **-m** - присвоить коммиту сообщение
  + **--amend** - дополнить коммит забытым файлом
    + **--no-edit** - оставить сообщение коммита как было
    + **-m** - изменить сообщение коммита
+ **git config** - работа с файлом настройки
  + **--global** - указать электронную почту и имя через значени *user.name*, *user.email* 
  + **--list** -  вывести содержимое файла конфигурации Git
+ **git status** - отобразить состояние файлов
  + **--ignored** - отобразить состояние файлов, включая игнорируемые файлы
+ **git init** - инициализировать репозиторий
+ **ssh-keygen -t rsa -b 4096 -C "электронная почта"** - сгенерировать SSH ключ
  + **ssh -T** - проверить правильность ключа
+ **git remote add** - привязать удалённый репозиторий к локальному
  + **git remote -v** - убедиться, что репозитории связаны
+ **git push** - отправить изменения на удалённый репозиторий
  + **git push -u origin master** - связать локальную ветку с одноименной удалённой
+ **git restore --staged file** - присвоить определённому файлу с состояением *staged* состояение *untracked*
+ **git reset --hard commit hash** - откатить то, что было закоммичено, то есть вернуть состояение репозитория к более раннему
+ **git diff** - посмотреть изменения в файлах с состоянием modified
  + **"hash первого коммита" "hash второго коммита"** - выведет разницу между двумя коммитами
  + **--staged** - покажет изменения в staged файлах
+ **git clone** - склонировать репозиторий
+ **git branch** - посмотреть ветку проекта
---

### Подробное описание некоторых команд:

Для копирования файлов через терминал существует команда **cp** (*от англ. copy — «копировать»*). В простом виде **cp** принимает два параметра: что копируем и куда копируем.
``` 
$ cp index.html src/
# скопировали index.html в папку src
``` 

Но можно указать сразу несколько файлов.
$ cp что_копируем что_копируем что_копируем куда_копируем

```
$ cp index.html style.css script.js src/
# скопировали три файла (index.html, style.css и script.js) в папку src
```

Для перемещения файлов через терминал существует команда **mv**. Синтаксис команды **mv** аналогичен синтаксису **cp**. После имени команды указывают список файлов и папок, которые нужно переместить, а затем — папку, в которую нужно выполнить перемещение.

Команда **git status** всегда подскажет, что происходит с файлом: например, он добавлен в список «на коммит» или ещё вообще не отслеживается, или изменён. **git status** показывает явно следующие состояния файлов: *untracked*, *staged* и *modified*. **git status** подсказывает, какие команды можно выполнить, чтобы поменять состояние файла.

Команда **git commit** сохраняет изменения всех файлов, которые находятся в состоянии *staged*. **git commit -m " "** добавляет описание коммита, которое указано в кавычках. **git commit --amend** вносит правки в последний коммит. **git commit --amend -m " "** изменяет сообщение последнего коммита на новое. **git commit --amend --no-edit** дополняет коммит новыми файлами.