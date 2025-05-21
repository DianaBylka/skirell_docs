Тип scene (Сценарий)
====================

Блок scene отправляет команду на сервер при нажатии, не ожидая ответа и не открывая страницу настроек. Параметры:

* param_1: Назначение (String, может быть пустым).
* param_2: Локация (String, может быть пустым).
* param_3: Название (String, обязательно).
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
            "command_topic": "panel/scenes/1",
            "payload": "1"
        }
    }

Пример::

    {
        "block": 2,
        "type": "scene",
        "data": 
        {
            "param_1": "",
            "param_2": "Режим",
            "param_3": "Чтение",
            "icon": "\uDB84\uDC56",
            "command_topic": "panel/scenes/2",
            "payload": "1"
        }
    }

.. image:: /images/block_scene.png