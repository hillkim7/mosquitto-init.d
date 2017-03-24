Fail-safe mosquitton init.d script for Ubuntu
====================================

There is a segmentation fault while mosquitto is running with websockets
on the "Ubuntu 16.04.2 LTS".  
You could refer [Segfault using Mosquitto websockets] issue on this subject.  
To overcome this situation, this shell script restarts the mosquitto
using the nodejs forever package whenever it is suddenly dead.
## Linux Environment
* Ubuntu 16.04.2 LTS 64bit

### Installation Procedure
* mosquitto installation
```sh
$ sudo apt-get install mosquitto
```
* Remove /etc/init.d/mosquitto for replacing it from this repository
```sh
$ sudo /etc/init.d/mosquitto stop
$ cd /etc/init.d/
$ sudo update-rc.d mosquitto remove
```
* Copy Fail-save mosquitto from this repository
```sh
$ cd <repository-download-dir>
$ sudo cp mosquitto-forever /etc/init.d/
$ sudo sudo cp mosquitto-forever.sh /etc/mosquitto/
$ cd /etc/init.d/
$ sudo update-rc.d mosquitto-forever defaults
```
* Setup nodejs [forever] package
```sh
$ sudo apt-get install nodejs -y
$ sudo npm install -g forever
```
* Run and check mosquitto
```sh
$ sudo /etc/init.d/mosquitto-forever start
$ sudo /etc/init.d/mosquitto-forever status
```
## License

This software is released under the [Apache 2.0 License][apache2_license].

© 2017 Altoran System. All rights reserved

[forever]: https://www.npmjs.com/package/forever
[Segfault using Mosquitto websockets]: https://github.com/eclipse/mosquitto/issues/303
