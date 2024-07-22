# Gallery project. Пароль и логин в конце 
## Технологический стек
<details>
    <summary>Фронтенд</summary>

    - React.js
    - Axios - библотека для обработки HTTP запросов
    - react-modsl - библиотека для работы с модальными окнами в React.

</details>

<details>
    <summary>Бэкенд</summary>

    - Directus - админ. панель, через которую будем добавлять фото на сайт

</details>

<details>
    <summary>Другое</summary>

    - Docker - для создания, развертывания и запуска приложения в изолированных средах(контейнерах).

</details>

## Процесс выполнения проекта

1. Первым делом в папке Photo-gallery создам react проект с помощью команды

`npx create-react-app photo-gallery-fontend`

2. Далее настрою Directus и Docker, как указано на оф. сайте:

<https://docs.directus.io/self-hosted/quickstart.html>

В корневой дериктории проекта создаю папки database(для хранения базы данных админки) и uploads(для хранения файлов админки). Далее создаю файл docker-compose.yaml (файл для управления многоконтейнерными приложениями) и настриваю переменные окружения как указано  в гайду, указываю пароль, логин от админки и на каких портах будет работать фронт и бэк моего приложения.

3. Создаю Dockerfile (скрипт, который содержит инструкции по созданию Docker-образа) в директории с фронт частью и настраиваю все зависимости. Подробнее про каждую написал в комментах в самом файле.

4. Подключаю небходимые беблиотеки в React-приложение с помощью команды:

`npm install axios react-modal`

5. Прописываю код для фронта своего приложения и соответственно подготавливаю билд докера:

`docker-compose --build`

6. Запускаю контейнеры

`docker-compose up`

7. Приложение заработало. и фрон и бэк запускаются через контейнеры (доп.требование 9) 😁 front (http://localhost:8055), back (http://localhost:8055)

8. Захожу в админку, ввожу логин и пароль которые указал в docker-compose.yaml.

9. Создаю новую коллекцию Photos и добавляю в нее сл. айтемы:

    -  title (input) - text
    - description (string) - textarea (элемент описания добавил, т.к. изначально в планах было сделать альбомы, но к сожалению понял, что не хватит времени :worried:)
    - image (file)

10. Открываю в настройках права доступа для просмотра моей коллекции всем Public ролям. И все готово.
 
 ## Инструкция для запуска

 1. Скачать проект с гита
 2. Установить библиотеки axios и react-modal
 3. Сбилдить проект  `docker-compose --build`
4. Запустить контейнеры

P.S. решил протестировать будет ли работать мой проект скачав его с гита, все работает не считая отображения картинок, не знаю почему. Файл .bd присутствует, title на фронте отображается верно, а картинки с файла .bd не работают :confounded: не смог решить данную проблему. Однако если новые картинки через админку кидать, то все работает

# Скриншоты приложения
## Главная страница

<img src="/description/main_page.png" alt="main_page.png">

## Модальное окно

<img src="/description/modal_page.png" alt="modal_page.png">

# Логин:  admin@example.com

# Пароль:  d1r3ctu5
