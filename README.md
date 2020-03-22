Ветка  master (Snoop Desktop)
=============================

## Snoop Project один из самых перспективных OSINT-инструментов по поиску никнеймов.

<img src="https://raw.githubusercontent.com/snooppr/snoop/master/images/snoop.png" />

Snoop Project разыскивает никнеймы в публичных данных. Это самое сильное ПО с учётом СНГ локации.

Историю смотри
https://raw.githubusercontent.com/snooppr/snoop/master/changelog.txt

| Платформа             | Поддержка |
|-----------------------|:---------:|
| GNU/Linux             |     ✅    |
| Windows 7/10 (32/64)  |     ✅    |
| Android/Termux/Andrax |     ✅    |
| macOS                 |     🚫    |
| IOS                   |     🚫    |


**В базе** [632 Websites!!!](https://github.com/snooppr/snoop/blob/master/sites.md "database"), **база расширяется**

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

## Работа Snoop на OS Windows
snoop.exe
https://github.com/snooppr/snoop/releases

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

## Основные ошибки
|  Сторона  |                         Проблема                      | Решение |
|:---------:| ------------------------------------------------------|:-------:|
| ========= |=======================================================| ======= |
| Клиент    |Блокировка соединения проактивной защитой (*Kaspersky) |    1    |
|           |Недостаточная скорость интернет соединения EDGE / 3G   |    2    |
|           |Слишком низкое значение опции '-t'                     |    2    |
|           |недопустимое username                                  |    3    |
|           |Ошибки: [GipsysTeam; RamblerDating; Mamochki]          |    7    |
| ========= |=======================================================| ======= |
| Провайдер |Internet Censorship                                    |    4    |
| ========= |=======================================================| ======= |
| Сервер    |Cайт изменил свой ответ/API                            |    5    |
|           |Блокировка сервером диапазона ip-адресов клиента       |    4    |
|           |Срабатывание/защита ресурса captch-ей                  |    4    |
|           |Некоторые сайты временно недоступны, технические работы|    6    |
| ========= |=======================================================| ======= |

Решения:
1. Перенастроить свой Firewall (например, Kaspersky блочит Ресурсы для взрослых).

2. Проверить скорость своего интернет соединения  
(например, spedtest; [интернетометр](https://yandex.ru/internet/ "yandex"))  
(желательная скорость >= 3Mbps). При низкой скорости увеличить значение опции '--time X'.

3. Исправить username  
(например, на некоторых сайтах недопустимы символы кириллицы или "пробелы" в именах пользоватлей).

4. **Сменить свой ip-адрес**  
("Серый" ip и цензура - самое частое из-за чего вы получаете ошибки пропуска/ложного срабатвания.  
Например самый действенный способ решить проблему — использовать VPN, Tor не очень хорошо подходит для данной задачи).

5. Открыть в Snoop на Github-e Issue/Pull request  
(сообщить об этом разработчику).

6. Не обращать внимание, сайты иногда уходят на ремонтные работы и возвращаются в строй.

7. [Проблема](https://wiki.debian.org/ContinuousIntegration/TriagingTips/openssl-1.1.1 "проблема простая и решаемая") с некоторыми дистрибутивами GNU/Linux  
Решение
```bash
$ sudo nano /etc/ssl/openssl.cnf

# Изменить в самом низу файла строки:
[CipherString = DEFAULT@SECLEVEL=2]
на
[CipherString = DEFAULT@SECLEVEL=1]
```

**Отпечаток публичного ключа:**	[076DB9A00B583FFB606964322F1154A0203EAE9D](https://raw.githubusercontent.com/snooppr/snoop/master/PublicKey.asc "pgp key")

**Лицензия Snoop Project:** https://github.com/snooppr/snoop/blob/master/COPYRIGHT
