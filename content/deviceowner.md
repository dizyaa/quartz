---
tags:
  - tech/android
title: Device Owner
---
# Особенности 
**Плюсы** 
- Самый надежный способ для управления устройством
- Без рута
- Есть АПИ для работы

**Минусы**
- Нужна предварительная настройка в ручную с помощью ADB
# Шаги
1) Сброс настроек устройства до заводских
2) В случаи миграции, сканим QR код
	**ИЛИ**
2) Ставим АПК через adb
3) Назначаем овнера через adb

# Миграция большого количества устройств

**Сканирование во время настройки устройства**: После сброса устройства до заводских настроек на экране приветствия можно выполнить долгое нажатие на экран, чтобы отсканировать QR-код и автоматически настроить устройство.

Для миграции на устройства можно использовать QR коды
- Нужен URL для скачивания APK
- Чексумма

JSON(Контент QR кода)
```json
{
  "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME":
  "com.example.myapp/.DeviceAdminReceiver",
  "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION":
  "https://your-server.com/myapp.apk",
  "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_CHECKSUM":
  "ABCDEF123456..."
}

```
**Получение чек суммы**: `sha256sum your_app.apk`

# Прод
1) Пишем скрипт с командами ADB
2) Создаем QR для миграции
3) Сбрасываем тестовые устройства
4) Ставим по флоу
5) Тестим лаунчер