---
tags:
  - tech/android
title: Режим "Киоска"
---

> [!WARNING] 
> Работает только на с 5.0(lollipop) Android!

## Родительское приложение
Нужно написать приложение, которое закрывает и блокирует любой доступ к настройкам и остальным приложением. 

Для запуска режима используется
```kotlin
startLockTask() // activity context
```

Остановка соотвественно
```kotlin
stopLockTask()
```

Для автозагрузки можно использовать **BootReceiver**
## Отключение системных кнопок (назад, домой)

```kotlin
override fun onBackPressed() {
    // Заблокировать кнопку "Назад"
}

override fun onWindowFocusChanged(hasFocus: Boolean) {
    super.onWindowFocusChanged(hasFocus)
    if (!hasFocus) {
        // Перехватываем кнопку "Домой" 
        val closeDialog: Intent = Intent(Intent.ACTION_CLOSE_SYSTEM_DIALOGS)
        sendBroadcast(closeDialog)
    }
}

```

## Служебные библиотеки

ДЕПРЕКЕЙНД
**DeviceAdminReceiver** и **DevicePolicyManager** — это встроенные классы Android для управления корпоративными устройствами.

## Основные ссылки
- [Официальная документация Android: Device Administration](https://developer.android.com/guide/topics/admin/device-admin)
- [Документация по Lock Task Mode](https://developer.android.com/work/dpc/lock-task-mode)  ! [DEPRECATION](https://developers.google.com/android/work/device-admin-deprecation)
