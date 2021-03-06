# Анализ репозиториев Github

Скрипт для анализ репозиториев github.

## Требования

Провести анализ репозитория, используя REST API Github.
Результат анализа выводятся в stdout.
Необходимо вывести такие результаты:
  * Самые активные участники. Таблица из 2 столбцов: login автора, количество его коммитов.
    Таблица отсортирована по количеству коммитов по убыванию. Не более 30 строк.
  * Количество открытых и закрытых pull requests.
  * Количество "старых" pull requests. Pull requests считается старым, 
    если он не закрывается в течении 30 дней.
  * Количество открытых и закрытых issues.
  * Количество "старых" issues. Issue считается старым, 
    если он не закрывается в течении 14 дней.


## Замечания по коду

* Работа с сетью. Никто не гарантирует, что у нас не будет проблем с сетью на клиенте, проблем с сетью у GitHub, проблем в функционировании самого GitHub. Сейчас в коде нет защиты от таких проблем.
* Привязка к допущению, что GitHub всегда будет выдавать по-умолчанию pull request упорядоченно по дате созданию. Никто не запрещает им это изменить. Код из-за этого перестанет правильно работать.
* https://github.com/maruschin/some_python/blob/master/main.py#L119 - нарушен отступ.
* parse_headers_link, множественные замены в строке по паттерну, хотя достаточно было бы сделать поиск и нужные данные вытаскивать из групп-совпадений.
* Код изобилует самоповторениями, фактически каждая функция получения данных создает URL.


## Примеры использования

Запуск скрипта без параметров:
```
>>> python main.py https://github.com/MonoGame/MonoGame/ -e 1900-12-31
```

Запуск скрипта с указанием ветки для анализа:
```
>>> python main.py https://github.com/MonoGame/MonoGame/ -b slave
```

Запуск скрипта с указанием даты начала и даты конца анализа:
```
>>> python main.py https://github.com/MonoGame/MonoGame/ -s 1900-11-30 -e 1900-12-31
```

Запуск doctest:
```
>>> python -m doctest -v main.py
```
