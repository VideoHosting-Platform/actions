#actions
setup-and-deploy - Github Actions, который выполняет следующие действия:
- устанавливает все утилиты и программы - docker, kubectl, yc(Yandex Cloud CLI)
- собирает и пушит образ в Docker Registry
- Подключается к облаку при помощи конфигурации
- Конфигурирует kubectl для работы с managed kubernetes в Yandex Cloud 