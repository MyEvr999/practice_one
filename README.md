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

Теперь вы знаете, что такое хеш коммита и для чего он нужен. Подведём итоги:

- Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — хеш.
- Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.
- Все хеши, а также таблицу соответствий `хеш → информация о коммите` Git хранит в папке `.git`.

Получить сокращённый лог можно с помощью команды `git log` с флагом `--oneline` (англ. «одной строкой»). В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.

- Можно вызвать не только полный лог, но и сокращённый — это делается командой `git log --oneline`.
- В сокращённом логе выводятся сокращённые хеши — их можно использовать точно так же, как и полные.

### Файл `HEAD`

Файл `HEAD` (англ. «голова», «головной») — один из служебных файлов папки `.git`. Он указывает на коммит, который сделан последним (то есть на самый новый).

В этом можно убедиться с помощью терминала. Перейдите в папку `.git` командой `cd`. Посмотрите содержимое файла `HEAD` командой `cat`.

```
$ pwd # посмотрели, где мы
/Users/user/dev/first-project

$ cd .git/
$ ls # посмотрели, какие есть файлы
COMMIT_EDITMSG  ORIG_HEAD  description  index  logs/     refs/
HEAD            config     hooks/       info/  objects/

$ cat HEAD # команда cat показывает содержимое файла
ref: refs/heads/master # в файле вот такая ссылка 
```

Внутри `HEAD` — ссылка на служебный файл: `refs/heads/master` (или `refs/heads/main` в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита.

```
$ cat refs/heads/master # взяли ссылку из файла HEAD
# внутри хеш
e007f5035f113f9abca78fe2149c593959da5eb7

$ git log 
# сверяем с хешем последнего коммита
commit e007f5035f113f9abca78fe2149c593959da5eb7
Author: John Doe <johndoe@example.com>
Date:   Tue Mar 28 00:26:53 2023 +0300

    Добавить амбиций в список дел

... # другие коммиты 
```

Когда вы делаете коммит, Git обновляет `refs/heads/master` — записывает в него хеш последнего коммита. Получается, что `HEAD` тоже обновляется, так как ссылается на `refs/heads/master`.

При работе с Git указатель `HEAD` используется довольно часто. Мы уже упоминали, что многие команды Git принимают в качестве параметра хеш коммита. Если нужно передать последний коммит, то вместо его хеша можно просто написать слово `HEAD` — Git поймёт, что вы имели в виду последний коммит.

💡 **Staging area, index и cache**

Staging area также называют **index** (англ. «каталог») или **cache** (англ. «кеш»), а состояние файла `staged` иногда называют `indexed` или `cached`.

Все три варианта могут встречаться в документации и в качестве флагов команд Git. А также в интернете — например, в вопросах и ответах [на сайте Stack Overflow](https://stackoverflow.com/).

💡 Для файлов в состояниях `staged` и `modified` обычно не указывают, что они также `tracked`, потому что это состояние подразумевается.

Важное:
- Статусом `untracked` помечается файл, о существовании которого Git знает, но не следит за изменениями в нём. Этот статус — противоположность `tracked`, в который попадают все файлы, отслеживаемые Git.
- Файл переходит в статус `staged` после выполнения `git add`.
- Статус `modified` означает, что файл был изменён.
- Большинство файлов в проектах «шагает» по следующему циклу: «изменён» → «добавлен в список на коммит» → «закоммичен» → «изменён» → и так далее.

В выводе команды `git log --oneline` умещается максимум 72 первых символа сообщения, поэтому многие правила включают пункт: «Сообщение не должно быть длиннее 72 символов».

Есть общие рекомендации по тому, как правильно составить сообщение к коммиту. Оно должно быть:
- относительно коротким, чтобы его было легко прочитать;
- информативным.

Чтобы упростить работу, команды или даже целые компании часто договариваются об определённом стиле (то есть о правилах) оформления сообщений коммитов.

Например, правила могут быть такие:

- длина сообщения от 30 до 72 символов;
- первое слово — глагол в инфинитиве («исправить», «дополнить», «добавить» и другие);
- и так далее.

Стандарт **Conventional Commits** (англ. «соглашение о коммитах») отличается качественной документацией и подробной проработкой. Он подходит для репозиториев с исходным кодом программ. Использовать его для других типов проектов (например, для перевода книги) было бы неудобно.

Conventional Commits предлагает такой формат коммита: `<type>: <сообщение>`. Первая часть `type` — это тип изменений. Таких типов достаточно много. Вот два примера:

- `feat` (сокращение от англ. _feature_) — для новой функциональности;
- `fix` (от англ. «исправить», «устранить») — для исправленных ошибок.

Более подробный список можно увидеть [на сайте с описанием этого стиля](https://www.conventionalcommits.org/ru/v1.0.0-beta.4/#%D1%81%D0%BF%D0%B5%D1%86%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%86%D0%B8%D1%8F).

Например, сообщение может быть таким.

```
git commit -m "feat: добавить подсчёт суммы заказов за неделю" 
```
### GitHub-стиль

GitHub можно использовать не только для хранения файлов проекта, но и для ведения списка **задач** (англ. _issue_) этого проекта. Если коммит «закрывает» или «решает» какую-то задачу, то в его сообщении удобно указывать ссылку на неё. Для этого в любом месте сообщения нужно указать `#<номер задачи>`. Например, вот так.

```
$ git commit -m "Исправить #334, добавить график температуры" 
```

В таком случае GitHub свяжет коммит и задачу.

💡 **Инфинитив и императив**

Для сообщений на русском языке часто рекомендуют использовать инфинитивы. Например: `Добавить тесты для PipkaService`, `Исправить ошибку #123` и так далее.

Для сообщений на английском рекомендуется использовать **повелительное наклонение** (англ. _imperative_). Например: `Use library mega_lib_300`, `Fix exit button` и так далее.

Эти рекомендации сложились исторически, и им следуют многие проекты.

Иногда в только что выполненном коммите нужно что-то поменять: например, добавить ещё пару файлов или заменить сообщение на более информативное.

В таком случае можно внести правки в уже сделанный коммит с помощью опции `--amend` (от англ. _amend —_ «исправить», «дополнить») у команды `commit`: `git commit --amend`.

💡 Важно: опция `--amend` работает только с последним коммитом (`HEAD`).

С опцией `--amend` команда `commit` не создаст новый коммит, а дополнит последний, просто добавив в него файл `common.css`. При этом хеш последнего коммита изменится, потому что изменился список файлов в коммите.

Обратите внимание на опцию `--no-edit`. Она сообщает команде `commit`, что сообщение коммита нужно оставить как было.

Точно так же можно добавить не новый файл, а дополнительные изменения в уже добавленном в коммит файле.

```
# ещё раз отредактировали main.html

$ git add main.html # добавили в список на коммит
$ git commit --amend --no-edit 
```

### Изменить сообщение коммита — `git commit --amend -m "Новое сообщение"`

Может быть и так, что добавлять новые файлы в коммит не нужно, зато понадобилось изменить сообщение.

Допустим, хочется заменить сообщение `Добавить главную страницу` на `Добавить главную страницу и стили`. Сделать это можно через `commit --amend` с флагом `-m`.

```
$ git commit --amend -m "Добавить главную страницу и стили"
$ git log --oneline
a31fa24 Добавить главную страницу и стили 
```

Коротко подытожим урок:

- `--amend` рассчитан на работу с последним коммитом (`HEAD`).
- Дополнить коммит новыми файлами можно с помощью `git commit --amend --no-edit`. Благодаря опции `--no-edit` сообщение к коммиту останется таким, каким и было.
- Изменить сообщение к коммиту позволяет команда `git commit --amend -m "Обновлённое сообщение коммита"`.
