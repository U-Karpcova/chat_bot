### Додавання нової теми в чат-бот:
#### Створення теми:
Для того, щоб додати нову тему до чат-бота,
треба спочатку створити змінну, 
яка буде містити рядок тексту із 
повідомленням виду:

```f" {you_chose}``` _(далі має йти назва вашої теми)_
```{topics}``` _(далі мають йти назви функцій або підтем вашої теми)_```"```

Назва змінної має складатися зі скороченої назви вашої теми та ```_msg```.

#### Створення функцій:

Після цього ви маєте створити функції, які користувач може обирати в вашій темі.
Функції повинні мати зрозумілу назву та не вимагати аргументів при виклику. 
Якщо для виконання функції потрібне введення користувачем якоїсь інформації, то після кожного викристання ```input()```
ви маєте зберігати введене користувачем до файлу з діалогом. 
Для цього потрібно викристати код:
```python
save_to_file(filename, user_input)
```
де ```user_input``` - це назва змінної, якій присвоюється те, що ввів користувач. 

Крім того, в функціях ви маєте використовувати ```input()``` таким чином:

```user_input = if_help(input("User: "), topic)```
де topic - це назва теми, якій відповідає ця функція.

Також написана вами функція має повертати такі типи значеннь:
* ``back``, якщо на будь-якому етапі виконання функції користувач ввів back
* ```exit```, якщо на будь-якому етапі виконання функції користувач ввів exit
* ```done!```, коли виконання функції завершене.

#### Додавання функцій та теми до коду

Тепер ви маєте до словника ``previous_topic_dict`` додати пари, в яких ключем буде тема, 
а значенням - попередня тема цієї теми. Тобто ключами будуть теми функцій, значеннями - 
назва нової доданої теми. Для назви нової доданої теми значенням потрібно вказати тему "меню",
якщо в хочете додати це як основну тему. Якщо ви бажаєте зробити нову тему підтемою до
вже існуючої, вкажіть її значенням ту тему, до якої її додаєте.

Далі в словник ``topic_answers_dict`` ви маєте додати пари, де ключ - це тема, а значення - функція,
яку вона виконує, або повідомлення, яке вона виводить. 

#### Розпізнавання тем в словах користувача

Для того, щоб бот розпізнавав, яку тему хоче обрати користувач, 
потрібно до функції ``def check_input(split_input)`` додати рядок виду:
