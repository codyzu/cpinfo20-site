---
title: Espruino Weather Station
---

# Espruino Weather Station

[Espruino](https://www.espruino.com/) is a project that combines small, powerful, and efficient microcontrollers with a JavaScript runtime.

For this course, we will use an [Espruino Wifi](https://www.espruino.com/WiFi), a [BME280 Environment Sensor](https://www.espruino.com/BME280) (temperature, humidity, and atmospheric pressure), and a [SSD1306 OLED](https://www.espruino.com/SSD1306) display. We will combine all of these components to create a weather station running JavaScript!

![weather station](./images/espruino.gif)

The weather station records the temperature, humidity, and atmospheric pressure. The data can then be used to monitor and predict the weather.

The components are combined as illustrated below:
![board](./images/board.svg)

<p align="center"><strong>CPINFO Espruino Circuit Diagram</strong></p>


## 1 Get Connected

1. Connect your Espruino board to the USB port of the computer. Wait for Windows to indicate the drivers were correctly installed.
1. Install the [Espruino Web IDE](https://chrome.google.com/webstore/detail/espruino-web-ide/bleoifhkdalbjfbobjackfdifdneehpo) and open it.
1. Connect to your Espruino board by clicking on connect icon and choosing the `Espruino` connection:
   ![Web IDE Connect](./images/ide-connect.png)
1. Click on the Run button to execute the code that is shown on the right half of the screen:
   ![Web IDE Run](./images/ide-run.png)

   You can modify the code on the right half of the screen and then click the Run button again to see the changes live. You can also execute `console.log("hello CPINFO")` to log messages and data to the console of the left half of the screen.

## 2 OLED Display

The SSD1306 OLED is a 128x64 resolution monochrome OLED display. It communicates with the Espruino using a SPI protocol. Fortunately, this is already supported by Espruino.

1. Setup the display by adding the following code to your project:
    ```javascript
    let display;
    function setupDisplay() {
      I2C1.setup({scl: B8, sda: B9});
      B7.set();
      B6.reset();
      display = require('SSD1306').connect(I2C1, start);
    }

    setupDisplay();
    display.drawString("Hello CPINFO");
    display.flip();
    ```

   The graphics library on Espruino allows changing the font, drawing lines, shapes, and much more. **See details**

1. clear() and flip()

   The Espruino [Graphics](https://www.espruino.com/Graphics) library lets us use "double buffering" to write to the display. First, we draw to a local variable (buffer) then we call the `flip()` function to write the buffer to the display. The function `clear()` clears the buffer.

1. refresh with setInterval()

   The function [setInterval()](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval) allows executing a function at regular intervals. For example:

   ```javascript
   let count = 0;
   setInterval(() => {
     console.log('The count is:', count);
     count = count + 1;
   })
   ```
### Reference

* [Espruino Graphics](https://www.espruino.com/Graphics) (includes fonts, text, shapes, and images)
* [Espruino SSD1306 OLED Driver](https://www.espruino.com/SSD1306)
* [Espruino `setInterval()`](https://www.espruino.com/Reference#l__global_setInterval)

## 3 BME280 Environment Sensor

1. Setup the environment sensor by adding the following code to your project:
    ```javascript
    let sensor;
    function setupSensor() {
      A4.reset();
      A5.set();

      console.log('Starting Temp');
      const i2c = new I2C();
      i2c.setup({scl: A1, sda: A0});
      sensor = require('BME280').connect(i2c);
    }

    const data = sensor.getData();
    console.log('Temp:', data.temp);
    console.log('Humidity:', data.humidity);
    console.log('Pressure:', data.pressure);
    ```

#### Exercise 3.1 Instead of displaying the data on the console, we should display it on the OLED dislplay! Use the `drawString()` functions to read the data from the sensor and display it on the OLED display.

#### Exercise 3.2: use setInterval to read the temperature and update the display

### Reference

* [Espruino BME280 Driver](https://www.espruino.com/BME280)

#### Bonus: Graph library to draw cool graphs!!!

### Reference

* [Espruino Graph Library](https://www.espruino.com/graph) (for drawing graphs)

## 4 Wifi

1. The following code allows connecting to a wifi access point:

TODO:
- Bring router and plug-in with cable?
- Share iphone connection?

### Reference

* [Espruino WiFi Reference](https://www.espruino.com/WiFi#using-wifi)

## 5 Server

### Reference

* [Espruino Web Server](https://www.espruino.com/Internet#server)
* [Espruino Handling POST'ed forms](https://www.espruino.com/Posting+Forms)

## Weather History
