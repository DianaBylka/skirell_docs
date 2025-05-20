Тип climate (Климат)
====================

Блок climate управляет климатическими устройствами и имеет два подтипа. Общие параметры:

* param_1: Название устройства (String, может быть пустым).
* param_2: Локация (String, обязательно).
* setting_name: Название в настройках (String, обязательно).
* icon: Иконка (String, обязательно).
* min_target: Минимальная температура (String, обязательно).
* max_target: Максимальная температура (String, обязательно).
* measure: Единица измерения (String, обязательно).
* color: Цвет интерфейса (String, обязательно).

Подтип climate_Variant_Cond (Кондиционер)
------------------------------------------

Управляет устройством с режимами и скоростями вентиляции. В данном подтипе присутствуют еще два массива:
с режимами работы и со скоростями. Дополнительные параметры:

* mode_command_topic: Топик для отправки режима(String, обязательно).
* mode_state_topic: Топик для получения режима(String, обязательно).
* off_payload: Сообщение для выключения(String, обязательно).
* modes: Массив с режимами. Здесь есть возможность оставить пустыми несколько полей режимов или полностью весь массив. Максимум 4 поля.

Массив с режимами::

    "modes": 
        {
            "mode_1": 
            {
                "icon": "", 
                "title": "", 
                "color": "", 
                "payload": "" 
            },
            "mode_2": 
            {
                "icon": "", 
                "title": "", 
                "color": "", 
                "payload": "" 
            },
            "mode_3": 
            {
                "icon": "", 
                "title": "", 
                "color": "", 
                "payload": "" 
            },
            "mode_4": 
            {
                "icon": "", 
                "title": "", 
                "color": "", 
                "payload": "" 
            }

        }

* currentTemp_state_topic(String, обязательно): Топик текущей температуры.
* targetTemp_command_topic(String, обязательно): Топик целевой температуры.
* targetTemp_state_topic(String, обязательно): Топик состояния целевой температуры.
* fan_command_topic(String, обязательно): Топик для управления вентилятором.
* fan_state_topic(String, обязательно): Топик состояния вентилятора.
* fan_modes: Массив со скоростями. Здесь есть возможность оставить пустыми несколько полей скорости или полностью весь массив. Максимум 5 полей.

Массив со скоростями::

    "fan_modes": 
        {
            "mode_1": 
            {
                "icon": "", 
                "payload": ""
            },
            "mode_2": 
            {
                "icon": "", 
                "payload": ""
            },
            "mode_3": 
            {
                "icon": "", 
                "payload": "" 
            },
            "mode_4": 
            {
                "icon": "", 
                "payload": ""
            },
            "mode_5": 
            {
                "icon": "", 
                "payload": ""
            }
        }

Пример::

    {
    "block": 1,
    "type": "climate",
    "data": {
        "param_1": "Конд-ер",
        "param_2": "Зал",
        "setting_name": "Кондиционер",
        "icon": "\uDB84\uDF52",
        "min_target": "15",
        "max_target": "30",
        "measure": "°С",
        "color": "color_red",
        "variant_type": "Climate_Variant_Cond",
        "variant": 
        {
            "mode_command_topic": "panel/climate/1/mode_command",
            "mode_state_topic": "panel/climate/1/mode_state",
            "off_payload": "off",
            "modes": 
                {
                    "mode_1": { "icon": "\uDB86\uDCF2", "title": "Авто", "color": "color_green", "payload": "auto" },
                    "mode_2": { "icon": "\uDB80\uDE38", "title": "Обогрев", "color": "color_red", "payload": "heat" },
                    "mode_3": { "icon": "\uDB81\uDF17", "title": "Охлаждение", "color": "color_blue", "payload": "cool" },
                    "mode_4": { "icon": "\uDB81\uDD8E", "title": "Осушение", "color": "color_yellow", "payload": "dry" }
                },
            "currentTemp_state_topic": "panel/climate/1/currentTemp_state",
            "targetTemp_command_topic": "panel/climate/1/targetTemp_command",
            "targetTemp_state_topic": "panel/climate/1/targetTemp_state",
            "fan_command_topic": "panel/climate/1/fan_command",
            "fan_state_topic": "panel/climate/1/fan_state",
            "fan_modes": 
                {
                    "mode_1": { "icon": "\uDB85\uDF1D", "payload": "0" },
                    "mode_2": { "icon": "\uDB85\uDC72", "payload": "1" },
                    "mode_3": { "icon": "\uDB85\uDC73", "payload": "2" },
                    "mode_4": { "icon": "\uDB85\uDC74", "payload": "3" },
                    "mode_5": { "icon": "", "payload": "" 
                }
            }
        }
    }
}

Подтип climate_Variant_Thermostat (Термостат)
---------------------------------------------

Управляет устройствами с регулировкой температуры или других параметров. Дополнительные параметры:

* OnOff_command_topic: Топик для включения/выключения.
* OnOff_state_topic: Топик состояния.
* payload_on: Сообщение для включения.
* payload_off: Сообщение для выключения.
* targetTemp_command_topic: Топик целевой температуры.
* targetTemp_state_topic: Топик состояния целевой температуры.
* sensor: Параметр с дополнительными датчиками. Здесь есть возможность оставить пустыми несколько полей датчиков или полностью весь массив. 
Также в параметре ``sensor_main`` указываем главный датчик, информация о котором будет отображаться в блоке на главной странице. Можно его оставить пустым. Максимум 3 поля.

Массив с датчиками::

    "sensor": 
        {
            "sensor_main": 1,
            "sensor_1_icon": "\uDB83\uDF55",
            "sensor_1_measure": "°С",
            "sensor_1_state_topic": "panel/climate/2/sensor_1_state",
            "sensor_2_icon": "",
            "sensor_2_measure": "",
            "sensor_2_state_topic": "",
            "sensor_3_icon": "",
            "sensor_3_measure": "",
            "sensor_3_state_topic": ""
        }


Пример::

    {
        "block": 2,
        "type": "climate",
        "data": 
        {
            "param_1": "Тепл. пол",
            "param_2": "Детская",
            "setting_name": "Теплый пол",
            "icon": "\uDB86\uDEAF",
            "min_target": "18",
            "max_target": "30",
            "measure": "°С",
            "color": "color_red",
            "variant_type": "Climate_Variant_Thermostat",
            "variant": 
            {
                "OnOff_command_topic": "panel/climate/2/OnOff_command",
                "OnOff_state_topic": "panel/climate/2/OnOff_state",
                "payload_on": "1",
                "payload_off": "0",
                "targetTemp_command_topic": "panel/climate/2/targetTemp_command",
                "targetTemp_state_topic": "panel/climate/2/targetTemp_state",
                "sensor": 
                {
                    "sensor_main": 1,
                    "sensor_1_icon": "\uDB83\uDF55",
                    "sensor_1_measure": "°С",
                    "sensor_1_state_topic": "panel/climate/2/sensor_1_state",
                    "sensor_2_icon": "",
                    "sensor_2_measure": "",
                    "sensor_2_state_topic": "",
                    "sensor_3_icon": "",
                    "sensor_3_measure": "",
                    "sensor_3_state_topic": ""
                }
            }
        }
    }