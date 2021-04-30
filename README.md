# PiMoonShine
Все для автоматики Винокура на Orange PI PC+

Основано на Node-Red
18b20-mqtt - сервис опрашивающий 18b20 датчики и засылающий их в mqtt

---


## Установка Armbian на Orange PI PC+
https://www.armbian.com/orange-pi-pc-plus/

Устанавливаем Armbian Focal

Через armbian-config настраиваем сеть, доступ по ssh, timezone и т.д.

Там же в System-Hardware включаем i2c0, uart1, w1-gpio

## Установка Node-RED и необходимые пакеты
#### Заходим по SSH на OrangePi под рутом и запускаем:
bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)

apt-get update&&apt-get upgrade&&apt-get install mosquitto mosquitto-clients nginx

pip3 install paho-mqtt
pip3 install w1thermsensor

---
#### Копируем из папки 18b20-mqtt:

18b20-mqtt в /usr/local/bin/

18b20-mqtt.service в /etc/systemd/system/

#### Копируем из папки nginx:

nodered в /etc/nginx/sites-enabled/

---
#### Запускаем:
systemctl daemon-reload&&systemctl restart mosquitto 18b20-mqtt nodered nginx

## Первоначальная Настройка

Заходим через браузер на http://<ip адресс orange-pi>/

Далее в "Управление палитрой"

#### Устанавилваем узлы:
node-red-contrib-bme280

node-red-contrib-configurable-interval

node-red-contrib-mytimeout

node-red-contrib-opi-gpio

node-red-contrib-simpletime

node-red-contrib-telegrambot

node-red-contrib-ui-led

node-red-contrib-ui-svg

node-red-dashboard

node-red-node-serialport

---

Импортируем проект из PiMoonShine.json

Настриваем telegram бота под свои данные.
