Для того, чтобы создать свой сервер для ScSpeak, вам понадобится:

* Приложение ScSpeak [Загрузить из GitHub](https://github.com/sashaqwert/scspeak/releases).
* Папка, доступная по протоколу HTTP/ (К файлам будут поступать GET-запросы)
* Компьютер
* Интернет-подключение

ПО, рекоммендованное на ПК (к серверу отношения не имеет!)

* ОС Linux (Kubuntu, Linux Mint, OpenSuse)
* Графическое окружение KDE
* KDE Connect (Для передачи данных на ПК)
* Dolphin (Файловый менеджер KDE. Поддерживает FTP)
* Kate (Текстовый редаттор)
* Mozilla Firefox

# Подготовка:

1. Установить ScSpeak на телефон или планшет
2. Заполнить базу слов нужными для сервера словами любым способом. (можно скачать слова с другого сервера)<br>
**ВНИМАНИЕ!** Слова начинают отображаться, если их 2 (или больше)
3. Открыть настройки приложения
4. Перейти в раздел "Основные"
5. Разрешить экспорт слов
6. Настройки приложения ScSpeak
7. Вернуться на главный экран приложения

# Экспорт на ПК

1. Убедитесь, что вы смоете получить файл выбранным вами способом. (в случае KDE Connect устройства должны быть спарены и подключены к одной и тойже сети WI-FI
2. Нажать на кнопку экспорта (значёк "upload")
3. Выбрать удобный для вас способ

# Пример полученной информации:

```
This data ONLY for ScSpeak server!
=================================================================
библиотека
{"ru":"библиотека", "en":"library", "mk":"библиотека", "ruTranscriptionToEN":"bibleoteka", "enTranscriptionToRU":"либрари", "ruTranscriptionToMK":"библиотека","mkTranscriptionToRU":"библиотека", "enTranscriptionToMK":"библиотека", "mkTranscriptionToEN":"bibleoteka"}
=================================================================
компьютер
{"ru":"компьютер", "en":"computer", "mk":"компјутер", "ruTranscriptionToEN":"computer", "ruTranscriptionToMK":"компјутер", "enTranscriptionToRU":"компьютер", "enTranscriptionToMK":"компјутер", "mkTranscriptionToRU":"компьютер",  "mkTranscriptionToEN":"computer"}
=================================================================
кот
{"ru":"кот", "en":"cat", "mk":"мачка", "ruTranscriptionToEN":"cat", "ruTranscriptionToMK":"кот", "enTranscriptionToRU":"кэт", "enTranscriptionToMK":"кэт", "mkTranscriptionToRU":"мачка",  "mkTranscriptionToEN":"machka"}
=================================================================
мир
{"ru":"мир", "en":"world", "mk":"свет", "ruTranscriptionToEN":"mir", "ruTranscriptionToMK":"мир", "enTranscriptionToRU":"ворлд", "enTranscriptionToMK":"ворлд", "mkTranscriptionToRU":"свет",  "mkTranscriptionToEN":"svet"}
=================================================================
образец
{"ru":"образец", "en":"example", "mk":"примерок", "ruTranscriptionToEN":"obrazetz", "ruTranscriptionToMK":"образец", "enTranscriptionToRU":"экзампл", "enTranscriptionToMK":"экзампл", "mkTranscriptionToRU":"примерок",  "mkTranscriptionToEN":"primerok"}
=================================================================
окно
{"ru":"окно", "en":"window", "mk":"прозорец", "ruTranscriptionToEN":"okno", "ruTranscriptionToMK":"окно", "enTranscriptionToRU":"виндоу", "enTranscriptionToMK":"виндоу", "mkTranscriptionToRU":"прозорец",  "mkTranscriptionToEN":"prozoretz"}
=================================================================
сервер
{"ru":"сервер", "en":"server", "mk":"сервер", "ruTranscriptionToEN":"server", "ruTranscriptionToMK":"сервер", "enTranscriptionToRU":"сервер", "enTranscriptionToMK":"сервер", "mkTranscriptionToRU":"сервер",  "mkTranscriptionToEN":"server"}
=================================================================
слово
{"ru":"слово", "en":"word", "mk":"збор", "ruTranscriptionToEN":"slovo", "ruTranscriptionToMK":"слово", "enTranscriptionToRU":"ворд", "enTranscriptionToMK":"ворд", "mkTranscriptionToRU":"збор",  "mkTranscriptionToEN":"zbor"}
=================================================================
стол
{"ru":"стол", "en":"table", "mk":"маса", "ruTranscriptionToEN":"stol", "ruTranscriptionToMK":"стол", "enTranscriptionToRU":"тЭйбл", "enTranscriptionToMK":"тЭйбл", "mkTranscriptionToRU":"маса",  "mkTranscriptionToEN":"masa"}
=================================================================
файл
{"ru":"файл", "en":"file", "mk":"фајл", "ruTranscriptionToEN":"fale", "ruTranscriptionToMK":"фајл", "enTranscriptionToRU":"тЭйбл", "enTranscriptionToMK":"фајл", "mkTranscriptionToRU":"файл",  "mkTranscriptionToEN":"fale"}
=================================================================
END OF SERVER DATA
```

# Объяснение полученной информации:

* `===...===` - Разделитель (отделяет одно слово от другого
* `Библеотека`, `Компьютер` ИТД (Строка №1) - имя файла на устройстве
* `{...}` (строка №2) - JSON для сервера. (Если эта строка не является JSON, то она вам не нужна)


# Загрузка данных на сервер

Сервер - это папка, доступная по протоколу HTTP [Пример сервера](https://web.archive.org/web/20170905212322/http://sccraft.ru/android-app/scspeak/)

В любом сервере ScSpeak есть:

* Манифест сервера (`list.sccraft`) можно создать в Kate
* Папка со словами (`words`)
* Как минимум один файл JSON в папке со словами, или в любой её вложенной папке

Чтобы поместить слово на сервер нужно его JSON сохранить как отдельный файл (с форматом `.json`).

Пример манифеста:

```
библиотека 1/0
компьютер 1/1
кот 1/2
мир 1/3
образец 1/4
окно 1/5
сервер 1/6
слово 1/7
стол 1/8
файл 1/9
```

Каждое слово - это одна строка манифеста.<br>
Имена файлов для сохранения находятся в первой колонке (БЕЗ ПРОБЕЛОВ!)<br>
Во второй колонке находмися путь к файлу JSON на сервере относительно папки `words` (без "/"в начале и `.json` на конце)<br>

# Как скачать слова с сервера?

Чтобы скачать слова с сервера, введите URL с папки с файлом `list.sccraft` и синхронизируйтесь с сервером!
