# Анализ репозиториев Github

Скрипт для анализ репозиториев github.

## Примеры использования

Запуск скрипта без параметров:
```
>> python main.py https://github.com/MonoGame/MonoGame/ -e 1900-12-31
```

Запуск скрипта с указанием ветки для анализа:
```
>> python main.py https://github.com/MonoGame/MonoGame/ -b slave
```

Запуск скрипта с указанием даты начала и даты конца анализа:
```
>> python main.py https://github.com/MonoGame/MonoGame/ -s 1900-11-30 -e 1900-12-31
```