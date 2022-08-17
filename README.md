# hello_api_TMDB
Принимает значение ключа API и создаёт переменную `user_api_key` из функции `get_user_api_key`, если ключ не верный, то возвращает сообщение:
```
Invalid api key
```

Если API ключ был введён верно, то cкрипт извлекает бюджет фильма с `id 215`
```
4000000
```

## Использование

В терминале введите команду:
```shell
python hello_api_TMDB.py
```

Скрипт запросит секретный ключ, необходимо его ввести:
```shell
Enter your api key v3:секретный_ключ
4000000
```

# find_similar
Файл выводит рекомендованные фильмы для просмотра, анализируя введённый фильм пользователем.

При запуске просит пользователя ввести путь к базе данный

Создаёт переменную `films_data` , в которой при помощи функции `load_data`  открыват в указанном ранее пути Json объект.

Если указан неверный путь, то выводит сообщение:
```
'File not found, sorry...'
```
Если путь указан верно, то следующим просит ввести пользователя название фильма для поиска

Далее с помощью функции `find_my_film` ищет данный фильм в базе.

Если фильм не найден, то выводит сообщение:
```
No such film in FilmsDB
```

Если фильм был найден, то выводит рекомендованные фильмы к просмотру

# own_db_helpers
Возвращает Json объект из базы данных, запрошенных в файле find_similar

# Файл tmdb_helpers.py

Содержит функции для скачивания информации из TMDB и проверки секретного ключа.
# make_own_db
Создание локальной базы фильмов под именем `MyFilmDB.json` в формате JSON.

Скрипт запрашивает секретный ключ и загружает информацию о фильмах с `id` от `0` по `999`. Если фильм с таким `id` найден, то данные фильма сохраняются, если нет &ndash; то скрипт переходит к следующему `id`. Т.о. по итогу загрузки фильмов в локальной базе может оказаться меньше чем 999.

### Использование

В терминале введите команду:

```shell
python make_own_db.py
```

Скрипт запросит секретный ключ, необходимо его ввести, затем пойдет загрузка, которая может занять некоторое время (15-20 мин.). Процент готовности выводится в консоль:

```shell
Enter your api key v3:секретный_ключ
please, wait, this operation may take smth like 15-20 minutes
0.0 percent complete
1.0 percent complete
2.0 percent complete
...
100.0 percent complete
```

После успешной загрузки в корне проекта появится файл `MyFilmDB.json`.
