Привет, дорогой читатель! Данный файл включает в себя мой полный коспект по гиту за прошедшие уроки. Да, оформление может хромать, но с этим мы справимся потом. Главное, что полезность не падает от этого)

```
git version - выведет на экран версию гита
git config --global user.name "your name" - добавит в конфигурацию никнейм пользователя
git config --global user.email "your email" - добавит в конфигурацию почту пользователя
cat ~/.gitconfig - выведет на экран конфигурационный файл гита
git config --list --show-origin - выведет на экран все конфиги гита и их расположение в системе
git init - инициализирвоать репозиторий (чтобы удалить репозиторий с компа, нужно удалить скрытую папку .git)
git status - выводит на экран статус репозитория
git add . - подготовить к сохранению в репозиторий все файлы из текущей папки
git add <file name> - подготовить к сохранению в репозиторий файл <file name>
git add --all - подготовить к сохранению в репозиторий все файлы из текущей папки
git commit -m "<your comment>" - сделает коммит в репозиторий с комментарием <your comment>
```

💡 **Чем отличается запоминание от сохранения?**

Команда `git add` не сохраняет содержимое файлов в репозитории. Само сохранение, или фиксацию состояния файлов, называют **коммитом** (от англ. _commit_ — «совершать», «фиксировать»). «Сделать коммит» значит сохранить текущую версию файла.

Если провести аналогию, команду `git add` можно сравнить с добавлением товаров в корзину в интернет-магазине, а коммит — с оформлением и оплатой заказа.

### Ещё раз о разнице между `git add` и `git commit`

Сначала команда `git add` сообщает Git, какие именно файлы нужно сохранить и какую их версию. Затем с помощью команды `git commit` происходит само сохранение.

### Привязать удалённый репозиторий к локальному — `git remote add`

Откройте консоль, перейдите в каталог локального репозитория и введите команду `git remote add` (от англ. _remote_ — «удалённый» и _add_ — «добавить»).

```
$ cd ~/dev/first-project
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
```

`origin` (англ. «источник») — стандартный псевдоним, с помощью которого можно обращаться к главному удалённому репозиторию (обычно такой репозиторий один). Это значительно упрощает работу.

### Убедиться, что репозитории связаны, — `git remote -v`

Отлично: вы связали локальный репозиторий с удалённым. Осталось убедиться, что всё работает, с помощью следующей команды.

```
$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push) 
```

В выводе вы должны увидеть две строчки, аналогичные тем, что показаны выше.

Флаг `-v` — короткая форма флага `--verbose` (англ. «подробный»). Он позволяет показать больше информации в выводе.
### Отправить изменения на удалённый репозиторий — `git push`
В первый раз эту команду нужно вызвать с флагом `-u` и параметрами `origin` (имя удалённого репозитория) и `main` или `master` (название текущей ветки). Флаг `-u` свяжет локальную ветку с одноимённой удалённой. Как вы связывали локальный и удалённый репозитории в предыдущем уроке, так же и здесь нужно дополнительно связать ветки.

```
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте 
                          # заменить main на master. 
```
В дальнейшем при работе с удалённым репозиторием флаг `-u` можно опустить и писать просто `git push`.

# Файл README.md

Чтобы другие пользователи, а также потенциальные клиенты или работодатели могли понять, что представляет собой проект, его нужно описать. Такое описание принято указывать в файле `README.md` (от англ. _read_ — «прочитай» и _me_ — «меня»). В этом уроке вы научитесь оформлять такие файлы.

### Подробнее о том, зачем нужен **`README.md`**

Как правило, в `README.md` проекта можно найти следующую информацию:

1. Название проекта и его краткое описание: кем создан, для чего, какие решает задачи и какие закрывает проблемы.
2. Технологии, которые применяются в проекте. В чём его отличие от аналогичных.
3. Документация проекта — подробная инструкция о том, что представляет собой проект.
4. Планы проекта, если они есть.

Вот пример файла `README.md` для Git [на GitHub](https://github.com/git/git/blob/master/README.md).
