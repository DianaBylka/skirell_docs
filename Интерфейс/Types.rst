Описание типов блоков
=====================

Тип **scene** (Сценарий)
------------------------

Блок scene отправляет команду на сервер при нажатии, не ожидая ответа и не открывая страницу настроек. Параметры:

* param_1: Назначение сцены (String, может быть пустым).
* param_2: Локация (String, может быть пустым).
* param_3: Название сценария (String, обязательно).
* icon: Иконка (String, Unicode, обязательно).
* command_topic: Топик для отправки команды на сервер (String, обязательно).
* payload: Сообщение, отправляемое на сервер (String, обязательно).

Пример::

    {
        "block": 1,
        "type": "scene",
        "data": 
        {
            "param_1": "Сцена",
            "param_2": "Гостинная",
            "param_3": "Вечеринка",
            "icon": "\uDB84\uDC56",
            "command_topic": "panel/scenes/2",
            "payload": "1"
        }
    }


Тип **light** (Свет)
------------------------

Блок light управляет освещением и имеет четыре подтипа. Общие параметры:

* param_1: Название устройства (String).
* param_2: Локация (String, обязательно).
* setting_name: Название в настройках (String, обязательно).
* icon: Иконка (String, Unicode, обязательно).
* variant_type: Подтип (Light_variant_OnOff, Light_variant_dimmer, Light_variant_color, Light_variant_temperature).
* variant: Параметры подтипа.

Подтип Light_variant_OnOff
~~~~~~~~~~~~~~~~~~~~~~~~~~
Отправляет команду включения/выключения на сервер и ожидает ответа о состоянии. Параметры variant:
* OnOff_command_topic: Топик для отправки команды (String, обязательно).
* OnOff_state_topic: Топик для получения состояния (String, обязательно).
* payload_on: Сообщение для включения (String, обязательно).
* payload_off: Сообщение для выключения (String, обязательно).
Пример::

    {
        "block": 1,
        "type": "light",
        "data": 
        {
            "param_1": "Фонари",
            "param_2": "Двор",
            "setting_name": "Фонари",
            "icon": "\uDB84\uDC20",
            "variant_type": "Light_variant_OnOff",
            "variant": 
            {
            "OnOff_command_topic": "panel/light/1/OnOff_command",
            "OnOff_state_topic": "panel/light/1/OnOff_state",
            "payload_on": "1",
            "payload_off": "0"
            }
        }
    }

Подтип Light_variant_dimmer
~~~~~~~~~~~~~~~~~~~~~~~~~~

Добавляет регулировку яркости. Дополнительные параметры:

* brightness_command_topic: Топик для отправки яркости (String).
* brightness_state_topic: Топик для получения яркости (String).
* brightness_scale: Максимальное значение яркости (Integer).

Подтип Light_variant_color
~~~~~~~~~~~~~~~~~~~~~~~~~~

Добавляет управление цветом (RGB). Дополнительный параметр:

* color_command_topic: Топик для отправки цвета (String).

Подтип Light_variant_temperature
~~~~~~~~~~~~~~~~~~~~~~~~~~

Добавляет регулировку цветовой температуры. Дополнительные параметры:

* temp_command_topic: Топик для отправки температуры (String).
* temp_state_topic: Топик для получения температуры (String).
* max_temp: Максимальная температура (Integer).
* min_temp: Минимальная температура (Integer).
