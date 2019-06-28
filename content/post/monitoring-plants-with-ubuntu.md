+++
Categories = ["HowTo"]
title = "Monitoring a Greenhouse with Ubuntu"
Description = "How to monitor plants with the Raspberry Pi, Xiaomi plant sensors, and Ubuntu"
Tags = ["xiaomi","gardening", "plants", "ubuntu", "snaps", "raspberrypi"]
date = 2018-05-16T12:01:43+01:00
menu = "main"
image = "/media/strawberries.jpg"

+++
<div align="center"><img alt="credit: Creative Commons - ShareAlike 3.0" src="/media/strawberries.jpg"></div>

There are a wide range of solutions on the market today to help the avid gardener with their plants, some are [low tech](https://www.amazon.co.uk/MoonCity-Moisture-Monitor-Humidity-Hygrometer/dp/B06Y3DZPZX/ref=sr_1_8?ie=UTF8&qid=1522249101&sr=8-8&keywords=plant+sensor) battery-less meters designed to give you a simple view of how your plant is doing, others are much more [high-tech](https://www.growtronix.com/) (and expensive). Two of the most important variables to monitor in a greenhouse are temperature and humidity, too hot and plants start to scorch and wilt, too cold and they can be damaged, and humidity is important for a whole host of plants you may find in a greenhouse.

At home I have a modest greenhouse, at 3 metres by 1.8 meters it has just enough room to start off delicate plants early and keep the family supplied throughout the season with chillies, tomatoes, cucumbers, strawberries, herbs, and even lemons. Although I can just barely make out the digital temperature gauge hanging on the inside of the greenhouse from my office window I thought is would be much better to have a more high-tech monitoring solution. After a bit of research I came across the Xiaomi Temperature and Humidity sensor which can be bought for as little as £9 from several Chinese online retailers. The sensor itself is a small, ZigBee-based device powered by a CR2032 button cell battery and capable of detecting temperatures from -20 to 60 celsius as well as humidity, perfect for this use case. The sensor does also need the Xiaomi gateway to work but I already had one of those. Another constraint is that any device you use to read the data needs to be within ZigBee range which, admittedly is 10s of meters, not a problem here.

Xiaomi produce an Android and iOS application that you can use to read the sensor data but after the initial (required) setup I wanted to use the data elsewhere.

## Necessary Hardware and Software
<div align="center"><img alt="credit: Creative Commons - ShareAlike 3.0" src="/media/temp-sensor.jpg"></div>

The initial idea was to put together a small, dedicated, low-powered device so the obvious choice was a Raspberry Pi3. The Ubuntu MATE project produce an [https://ubuntu-mate.org/raspberry-pi/](excellent version of Ubuntu tailored for the Pi3) so a short install later followed by enabling ssh access `sudo systemctl enable ssh` I had a fresh Ubuntu environment to get started.

In addition to Ubuntu MATE I am using [MQTT](http://mqtt.org/) in the form of [Mosquitto](https://mosquitto.org/) to send messages around the network, the mihome Python bindings from [jon1012 on GitHub](https://github.com/jon1012/mihome), [InfluxDB](https://www.influxdata.com/) to store the data, and [Grafana](https://grafana.com/) to visualise it. Installing Mosquitto can be done via the snap (`sudo snap install mosquitto`) or from the .deb. Setting up InfluxDB and Grafana is a little more involved but both have great step-by-step instructions on their respective websites.

Mosquitto needs to be running as well as the mihome software that sniffs the network for ZigBee packets. With both of these in place it's just a matter of capturing the bits we are interested in and putting them in an InfluxDB database (warning, I'm no Python expert!).

~~~
import paho.mqtt.client as mqtt
import json
import sqlite3
from sqlite3 import Error
from influxdb import InfluxDBClient
import time
import datetime

broker_address="192.168.0.100"

topics = ["xiaomi/sensor_ht/158d0001ad37b7/temperature", "xiaomi/sensor_ht/158d0001ad37b7/humidity"]

def on_message(client, userdata, message):
    msg = message.payload.decode("utf-8")
    prefix, device, sid, prop = message.topic.split("/")

    rectime = datetime.datetime.utcnow()

    topic = prop + "_" + sid

    isfloatval = False

    # See if the message is a temperature or humidity data entry (float)
    try:
        val = float(msg)
        val = val / 100
        isfloatval = True

    except:
        print ("Not a temperature or humidity value")

    if isfloatval:
        json_body = [
            {
                "measurement": topic,
                "time": rectime,
                "fields": {
                    "value": val
                }
            }
        ]
        dbclient.write_points(json_body)

# Set up mqtt client
client = mqtt.Client("sensors")
client.on_message=on_message
client.connect(broker_address)
client.loop_start()

# Set up InfluxDB client
dbclient = InfluxDBClient('192.168.0.100', 8086, 'root', 'root', 'sensordata')

# Subscribe to topics
for t in topics:
    print("Subscribing to topic " + t)
    client.subscribe(t)

# Loop and wait until interrupted
try:
    while True:
        pass
except KeyboardInterrupt:
    print("interrupted by keyboard")

client.loop_stop()
~~~

The code is pretty simple. Set up the MQTT and InfluxDB clients which are both hosted on the Raspberry Pi at 192.168.0.100 and loop looking for MQTT messages that are listed in the topics array. In the code above we only have one sensor (but two topics) and the ID of the sensor was found by looking at the output of the running mihome software.

## Visualisations

<div align="center"><img alt="credit: Creative Commons - ShareAlike 3.0" src="/media/grafana-greenhouse-data.png"></div>

Once you have Grafana set up and connected to the InfluxDB database it is simple to add charts visualising the data. I opted for two charts, one for temperature and another for humidity and as you can see, here in the south of England it got pretty hot in there at the start of May, too hot in fact. I have already made modifications to the greenhouse to try cool things down when it becomes too hot but some manual intervention is still needed on the warmest of days.

To finish it all off you can use [Mir Kiosk](https://tutorials.ubuntu.com/tutorial/graphical-snaps), a small, light-weight graphical server and a small LCD display to provide an always on view of the data.

There are lots of things that can be done with the Xiaomi range of sensors, as of writing I have 9 temperature sensors around the home, smart switches on every door to monitor open/close events, and plant sensors in several indoor plants to monitor fertility, moisture, temperature, and other conditions necessary to keep them all healthy. I'll expand on this further in a future blog post.
