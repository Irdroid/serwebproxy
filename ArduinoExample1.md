# What is needed #

  * Arduino device
  * Arduino IDE
  * openSSL libraries installed
  * serwebproxy

# Connect Arduino device to computer #

Connect your Arduino device to computer using USB or Bluetooth and find out which serial port uses (my bluetooth serial port is COM15). COM port should appear in Windows device manager after connection.

# Send example Arduino project to Arduino device #

In examples folder, there is file named simple\_chart\_arduino.txt. Copy & paste contents of this file to Arduino project and upload it to your device. All it does is that it send numbers to serial port (used to draw chart) and when it receives data, it outputs 'Command XX received'.

# Modify config file #

Edit windows\_binary/serwebproxy.cfg to look like this (modify to match your COM port)

```
comm_ports=15
comm_baud=9600
comm_databits=8
comm_stopbits=1
comm_parity=none
timeout=300
use_websocket15=1
net_port15=5331
serial_device15=\\.\COM15
```


# Run SerWebProxy #

Run SerWebProxy.exe (using included binary in windows\_binary folder). Console window should appear and it now waits for incoming connections.

# Open example #

Open simple\_chart.html in examples folder using Google Chrome browser. Other browsers don't support WebSocket. Click connect in example application and chart should start to appear.