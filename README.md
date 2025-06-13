# actions
setup-and-deploy - Github Actions, который выполняет следующие действия:
- устанавливает все утилиты и программы - docker, kubectl, yc(Yandex Cloud CLI), helm
- собирает и пушит образ в Docker Registry
- логинится в helm-registry пользователя, чтобы получать оттуда чарт
- Подключается к облаку при помощи конфигурации
- Дальше workflow должен сам сделать helm upgrade


# Параметры, которые нужно задать
- registry - Docker registry, в который пушится образ
- image_name - Docker image name
- folder_id - ID папки, получить в облаке
- cluster_id - ID кластера managed k8s, получить в облаке
- dockerhub_username - Dockerhub username
- dockerhub_token - токен. Чтобы получить, нужно
  - Нажать на профиль справа сверху -> Account Settings -> Personal access tokens
  - Generate new token -> дать права Read & Write -> Generate
- yc_service_account_key - сервисный аккаунт yandex cloud для ci/cd. Чтобы получить, нужно
  - Зайти в облако, создать сервисный аккаунт
  - Сервисному аккаунту выдать права k8s.cluster-api.cluster-admin, k8s.admin, editor(права избыточные, но работают)
  - Создать новый ключ -> Создать авторизованный ключ -> RSA_4096 -> Скачать ключ
  - Скопировать его содержимое из файла
- gh_token - Github Token(Обязательно нужен токен redblood-pixel, так как он владелец чарта). Чтобы получить, нужно
  - Настройки → Developer settings → Personal access tokens → Tokens (classic).
  - Дайте права: write:packages, read:packages, delete:packages. Лучше указать больше время жизни
  - Скопировать содержимое