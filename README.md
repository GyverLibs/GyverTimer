[![Foo](https://img.shields.io/badge/Version-3.2-brightgreen.svg?style=flat-square)](#versions)
[![Foo](https://img.shields.io/badge/Website-AlexGyver.ru-blue.svg?style=flat-square)](https://alexgyver.ru/)
[![Foo](https://img.shields.io/badge/%E2%82%BD$%E2%82%AC%20%D0%9D%D0%B0%20%D0%BF%D0%B8%D0%B2%D0%BE-%D1%81%20%D1%80%D1%8B%D0%B1%D0%BA%D0%BE%D0%B9-orange.svg?style=flat-square)](https://alexgyver.ru/support_alex/)

# GyverTimer
Пполноценный таймер на базе системных millis() / micros()  
**ВНИМАНИЕ, БИБЛИОТЕКА УСТАРЕЛА! ИСПОЛЬЗУЙ [TimerMs](https://github.com/GyverLibs/TimerMs)**
- Миллисекундный и микросекундный таймер
- Два режима работы:
    - Режим интервала: таймер "срабатывает" каждый заданный интервал времени
    - Режим таймаута: таймер "срабатывает" один раз по истечении времени (до следующего перезапуска)
- Служебные функции:
    - Старт
    - Стоп
    - Сброс
    - Продолжить

### Совместимость
Совместима со всеми Arduino платформами (используются Arduino-функции)

### Документация
К библиотеке есть [расширенная документация](https://alexgyver.ru/gyvertimer/)

## Содержание
- [Установка](#install)
- [Инициализация](#init)
- [Использование](#usage)
- [Пример](#example)
- [Версии](#versions)
- [Баги и обратная связь](#feedback)

<a id="install"></a>
## Установка
- Библиотеку можно найти по названию **GyverTimer** и установить через менеджер библиотек в:
    - Arduino IDE
    - Arduino IDE v2
    - PlatformIO
- [Скачать библиотеку](https://github.com/GyverLibs/GyverTimer/archive/refs/heads/main.zip) .zip архивом для ручной установки:
    - Распаковать и положить в *C:\Program Files (x86)\Arduino\libraries* (Windows x64)
    - Распаковать и положить в *C:\Program Files\Arduino\libraries* (Windows x32)
    - Распаковать и положить в *Документы/Arduino/libraries/*
    - (Arduino IDE) автоматическая установка из .zip: *Скетч/Подключить библиотеку/Добавить .ZIP библиотеку…* и указать скачанный архив
- Читай более подробную инструкцию по установке библиотек [здесь](https://alexgyver.ru/arduino-first/#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA)

<a id="init"></a>
## Инициализация
```cpp
// mode: MS/US
GTimer myTimer(mode);
GTimer myTimer(mode, interval);
```

<a id="usage"></a>
## Использование
```cpp
void setInterval(uint32_t interval);	// установка интервала работы таймера (также запустит и сбросит таймер) - режим интервала
void setTimeout(uint32_t timeout);		// установка таймаута работы таймера (также запустит и сбросит таймер) - режим таймаута
boolean isReady();						// возвращает true, когда пришло время
boolean isEnabled();					// вернуть состояние таймера (остановлен/запущен)
void reset();							// сброс таймера на установленный период работы
void start();							// запустить/перезапустить (со сбросом счёта)
void stop();							// остановить таймер (без сброса счёта)	
void resume();							// продолжить (без сброса счёта)	

// служебное
void setMode(boolean mode);				// установка режима работы вручную: AUTO или MANUAL (TIMER_INTERVAL / TIMER_TIMEOUT)
```

<a id="example"></a>
## Пример
Остальные примеры смотри в **examples**!
```cpp
#include "GyverTimer.h"
GTimer myTimer(MS);               // создать миллисекундный таймер

void setup() {
  Serial.begin(9600);
  myTimer.setInterval(500);   // настроить интервал
}

void loop() {
  if (myTimer.isReady()) Serial.println("Timer!");
}
```

<a id="versions"></a>
## Версии
- v2.0 - улучшенный алгоритм работы таймера
    - Кратные интервалы
    - Защита от пропусков
    - Защита от переполнения millis()
    - Убраны дефайны
- v2.1 - возвращены дефайны
- v2.2 - улучшена стабильность	
- v3.0
    - Логика работы разделена на интервал и таймаут
    - Добавлен общий класс GTimer (для миллисекундного и микросекундного таймера)
    - Добавлена возможность остановить и продолжить счёт таймера
- v3.2
    - Добавлен isEnabled
    - Возможность не запускать таймер при создании

<a id="feedback"></a>
## Баги и обратная связь
При нахождении багов создавайте **Issue**, а лучше сразу пишите на почту [alex@alexgyver.ru](mailto:alex@alexgyver.ru)  
Библиотека открыта для доработки и ваших **Pull Request**'ов!
