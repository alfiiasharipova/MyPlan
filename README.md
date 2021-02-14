# План тестирования вклада Накопилка

## Перечень автоматизируемых сценариев
#### Переход на Накопилку:
* Переход на "Накопилку" из меню "Частным лицам" - "Накопилка"
* Переход на "Накопилку" через меню "Вклады"
#### Накопилка страница:
* Переход в анкету по кнопке “Заполнить заявку” из раздела “Накопительный счет Накопилка”
* Переход в анкету по кнопке “Заполнить заявку” из раздела вопросов “Как открыть счет и услугу Копилка для сдачи”
#### Страница Анкеты:
* Отправка заполненной формы валидными данными и отображение информации - “Скоро мы вам перезвоним”
* Отправка пустой формы
* Отправка формы с незаполненным именем
* Отправка формы с незаполненным номером телефона
* Отправка формы без выбранного чекбокса “Я согласен на обработку данных”
* Отправка с неполным телефоном (например, 4 цифры)
* Отправка имени - латиницей/цифры

## Перечень используемых инструментов с обоснованием выбора
Автоматизированное тестирование - т.к. тестируемый функционал часто используется пользователями и будет включен в регресс или смоук.
Для автоматизации будет использоваться связка Java 11 + Maven + JUnit 5 + Selenide +  Allure 2. 

#### Выбраны следующие инструменты:
* Java -  большое комьюнити, много ресурсов/материалов по автоматизации на Java 
* intellij idea - т.к бесплатная версия,  большое комьюнити, множество поддерживаемых плагинов, редактор кода, юзабилити.
* Allure 2 -  т.к бесплатная версия, юзабилити - удобная группировка тестов, история
* Github - как гит репозиторий и CI - бесплатная версия

## Перечень необходимых разрешений/данных/доступов от банка 
* Возможность работы с апи: 
  + Доступ к  API - дошел ли запрос до колл центра после заполнения анкеты, 
  + Обход ограничения на количество отправок формы Анкеты (если есть)
* Если доступа к API нет, телефон специалиста колл центра (Ручное тестирование)

## Перечень и описание возможных рисков при автоматизации
1) Изменения требований (например, провал на бета-тестировании - недовольство пользователей)
2) Частые изменения в дизайне/ коде (Например, локаторы)
3) Наличие багов в SUT -> частый ре-тест
4) Отсутствие сборки, тестовых доступов
5) Увольнение, больничный, отпуск членов команды
6) Квалификация команды
7) Взаимодействие в команде
8) В макетах нет страницы с вкладами - как можно перейти на "Накопилку"
9) Нет макетов для поведения негативных тестов отправки формы в Анкете (текст ошибок, отображение ошибок-подсвечивание/ тултип)
10) Тестирование в разных браузерах - не сказано какие браузеры поддерживаем

## Перечень необходимых специалистов для автоматизации
1) специалист тестирования
2) продакт оунер (уточнение требований/ спецификаций)
3) дизайнер (исправление багов в макетах)
4) бэкенд разработчик (исправление багов)
5) фронтенд разработчик (исправление багов)

## Интервальная оценка с учётом рисков (в часах) в тестировании
#### Итого: 10,75 часов

Написание автотестов - 7 часов:
* Главная страница + Накопилка (а также зависимости, подключение библиотек, архитектура фреймворка) - 3 часа
* Страница Анкеты (а также интеграция с API) - 2,5 часа
* CI - 0,5 часов
* Allure отчет - 1 час

Учет рисков - 3,75 часа: 
1) Изменения требований (например, провал на бета-тестировании - недовольство пользователей) - не оценивается
2) Частые изменения в дизайне/ коде (Например, локаторы) - Построение правильной архитектуры тестового фреймворка (Page object + вынос локаторов при необходимости) - 1 час
3) Наличие багов -> частый ре-тест (Время на запуск тестов + анализ результатов + коммуникация) 1 итерация 1,5 час
4) Отсутствие сборки, тестовых доступов - не оценивается
5) Увольнение, больничный, отпуск членов команды - не оценивается
6) Квалификация команды - не оценивается 
7) Взаимодействие в команде - не оценивается
8) В макетах нет страницы с вкладами - как можно перейти на "Накопилку" Исправление 1 теста 0,25 часов (время на исправление теста + запуск всех тестов)
9) Нет макетов для поведения негативных тестов отправки формы в Анкете (текст ошибок, отображение ошибок - подсвечивание/тултип?) - время на исправление 6 тестов и запуск всех тестов - 1 час
10) Тестирование в разных браузерах - не оценивается 

## Вопрос к продакт оунеру 
* Зачем по завершению отправки анкеты остается фраза “оставьте свои контакты, и мы с вами свяжемся”?
 ![Image alt](https://github.com/alfiiasharipova/MyPlan/blob/main/Screenshot%202021-02-14%20at%2015.33.34.png)
