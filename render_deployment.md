## Развертывание Hexlet-Friends на Render

1. Создайте аккаунт на Render. Для успешного деплоя приложения вам понадобится база данных `PostgreSQL` и приложение
2. Создайте новю базу данных PostgreSQL. `+ New` -> `PostgreSQL`
3. Дайте ей имя и выберите регион поближе к вам. При желании остальные поля можно не заполнять.  `Create database`
4. Создайте новый Web service. `+ New` -> `Web service`. В выпадающем списке выберите свой репозиторий с `Hexlet-friends`. Здесь возможно понадобится дать доступы Render к вашим репозитория, если ранее вы их не настроили

   - Заполнить следущие поля:

      - `Name` Произвольное имя
      - `Region` Тотже, что и у базы данных
      - `Branch` main (e.g., master/main)
      - `Root` directory Оставить пустым
      - `Environment` Docker

    - Открыть раздел "Advanced" и добавить переменные окружения:

      - `PORT` - присвойте значение 8000
      - `GITHUB_AUTH_TOKEN`
      - `SECRET_KEY`
      - `DATABASE_URL`: Internal Database URL из базы данных на Render
     
   - `Create Web Service`

5.  При успешном завершении логи имеют сдедущий вид. Их всегда можно посмотреть на владке `Logs`

      ```bash
      System check identified no issues (0 silenced).
      August 12, 2023 - 01:43:01
      Django version 4.2.3, using settings 'config.settings'
      Starting development server at http://0.0.0.0:8000/
      Quit the server with CONTROL-C.
 
      Your service is live 🎉
      ```

6.  Теперь приложение будет доступно по ссылке `.onrender.com` на странице приложения.

7. Для выполнения миграций вам понадобится развернуть приложение локально, если у вас бесплатный тариф или воспользоваться Shell на Render, если платный. Для подключения локального приложения к БД используйте External Database URL. Выполните `python manage.py migrate`

8. Для заполнения БД выплоните команду `python manage.py fetchdata <organization name>`
11. Перейдите по ссылке на странице приложения на Render и убедитесь, что приложение работает
