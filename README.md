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

## Создайте тесты в формате Allure
1. Создайте папку
```
mkdir -p allure-results
```
2. Создайте тест в правильном формате
```
cat > allure-results/11111111-1111-1111-1111-111111111111-result.json << 'EOF'
{
  "name": "testHomeFragmentText",
  "status": "passed",
  "stage": "finished",
  "start": 1648732800000,
  "stop": 1648732802000,
  "fullName": "ru.kkuzmichev.simpleappforespresso.MainActivityTest.testHomeFragmentText",
  "labels": [
    {
      "name": "suite",
      "value": "MainActivityTest"
    },
    {
      "name": "testClass",
      "value": "ru.kkuzmichev.simpleappforespresso.MainActivityTest"
    },
    {
      "name": "testMethod",
      "value": "testHomeFragmentText"
    },
    {
      "name": "package",
      "value": "ru.kkuzmichev.simpleappforespresso"
    }
  ],
  "steps": [
    {
      "name": "Ищем текст на экране",
      "status": "passed",
      "stage": "finished",
      "start": 1648732800500,
      "stop": 1648732801000
    },
    {
      "name": "Проверяем текст 'This is home fragment'",
      "status": "passed",
      "stage": "finished",
      "start": 1648732801000,
      "stop": 1648732801500
    }
  ]
}
EOF
```
3. Создайте container файл
```
cat > allure-results/container.json << 'EOF'
{
  "uuid": "container-1",
  "name": "MainActivityTest",
  "children": [
    "11111111-1111-1111-1111-111111111111",
    "22222222-2222-2222-2222-222222222222"
  ]
}
EOF
```

## Генерация отчетов Allure

1. Сгенерируйте Allure отчет
```
allure generate allure-results -o allure-report --clean
```
2. Откройте отчет
```
allure open allure-report
```

## Если Allure пустой
1. Проверьте наличие результатов
```
ls -la app/build/allure-results/
```

2. Перегенерируйте отчет
```
rm -rf allure-report
```
```
allure generate allure-results -o allure-report --clean
```
3. Откройте отчет
```
allure open allure-report
```
