# Industrial Internet of Things - (Siemens&ElasticStack)
Documentation about me experience connecting a PLC to cloud (OT/IT).

<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/loops_control_industries.png" width="600" align="center"/>
</div>

The architecture specifies a five-step process:
- Step 1 Data Collection: Security related information is collected from the probes, including
system level and application level probes as specified in the architecture.
- Step 2 Routing: Security information is routed to data stores and data analytics engines at
either the data collection or the security intelligence layer of the architecture.
- Step 3 Analyze: Security information is analyzed towards identifying patterns based on rules
or other data-driven mechanisms (e.g., classification).
- Step 4 Control & Actuate: Upon the identification of a specific behavior or event (e.g.,
fulfilment of rules or classification of information) the probes are reconfigured in order to
adapt the data collection.
- Step 5 Visualize: The entire intelligent and adaptive data collection process can be monitored
and controlled in a visual fashion, based on proper dashboards.

## Communication protocols

Every vendor use a specific protocol:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/vendor_brand_specific_protocol.png" width="600" align="center"/>
</div>

Also, exists open protocols:

<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/open_stantard_protocols.png" width="600" align="center"/>
</div>

# IT/OT Achitecture

The Siemens IOT2040 module is the one that allows to link the industrial plant to the cloud, for security reasons it will only send data to the cloud, but it will leave the control of the industrial processes to the internal PLC.

Elasticsearch is a non-relational database, which will store the data sent from the industrial plant. 

<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/architecture_ITOT.png" width="600" align="center"/>
</div>

Kibana or Power BI is used to generate reports, some examples of generated dashboards are:


<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/iiot-canvas-dashboards-blog.gif" width="600" align="center"/>
</div>

# Why ElasticStack for IoT Analytics Platform
While specific requirements of a platform varies between organisations, developing a platform which serves real-time operational use cases must address these seven key criteria.

- [x] Raw Data Processing
- [x] Real-Time Aggregation
- [x] Auto-Scaling Datastore
- [x] Data Lifecycle Management
- [x] Real-Time Alerting
- [x] Self-Service Visualisation
- [x] Application Monitoring

The Elastic Stack comprises of a suite of open source products that enable users to take data from anywhere and search, analyse and visualise it in real-time.

Example of use case for monitoring temperature anomaly: https://blog.codecentric.de/en/2019/10/apache-plc4x-elasticsearch-iiot-monitoring-anomaly-detection/

# Software

## Node-Red

<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/node_red_flow_example.gif" width="600" align="center"/>
</div>

### Deploying in Windows 

* Download and install nodejs from: https://nodejs.org/en/
* Check version using this command: ```node -v```
* Install node-red: ```npm install -g --unsafe-perm node-red```
* Launch node-red server, execute: ```node-red```

If you have nvm:
* ```nvm install [VERSION-NODE]```
* ```nvm use [VERSION-NODE]```


Upgrading npm:
* ```npm install npm@latest -g```
* ```npm install --global --production windows-build-tools```

Versions:
 - Node-RED version: 1.1.3
 - Node.js version: 12.18.2
 - npm version: 6.14.5

#### Remove from windows
* Run this command: npm cache clean --force
* Uninstall from Programs & Features with the uninstaller.
* Reboot (or you probably can get away with killing all node-related processes from Task Manager). Look for these folders and remove them (and their contents) if any still exist. Depending on the version you installed, UAC settings, and CPU architecture, these may or may not exist:
  * C:\Program Files (x86)\Nodejs
  * C:\Program Files\Nodejs
  * C:\Users\{User}\AppData\Roaming\npm (or %appdata%\npm)
  * C:\Users\{User}\AppData\Roaming\npm-cache (or %appdata%\npm-cache)
  * C:\Users\{User}\.npmrc (and possibly check for that without the . prefix too)
  * C:\Users\{User}\AppData\Local\Temp\npm-*
  * Check your %PATH% environment variable to ensure no references to Nodejs or npm exist.
* If it's still not uninstalled, type where node at the command prompt and you'll see where it resides -- delete that (and probably the parent directory) too.
* Reboot, for good measure.

### Deploying in Simatic-IoT2040

Comming soon

### Deploying in Docker

We create a file 'docker-compose.yml' with this content:

```
version: '3'
services:
	mosquitto:
		image: eclipse-mosquitto
		ports:
		  - 1883:1883
		  - 9001:9001
	
	nodered:
		image: cpswan/node-red
		ports:
		  - 1880:1880
``` 
A video explanation see: https://www.youtube.com/watch?v=KJXU0PL1oNM

### Deploying in IBM-Cloud.

1. Create an account in https://cloud.ibm.com/login
2. Logging in IBM-Cloud.
3. On IBM-Console type "node-red app" and click on butoon.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_01.png" width="600" align="center"/>
</div>
4. Wait by load.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_02.png" width="600" align="center"/>
</div>
5. Type the data required and click on create.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_03.png" width="600" align="center"/>
</div>
6. Click on "Desplegar su aplicación".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_04.png" width="600" align="center"/>
</div>
7. Configurate the api-key.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_05.png" width="600" align="center"/>
</div>
8. Click on own name server, that defined preview.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_06.png" width="600" align="center"/>
</div>
9. Wait by finish deploying. After, click on "view console".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_07.png" width="600" align="center"/>
</div>
10. Lauch application doing click on "visit url of the app".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_08.png" width="600" align="center"/>
</div>
11. Click on "next". Create a username and password, like below:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_09.png" width="300" align="center"/>
</div>
12. Click on "Next" and after click on "Finish". Wait by applying the settings.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_10.png" width="300" align="center"/>
</div>
13. Click on "Go to node-red flow editor".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_11.png" width="600" align="center"/>
</div>
14. Write you username and pasword created in eleven step and click on "Login".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_12.png" width="400" align="center"/>
</div>
15. Now you can use the "node-red".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/ibmcloud_13.png" width="600" align="center"/>
</div>

#### IBM Documentation
- https://developer.ibm.com/tutorials/how-to-create-a-node-red-starter-application/
- https://flows.nodered.org/

# Broker MQTT 

## When you need a broker-mqtt?
- When you have two or more sucriptors controlling multiple devices.
- When you bandwidth are bad and with problems of comunications.
- Not need, when you only reading data from devices (by monitoring).

## Online Broker-MQTT

<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/brokers_oit.png" width="400" align="center"/>
</div>

Link with differents brokers online: https://mntolia.com/10-free-public-private-mqtt-brokers-for-testing-prototyping/

## Configuration a broker in Shiftr.io
We used broker online like "shiftr.io" for fast deployment. For configurate just follow the next steps:
1. Create account in shiftr.io using your email.
2. Login with you account in shiftr.io.
4. Create a new-namespace.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/create_new_namespace_shiftr.png" width="230" align="center"/>
</div>
5. Fill the white spaces.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/create_broker_mqtt_shiftr.png" width="400" align="center"/>
</div>
6. Create a token clicking on "Namespace settings".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/create_token_shiftr.png" width="400" align="center"/>
</div>
7. Wait by load, and after clink on "Add Token".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/add_token_shiftr.png" width="400" align="center"/>
</div>
8. Type the username and password token.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/typing_usr_pasw_token_shiftr.png" width="400" align="center"/>
</div>
9.You can write data to broker-mqtt using a similar configuration: (mqtt://mykeyusername:mysecretpassword@broker.shiftr.io)
  - Server: broker.shiftr.io
  - User: mykeyusername
  - Password: mysecretpassword
  - Port: 1883
  - Protocol: mqtt

# Hardware

<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/photo_plc_iot.jpg" width="500" align="center"/>
</div>

## Simatic S7-1200

### Some Details

- RAM memory 100 [kB] (work)
- ROM memory 4 [MB]
- Remmant memory 10 [kB]
- E/S local integrated 14E/10S (Discret)
- 2E/2S (Analog)
- Image memory of process 1024 [bytes]
- Labels area 8192 [bytes]
- Ampliation Slots of signals module 8
- Ampliation Slots of comunication module 3
- High counters (HSC) 6
- Pulse generators 4
- PROFINET ports 2 (Ethernet)

## Simatic IOT2000

### Some Details

- MicroSD card is needed for the operating system with a minimun of 2GBytes.
- Connection for the power supply (24 V).
- COM interfaces (RS232/422/485)
- Ethernet interface 10/100 Mbps.
- USB type Micro-B.
- USB type A.

### Hardware and software required

* Engineering Station: Requirements are hardware and operating system (for additional information, see Readme on the TIA Portal Installation DVDs)
* SIMATIC STEP 7 Professional software in TIA Portal V15 or higher
* Software for writing the example image on the SD card, e.g. Win32 Disk Imager
* Software for SSH access, e.g. PuTTY
* Software for SFTP/SCP file transfer, e.g. WinSCP
* SIMATIC IOT2000 controller, e.g. IOT2040 with MicroSD Card and IO-Shield https://support.industry.siemens.com/cs/document/109741799/imagen-ejemplo-para-la-sd-card-de-un-simatic-iot2020-iot2040?dti=0&lc=es-AR (Yocto Linux Operating System).
* Ethernet connection between the engineering station and controller
* SIMATIC IOT2000EDU Software Controller executable on IOT2020 and IOT2040

# Connect to PLC-Siemens

##  How to configure data-blocks of PLC S7-1200 correctly

In order to correctly read the data from the plc, the following steps must be followed.

1. Enable PUT/GET
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_01.PNG" width="400" align="center"/>
</div>
2. Configure IP of PLC
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_02.PNG" width="400" align="center"/>
</div>
3. Add a new data-block
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_03.PNG" width="200" align="center"/>
</div>
4. Write name of data-block (example: IOT) and set manually the direction of block (in this case is 10)
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_04.PNG" width="400" align="center"/>
</div>
5. Define the variables, like this:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_05.PNG" width="700" align="center"/>
</div>
6. Open properties of this data-block:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_06.png" width="400" align="center"/>
</div>
7. Disabled "optimized block access"
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_07.PNG" width="400" align="center"/>
</div>
8. Compile the data-block, doing click in "compile" button.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_08.PNG" width="700" align="center"/>
</div>
9. Whait by finish of compilation.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_09.PNG" width="400" align="center"/>
</div>
10. Now you can see the direction in memory of every variable defined in data-block.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/plc_10.PNG" width="700" align="center"/>
</div>

## Python - PLC S7-1200

### Installing Snap7 in Windows

Install snap7 library: 
```pip install python-snap7```

Download snap7 from https://sourceforge.net/projects/snap7/files/

Search the snap7 folder for snap7.dll and snap7.lib files Copy the snap7.dll and snap7.lib into the "C:/PythonXX/site-packages/snap7 " directory:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/w10_snap7_config.png" width="600" align="center"/>
</div>

### Installing Snap7 in SimaticIOT2040

Comming soon.

### Python Code

```python
import snap7
import struct
import logging
from snap7.common import Snap7Library
from snap7.util import *

logging.basicConfig(level=logging.INFO)

# If you are using a different location for the library
Snap7Library(lib_location='C:/snap7/snap7.dll')
load_library() #Testing library is correctly <WinDLL 'C:\snap7\snap7.dll', handle 7ff9d5d90000 at 0x1a5a0417640>

plc = snap7.client.Client()
plc.connect("10.112.115.10",0,1)

#---Read DB--- 
# DB:10, start:0, size:8
db = plc.db_read(10,0,8)
real = struct.iter_unpack("!f",db[:6] )
print( "3 x Real Vars:", [f for f, in real] )
print( "3 x Bool Vars:", db[1]&1==1, db[2]&2==2, db[3]&4==4 )

#---Write ---
value_1 = 0b10110001
value_2 = 480
print("write 0b10110001 to V10")
plc.write("V10", value_1)
plc.write("V10.2", 0)

VW20 = plc.read('VW20')
print("VW20 : {0}".format(VW20))

plc.destroy()
```

### Snap7 Documentation: 

- https://python-snap7.readthedocs.io/en/latest/installation.html#compile-from-source
- https://readthedocs.org/projects/python-snap7/downloads/pdf/latest/
- https://www.npmjs.com/package/node-snap7/v/0.1.2

## Node-Red

### Connecting Node-Red with Broker-MQTT

A usually architecture in IoT is connect a "localhost" with a "broker" using a "node-red" like a intermediary.

<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/nodered_shiftr_ibmcloud.png" width="700" align="center"/>
</div>

#### Send data to Broker-MQTT
1. Search by MQTT nodes, it's like this:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_01.png" width="120" align="center"/>
</div>
2. Click on "mqtt in", drag and drop in workspace. After double click in this node for set the configuration:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_02.png" width="400" align="center"/>
</div>
3. Fill the configuration using the broker configuration preview created. Write server "broker.shiftr.io", port "1883", and client ID "hoat23".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_03.png" width="400" align="center"/>
</div>
4. Fill the security configuration, for this case user: "mykeyusername" and password: "mysecretpassword".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_04.png" width="400" align="center"/>
</div>
5. Set node-name to "shiftr-io-hoat23" and click on "Update". After write in topic, QoS and Retain similar to this image:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_05.png" width="400" align="center"/>
</div>
6. Click on "Done". If that configuration is rigth you would see "connected" and green rectangle in "mqtt node".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_06.png" width="600" align="center"/>
</div>

#### Receiving data from Broker-MQTT
Similar to before, just follow this steps:
1. Search by MQTT nodes, it's like this:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_01.png" width="120" align="center"/>
</div>
2. Click on "mqtt out", drag and drop in workspace. After double click in this node for set the configuration:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_07.png" width="400" align="center"/>
</div>
3. Fill the configuration using the broker configuration preview created. Write server "broker.shiftr.io", port "1883", and client ID "IBM-Cloud".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_08.png" width="400" align="center"/>
</div>
4. Fill the security configuration, for this case user: "mykeyusername" and password: "mysecretpassword".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_09.png" width="400" align="center"/>
</div>
5. Set node-name to "shiftr-io-hoat23" and click on "Update". After write in topic, QoS and Retain similar to this image:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_10.png" width="400" align="center"/>
</div>
6. Click on "Done". If that configuration is rigth you would see "connected" and green rectangle in "mqtt node".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_11.png" width="600" align="center"/>
</div>

Finally, in brocker-shiftr we can see the 2 modules connecting, like image below:

<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_mqtt_12.png" width="400" align="center"/>
</div>

"Hoat23" is a localhost, this recollecting data and "IBM-Cloud" receiving the data.

### Connecting Node-Red with PLC S7-1200

#### Installing S7 nodes
1. Go to "Manage palete".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_s7_01.png" width="400" align="center"/>
</div>
2. Search by "node-red-contrib-s7" and click on "Install".
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_s7_03.png" width="400" align="center"/>
</div>
3. Click on install again.
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_s7_04.png" width="340" align="center"/>
</div>
4. Wait by installing. If don't have error, now can use the s7 nodes
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/steps/nodered_s7_05.png" width="120" align="center"/>
</div>

#### Read data from S7-1200
Comming soon.
#### Write data on S7-1200
Comming soon.

# More Information

- Siemens-IOT2000 configuration: https://www.automation.siemens.com/sce-static/learning-training-documents/tia-portal/hw-config-iot2000/sce-014-101-hardware-configuration-iot2000edu-r1806-en.pdf
- https://www.elastic.co/es/blog/industrial-internet-of-things-iiot-with-the-elastic-stack
- https://github.com/apache/plc4x
- https://secureiot.eu/sites/default/files/SECUREIoT_D3.3-Intelligent%20Data%20Collection%20Mechanisms%20and%20APIs-First%20Version-Final_v11.pdf
- https://www.maffucci.it/wp-content/uploads/2020/02/SIMATIC_IOT2000_Setting_up_V2.1.1.pdf
