## Развертывание Hexlet-Friends на Render

1. Создайте аккаунт на Render. Для успешного деплоя приложения вам понадобится база данных `PostgreSQL` и приложение
2. Создайте новю базу данных PostgreSQL. `+ New` -> `PostgreSQL`
3. Создайте новый Web service. `+ New` -> `Web service`. В выпадающем списке выберите свой репозиторий с `Hexlet-friends`. Здесь возможно понадобится дать доступы Render к вашим репозитория, если ранее вы их не настроили

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

4.  При успешном завершении логи имеют сдедущий вид. Их всегда можно посмотреть на владке `Logs`

      ```bash
      System check identified no issues (0 silenced).
      August 12, 2023 - 01:43:01
      Django version 4.2.3, using settings 'config.settings'
      Starting development server at http://0.0.0.0:8000/
      Quit the server with CONTROL-C.
 
      Your service is live 🎉
      ```

5.  Теперь приложение будет доступно по ссылке `.onrender.com` на странице приложения.

6. Приложение пустое




7. Как видим миграции не приняты, для этого перейдем вновь на вкладку `Settings` в настройках приложения:

   - в меню `Start Command` укажем `python manage.py migrate`
   - произойдет редеплой в ходе которого применятся миграции. Отследить выполнение команды можно в логах приложения
   - удалим команду из `Start Command`
   - убедимся по логам, что все в порядке

    ```bash
    Performing system checks...
    ﻿Django version 4.1.9, using settings 'config.settings'
    ﻿Starting development server at http://0.0.0.0:8000/
    ﻿Quit the server with CONTROL-C.
    ```

8. Если необходимо выполнить заполнение БД, то в `Start Command` следует указать команду `python manage.py fetchdata <organization name>`
9. Перейдем по ссылке в `Domains` в `Settings` и убедимся, что приложение работает
