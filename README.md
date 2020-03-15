Ветка  master (Snoop Desktop)
=============================

## Snoop Project один из самых перспективных OSINT-инструментов по поиску никнеймов.

<img src="https://raw.githubusercontent.com/snooppr/snoop/master/images/snoop.png" />

Snoop Project разыскивает никнеймы в публичных данных. Это самое сильное ПО с учётом СНГ локации.

Историю смотри
https://raw.githubusercontent.com/snooppr/snoop/master/changelog.txt

| Платформа | Поддержка|
| --------- |:----------:|
| GNU/Linux |✅|
| Windows 7/10 (32/64) |✅|
| Android/Termux/Andrax |✅|
| macOS |🚫|
| IOS |🚫|


**В базе** [561 сайт](https://github.com/snooppr/snoop/blob/master/sites.md "database"), **база расширяется**

## Установка

**Примечание**: Требуемая версия python 3.6 и выше.

```bash
# Клонировать репозиторий
$ git clone https://github.com/snooppr/snoop

# Войти в рабочий каталог
$ cd ~/snoop

# Установить python3 и python3-pip, если они не установлены
$ apt-get update && apt-get install python3

# Установить зависимости 'requirements'
$ pip install --upgrade pip
$ python3 -m pip install -r requirements.txt
# Либо установить все зависимости из 'requirements.txt' в ручную через
$ pip3 install module
```
## Работа Snoop на Android-е
Смотри ветку Termux
https://github.com/snooppr/snoop/tree/termux

## Использование

```bash
$ python3 snoop.py --help

usage: snoop.py [-h] [--donate Y] [--sort Y] [--version] [--verbose] [--csv]
                [--json] [--site] [--time] [--found-print] [--no-func]
                [--userload] [--list all] [--country] [--update Y]
                USERNAMES [USERNAMES ...]

Snoop: поиск никнейма по всем фронтам! (Version 1.1.5_rus Ветка Snoop Desktop)

positional arguments:
  USERNAMES             Никнейм разыскиваемого пользователя, поддерживается
                        несколько имён

optional arguments:
  -h, --help            show this help message and exit
  --donate Y            Пожертвовать на развитие Snoop project-а
  --sort Y              Обновление/сортировка черного и белого списков (.json)
                        сайтов БД Snoop. Если вы не разработчик, не
                        используйте эту опцию
  --version, --about,-V Вывод на печать версий: OS; Snoop; Python и Лицензии
  --verbose, -v         Во время поиска 'username' выводить на печать
                        подробную вербализацию
  --csv                 По завершению поиска 'username' сохранить файл в
                        формате таблицы 'username.CSV' с расширенным анализом
  --json , -j           Указать для поиска 'username' другую БД в формате
                        'json', например, 'example_data.json'. Если у вас нет
                        такой БД, не используйте эту опцию
  --site , -s           Указать имя сайта из БС '--list all'. Поиск 'username'
                        на одном указанном ресурсе
  --time , -t 9         Установить выделение макс.времени на ожидание ответа
                        от сервера (секунды). Влияет на продолжительность
                        поиска. Влияет на 'Timeout ошибки:'Оптимальное
                        значение при хорошем интернет соединении = 9с.
                        Вкл. эту опцию необходимо практически
                        всегда, чтобы избежать длительных зависаний при
                        Internet Censorship
  --found-print, -f     Выводить на печать только найденные аккаунты
  --no-func, -n         ✓Монохромный терминал, не использовать цвета в url
                        ✓Отключить звук ✓Запретить открытие web browser-а
                        ✓Отключить вывод на печать флагов стран
  --userload , -u       Указать файл со списком user-ов. Пример, 'python3
                        snoop.py -u ~/file.txt start'
  --list all            Вывод на печать БД (БС+ЧС) поддерживаемых сайтов
  --country, -c         Сортировка 'вывод на печать/запись в html'
                        результат по странам, а не по алфавиту
  --update Y            Обновить Snoop
```

**Примеры**
```bash
# Для поиска только одного пользователя:
$ python3 snoop.py username1
# Или, например, кириллица поддерживается:
$ python3 snoop.py олеся

# Запуск на OS Windows:
$ python snoop.py username1

# Для поиска одного и более юзеров:
$ python3 snoop.py username1 username2 username3 username4

# Поиск множества юзеров — сортировка вывода результатов по странам;
# избежание зависаний на сайтах (чаще 'мёртвая зона' зависит от вашего ip-адреса);
# выводить на печать только найденные аккаунты; дополнить отчёт csv файлом;
# указать файл со списком разыскиваемых аккаунтов:
$ python3 snoop.py -с -t 9 -f --csv -u ~/file.txt start

# 'ctrl-c/z' — прервать поиск
```
Найденные учетные записи будут храниться в ~/snoop/results/*/username.{txt.csv.html}.


```bash
# Обновляйте Snoop для поддержки ПО и БД в актуальном состоянии:
$ python3 snoop.py --update Y
[^1]: Требуется установка и лёгкая "настройка" Git.
```

<img src="https://raw.githubusercontent.com/snooppr/snoop/master/images/Run.gif"/>

## 
| Основные ошибки ложно-положительного_отклика/соединения при поиске username|
| ---------------------------------------------------------------------------|
| Cайт изменил свой ответ |
| Блокировка сервером диапазона ip-адресов клиента |
| Internet Censorship |
| Срабатывание/защита ресурса captch-ей |
| Недостаточная скорость интернет соединения EDGE/3G (желательная скорость >= 3Mbps) |
| Слишком низкое значение опции '-t' |
| В некоторых случаях недопустимое username |
| Некоторые сайты временно недоступны, например, технические работы |
| Некоторые сайты временно недоступны, например, технические работы |

**Например**

Если вы постоянно (*Debian) получаете "ошибку соединения" на этих ресурсах:

[GipsysTeam;
RamblerDating;
Mamochki;
и т.д.]

Решение следующее (проверенное):
```bash
$ sudo nano /etc/ssl/openssl.cnf

# Изменить в самом низу файла строки:
[CipherString = DEFAULT@SECLEVEL=2]
на
[CipherString = DEFAULT@SECLEVEL=1]
```
https://wiki.debian.org/ContinuousIntegration/TriagingTips/openssl-1.1.1

**Отпечаток публичного ключа:**	076DB9A00B583FFB606964322F1154A0203EAE9D

**Лицензия Snoop Project:** https://github.com/snooppr/snoop/blob/master/COPYRIGHT
