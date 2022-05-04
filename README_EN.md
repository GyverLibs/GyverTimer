This is an automatic translation, may be incorrect in some places. See sources and examples!

# GyverTimer
Full timer based on system millis() / micros()
**WARNING, THE LIBRARY IS OUT OF DATE! USE [TimerMs](https://github.com/GyverLibs/TimerMs)**
- Millisecond and microsecond timer
- Two modes of operation:
    - Interval mode: the timer "fires" every set interval of time
    - Timeout mode: the timer "fires" once after the time has elapsed (until the next restart)
- Service functions:
    - Start
    - Stop
    - Reset
    - Proceed

### Compatibility
Compatible with all Arduino platforms (using Arduino functions)

### Documentation
The library has [extended documentation](https://alexgyver.ru/gyvertimer/)

## Content
- [Install](#install)
- [Initialization](#init)
- [Usage](#usage)
- [Example](#example)
- [Versions](#versions)
- [Bugs and feedback](#feedback)

<a id="install"></a>
## Installation
- The library can be found by the name **GyverTimer** and installed through the library manager in:
    - Arduino IDE
    - Arduino IDE v2
    - PlatformIO
- [Download Library](https://github.com/GyverLibs/GyverTimer/archive/refs/heads/main.zip) .zip archive for manual installation:
    - Unzip and put in *C:\Program Files (x86)\Arduino\libraries* (Windows x64)
    - Unzip and put in *C:\Program Files\Arduino\libraries* (Windows x32)
    - Unpack and put in *Documents/Arduino/libraries/*
    - (Arduino IDE) automaticinstallation from .zip: *Sketch / Include library / Add .ZIP library ... * and specify the downloaded archive
- Read more detailed instructions for installing libraries [here] (https://alexgyver.ru/arduino-first/#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE% D0%B2%D0%BA%D0%B0_%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA)

<a id="init"></a>
## Initialization
```cpp
// mode: MS/US
GTimer myTimer(mode);
GTimer myTimer(mode, interval);
```

<a id="usage"></a>
## Usage
```cpp
void setInterval(uint32_t interval); // set timer interval (will also start and reset timer) - interval mode
void setTimeout(uint32_ttimeout); // set the timeout for the timer (will also start and reset the timer) - timeout mode
boolean isReady(); // returns true when it's time
boolean isEnabled(); // return timer status (stopped/started)
void reset(); // reset the timer for the set period of work
void start(); // start/restart (with count reset)
void stop(); // stop the timer (without resetting the count)
void resume(); // continue (without resetting the score)

// service
void setMode(boolean mode); // setting the operating mode manually: AUTO or MANUAL (TIMER_INTERVAL / TIMER_TIMEOUT)
```

<a id="example"></a>
## Example
See **examples** for other examples!
```cpp
#include "GyverTimer.h"
GTimer myTimer(MS); // create a millisecond timer

void setup() {
  Serial.begin(9600);
  myTimer.setInterval(500); // set interval
}

void loop() {
  if (myTimer.isReady()) Serial.println("Timer!");
}
```

<a id="versions"></a>
## Versions
- v2.0 - improved timer algorithm
    - Multiple intervals
    - Protection against passes
    - Overflow protection millis()
    - Removed defines
- v2.1 - defaults returned
- v2.2 - improved stability
- v3.0
    - Operation logic is divided into interval and timeout
    - Added common class GTimer (for millisecond and microsecond timer)
    - Added the abilitystop and continue counting timer
- v3.2
    - Added isEnabled
    - Possibility not to start the timer when creating

<a id="feedback"></a>
## Bugs and feedback
When you find bugs, create an **Issue**, or better, immediately write to the mail [alex@alexgyver.ru](mailto:alex@alexgyver.ru)
The library is open for revision and your **Pull Request**'s!