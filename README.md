# ByeByeDPI Android

[![Build](https://github.com/solodyagin/ByeByeDPIAndroid/actions/workflows/build.yml/badge.svg?branch=master)](https://github.com/solodyagin/ByeByeDPIAndroid/actions/workflows/build.yml)

<div style="text-align: center;">
  <img alt="Логотип ByeDPI" src="https://github.com/solodyagin/ByeByeDPIAndroid/raw/master/.github/images/logo.svg" width="100%" height="200px">
</div>

---

Приложение для Android, которое локально запускает ByeDPI и перенаправляет весь TCP трафик через него.

Для стабильной работы может потребоваться изменить настройки. Подробнее о различных настройках можно прочитать в [документации ByeDPI](https://github.com/hufrea/byedpi/blob/main/README.md).

Приложение не является VPN. Оно использует VPN-режим на Android для перенаправления трафика, но не передает ничего на удаленный сервер. Оно не шифрует трафик и не скрывает ваш IP-адрес.

Приложения является форком [ByeDPIAndroid](https://github.com/dovecoteescapee/ByeDPIAndroid)

---

### Возможности

* Поддержка фильтра приложений для режима VPN (раздельное туннелирование через whitelist/blacklist)
* Автозапуск VPN/Proxy при старте устройства
* Автоподключение к VPN/Proxy при запуске приложения
* Сохранение списков параметров командной строки с возможностью переключения
* Улучшена совместимость с Android TV/BOX, исправлены некоторые ошибки оригинала

<div style="text-align: center;">
    <img alt="Скриншот-1" src="https://github.com/solodyagin/ByeByeDPIAndroid/raw/master/.github/images/settings_screen_2.png">
    <img alt="Скриншот-2" src="https://github.com/solodyagin/ByeByeDPIAndroid/raw/master/.github/images/apps_screen_2.png">
</div>

### Использование
* Для работы автозапуска активируйте пункт в настройках.
* Рекомендуется подключится один раз к VPN, чтобы принять запрос.
* После этого, при загрузке устройства, приложение автоматически запустит сервис в зависимости от настроек (VPN/Proxy)
* Если у вас Android TV/BOX, и при подключении пропадает соединение по Ethernet, активируйте режим белого списка и укажите нужные приложения, которые должны работать через VPN (например, YouTube)
* Инструкция для [SberBOX](sbox.md)

### Как использовать ByeDPI вместе с AdGuard?
* Запустите ByeDPI в режиме прокси.
* Добавьте ByeDPI в исключения AdGuard на вкладке "Управление приложениями".
* В настройках AdGuard укажите прокси:
```plaintext
Тип прокси: SOCKS5
Хост: 127.0.0.1
Порт: 1080 (по умолчанию)
```

## Сборка

Для сборки приложения требуется:

1. JDK 8 или новее
2. Android SDK
3. Android NDK
4. CMake 3.22.1 или новее

Сборка приложения:

1. Клонируйте репозиторий с подмодулями:
   ```bash 
   git clone --recurse-submodules
   ```
2. Запустите скрипт сборки из корня репозитория:
   ```bash
   ./gradlew assembleRelease
   ```
3. APK будет лежать в `app/build/outputs/apk/release/`
