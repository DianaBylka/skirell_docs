Тип sensor (Датчики)
====================

Блок sensor отображает данные с датчиков. Подтипов нет. Параметры:

* param_1: Название датчика (String, обязательно).
* measure: Единица измерения (String, может быть пустым).
* min: Минимальное значение (String, обязательно).
* stage_1: Первая граница для цветового индикатора (String, обязательно).
* stage_2: Вторая граница для цветового индикатора (String, обязательно).
* max: Максимальное значение (String, обязательно).
* color_1: Цвет для значений ниже stage_1 (String, обязательно).
* color_2: Цвет для значений между stage_1 и stage_2 (String, обязательно).
* color_3: Цвет для значений выше stage_2 (String, обязательно).
* state_topic: Топик для получения данных (String, обязательно).

Пример::

    {
        "block": 1,
        "type": "sensor",
        "data": 
        {
            "param_1": "Температура",
            "measure": "°C",
            "min": "10",
            "stage_1": "20",
            "stage_2": "30",
            "max": "40",
            "color_1": "color_blue",
            "color_2": "color_green",
            "color_3": "color_red",
            "state_topic": "panel/sensor/1/state"
        }
    }

Пример::

    {
        "block": 2,
        "type": "sensor",
        "data": 
        {
            "param_1": "Интернет",
            "measure": "MB",
            "min": "1",
            "stage_1": "4",
            "stage_2": "8",
            "max": "10",
            "color_1": "color_red",
            "color_2": "color_yellow",
            "color_3": "color_green",
            "state_topic": "panel/sensor/2/state"
        }
    }

.. image:: /images/block_sensor.png