---
title: Espruino Weather Station
---

# Espruino Weather Station

[Espruino](https://www.espruino.com/) is a project that combines small, powerful, and efficient microcontrollers with a JavaScript runtime.

For this course, we will use an [Espruino Wifi](https://www.espruino.com/WiFi), a [BME280 Environment Sensor](https://www.espruino.com/BME280) (temperature, humidity, and atmospheric pressure), and a [SSD1306 OLED](https://www.espruino.com/SSD1306) display.

The components are combined as illustrated below:
![board](./images/board.svg)
**CPINFO Espruino Circuit Diagram**

## 1 Get Connected

1. Connect your Espruino board to the USB port of the computer. Wait for Windows to indicate the drivers were correctly installed.
1. Install the [Espruino Web IDE](https://chrome.google.com/webstore/detail/espruino-web-ide/bleoifhkdalbjfbobjackfdifdneehpo) and open it.
1. Connect to your Espruino board by clicking on connect icon and choosing the `Espruino` connection:
   ![Web IDE Connect](./images/ide-connect.png)
1. Click on the Run button to execute the code that is shown on the right half of the screen:
   ![Web IDE Run](./images/ide-run.png)

   You can modify the code on the right half of the screen and then click the Run button again to see the changes live. You can also execute `console.log("hello CPINFO")` to log messages and data to the console of the left half of the screen.

## 2 OLED Display