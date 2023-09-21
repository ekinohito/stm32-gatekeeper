# stm32-gatekeeper

## Необходимые задачи

- Опрос rfid датчиков (как можно чаще)
- Опрос wifi-адаптера на предмет изменений в базе данных пропусков (пару раз в минуту)
- Если wifi сеть есть и есть новые записи в журнале прохода:
  - Отправить данные на сервер и удалить из локального журнала
- Если на rfid датчиках новая карта:
  - Считываем данные и сверяем с базой данных пропусков
  - Если запись совпадает:
    - Добавляем в журнал запись о новом проходе
    - Подаем сигнал на нужный реле
    - Выводим на экран информацию о пропуске
  - Если не совпадает:
    - Добавляем в журнал запись о неудачной попытке прохода
    - Выводим на экран информацию о невозможности прохода

## Отладка

Отладка будет доступна по serial порту, подключаемому через usb-ttl адаптер к компьютеру. Команды позволяют проверить все модули, подключаемые к микроконтроллеру и проверить корректность работы программы

Набор команд:

1. `TURN CW/CCW` - открытие реле поворота по часовой/против часовой стрелки
2. `WIFI <Id> <Pwd>` - подключение к wifi сети
3. `DISP <Msg>` - вывод сообщения на дисплей
4. `MEM DUMP/CLR` - выгрузка/очистка базы данных из eeprom модуля
5. `USR ADD <UsrInfo>` - добавление пользователя с картой, приложенной к модулю считывания
6. `USR DEL <UsrId>` - удаление пользователя
7. `ESP <AT-command>` - проксирование AT-комманд до wifi модуля
8. и т.д.


