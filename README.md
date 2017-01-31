# xCloud - Информация
Система пользовательского управления сервером, манипуляций файлами с рядом системных и вспомогательных ПО. Эту систему можно назвать домашним облаком с поддержкой многозадачности и более расширенным функционалом.
- Разработчик: RVA ( Quareal Foundation )
- Сайт Quareal: https://quareal.ru/
- Сайт проекта ( в разработке ): https://projects.quareal.ru/
- Страница GitHub: https://github.com/rvasources/
![Главная страница](https://github.com/rvasources/xCloud/blob/master/main.png)
- Платформы: Desktop, Mobile
- Браузеры: Все современные браузеры с включенным JS
- Серверная часть: Linux, PHP, MySQL
- Язык: Русский ( Российская Федерация )
- Текущая версия: 0.3 Alpha

# xCloud - Приложения
В системе есть 3 типа приложений, которые размещены в каталоге ./apps/, информация о них записана в DB.
- Обычное приложение - иконка приложения показывается в рабочей области, открывается через стандартное окно
- Скрытое приложение - не показывается на главной странице, но открывается через окно
- Мини приложение - не показывается на главной странице и контент приложения находится в вкладке уведомления ( например плеер музыки )

Каждое приложение обязательно имеет главный файл `code.php` в котором распологается php код приложения. При создании приложения, вы можете пользоваться API системой по средствам обращения к глобальной переменной `$APP`. Приложения и система общаются по средствам POST запросов. Каждое приложение в конце имеет обязательный `return array(тут параметры, в записимости от приложения);`
![Пример оконного приложения](https://github.com/rvasources/xCloud/blob/master/window.png)
В системе имеется ряд стандартных приложений: Настройки, Менеджер памяти, Apps Market, dolphx, Обозреватель картинок, Плеер, Текстовый редактор, Редактор аккаунта. Все приложения от разработчика ( RVA & Quareal ) можно скачать через Apps Market. Сверху окна находится 2 кнопки, желтая - развернуть окно во всю длину, второе - закрыть приложение. В некоторых ситуациях красная кнопка будет вас возвращать в приложение открытое ранее ( если открыто несколько программ ).

# xCloud - Реестры
Предусматриваются несколько реестров. 
- Реестр аккаунтов ( в нем вы создаете аккаунты для авторизации )
- Реестр приложений ( список приложений, их конфигураций )
- Реестр зависимостей ( определяет, какой файл какой программой следует открывать )

Каждый из перечисленных реестров можно редактировать в программе `Настройки`

# xCloud - Пользовательские настройки
Все настройки платформы, на которой установлена система осуществляется через стандартное приложение `Настройки`. В нем также осуществляется мониторинг системы.
![Настройки](https://github.com/rvasources/xCloud/blob/master/settings.png)

# xCloud - API Системы
Пользователю и разработчику доступны API для работы с рабочей зоной облака, приложениями и основными окнами, реестром уведомлений, файлами. Каждая из API доступна либо через статическую библиотеку `Project::имя()` либо через глобальные переменные. Так же API приложений разбивается на несколько частей: API к системе, API шаблонизатора ( для создания шаблона приложений ), API для проигрывания JS сценария.

# xCloud - Верхнее меню
Верхнее меню состоит из 4 вкладок: Приложения, Уведомления, Поиск, %username%
- Приложения - основная вкладка со списком установленных приложений
- Уведомления - система оповещений об обновлениях, записях приложений, и управление мини приложениями
- Поиск - вкладка поиска файлов, приложений и т.д.
- %username% - при нажатии открывается приложение `Редактор аккаунта`

# Установка
ВНИМАНИЕ: данная версия находится на стадии разработки и не предназначена для полноценного использования, только для ознакомления. Ниже описаны шаги, которые вам нужно проделать для установки. Уже предполагается, что у вас на сервере стоит дистрибутив Linux, PHP, MySQL, Apache/Nginx.
 1) Создайте пользователя MySQL и импортируйте в него базу данных xCloud
 1.2) Отредактируйте таблицу settings, колонка json_config, параметр home_path и вставьте в него рабочую область. пример: "/"
 2) Откройте файл ./resources/config.php и внесите в него ваши данные MySQL
 3) Скопируйте все файлы xCloud в папку домена, где будет стоять система
 4) Выставьте права 777 на рабочую область ( шаг 1.2 ) и папку ./apps/
Данные для входа: test:qwerty321
