# Simple App For Espresso

UI тесты для Android приложения с использованием Espresso и Allure отчетности.

## Требования

- Android Studio
- JDK 8 или выше
- Android SDK API 31
- Allure CLI (для генерации отчета)

## Зависимости
- Android Gradle Plugin: 7.4.2
- Gradle: 8.5
- Espresso: 3.4.0
- Allure: 2.17.3

## Установка Allure CLI (macOS)

```bash
brew install allure
```
## Установка Allure CLI (Windows)

 1. Скачайте последнюю версию Allure
 ```https://github.com/allure-framework/allure2/releases```

 2. Распакуйте архив в папку, например: ```C:\allure```

 3. Добавьте в PATH (через командную строку администратора)
```
setx PATH "%PATH%;C:\allure\bin"
```
 4. Проверьте установку
```
allure --version
```

## Запуск тестов

1. Запустите эмулятор

2. Запустите тесты
```./gradlew clean connectedAndroidTest```

## Генерация отчетов Allure

1. Сгенерируйте Allure отчет
```
allure generate allure-results -o allure-report --clean
```
2. Откройте отчет
```
allure open allure-report
```
