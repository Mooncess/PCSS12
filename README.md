# Работа с Memaid в Github
## GitGraph
```mermaid
gitGraph
   commit id: "Initial commit"

   branch develop
   commit id: "Разработка функционала бронирования"
   branch feature/personnel_management
   commit id: "Начата разработка функционала управления персоналом"
   commit id: "Добавления функций назначения задач"
   checkout develop
   merge feature/personnel_management tag: "функционал управления персоналом разработан"
   
   branch feature/notifications
   commit id: "Начата работа над функцией уведомлений"
   commit id: "Отладка мобильных уведомлений"
   checkout develop
   merge feature/notifications tag: "Функционал уведолмений разработан"
   
   branch feature/payment
   commit id: "Начата работа над функционалом оплаты"
   commit id: "Интеграция платежного шлюза"
   checkout develop
   merge feature/payment tag: "Функционал оплаты разработан"

   commit id: "Фикс ошибок"

   checkout main
   merge develop tag: "Релиз v1.0.0"
```
### Пояснения 
Первым на рассмотрении будет GitGraph. С его помощью можно отобразить базовый процесс работы с разными ветками при разработке системы. Такой граф является более наглядным в сравнение с ручным разбором истории коммитов.
Пример графа для ИС гостиницы представлен выше.
## Квадрант-граф
``` mermaid
   quadrantChart
    title Приоритет разработки функционала
    x-axis Low priority --> High priority
    y-axis Ease of Development --> Difficulty of Development

    "Notifications" : [0.25, 0.25]
    "Booking Management" : [0.90, 0.70]
    "Room Management" : [0.75, 0.40]
    "Report Generation" : [0.65, 0.75]
    "Payment Processing" : [0.90, 0.30]
    "Guest Data Management" : [0.60, 0.30]
    "Pricing Policy Management" : [0.60, 0.15]
    "Staff Management" : [0.55, 0.60]
```
### Пояснения 
Следующим на рассмотрении идет Квадрант-граф. Он позволяет классифицировать задачи по разным критериям, например, высокая/низкая сложность и высокий/низкий приоритет. Данный подход удобен, когда в момент разработки возникает несколько задач и команда не сразу понимает за что браться. Данный граф помогает оценить каждую задачу и сфокусировать внимание на самых важных. Пример такого графа представлен выше.
## User Journey Diagram
``` mermaid
journey
    title User Journey: Бронирование, Оплата и Уведомление
    section Бронирование номера
      Клиент выбирает номер: 4: Клиент
      Клиент оформляет бронь: 5: Клиент
      ИС проверяет форму: 5: ИС
      Перенаправление на стр. оплаты: 3: ИС
    section Оплата
      Клиент вводит платежные данные: 3: Клиент
      Передача в платежный шлюз: 5: ИС
      Обрабатка транзакции: 4: Платежный шлюз
      Подтверждение оплаты: 7: ИС
    section Уведомление
      Уведомление об успешной оплате: 7: ИС
      Напоминание о брони: 7: Клиент
```
### Пояснения
Третьим по очереди, но не по значению можно выделить User Journey Diagram. Данная диаграмма позволяет оценить пользовательский опыт при взаимодействии с каждым элементом нашей системы и выявить слабые места. 
## Mind Map
``` mermaid
mindmap
  root((ИС гостиницы))
    Клиент
      Бронирование
        Выбор номера
        Подтверждение бронирования
        Оплата бронирования
      Уведомления
        Получение уведомлений о статусе бронирования
        Напоминания о заезде
      Обслуживание
        Оставление отзывов
        Заказ дополнительных услуг
    Администратор
      Управление номерным фондом
        Добавление/удаление номеров
        Управление доступностью номеров
      Управление бронированиями
        Подтверждение/отмена бронирований
        Проверка статуса бронирований
      Управление персоналом
        Распределение задач
        Контроль работы персонала
      Генерация отчетов
        Финансовые отчеты
        Отчеты о загрузке номеров
    Персонал
      Просмотр задач
      Изменение статуса задач
```
### Пояснения
И наконец последняя диаграмма – Mind Map. Данные диаграммы можно использовать для визуализации ключевых аспектов клиент-серверной системы, которые можно сгруппировать по ролям. 