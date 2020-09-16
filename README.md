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

### Installing in Windows 

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

### Installing in Docker

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

### Remove from windows
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

# Hardware

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

# Connect to PLC-Siemens using Snap7

## Installing Snap7 in Windows

Install snap7 library: 
```pip install python-snap7```

Download snap7 from https://sourceforge.net/projects/snap7/files/

Search the snap7 folder for snap7.dll and snap7.lib files Copy the snap7.dll and snap7.lib into the "C:/PythonXX/site-packages/snap7 " directory:
<div align="center">
<img src="https://github.com/hoat23/IndustrialInternetOfThings/blob/master/img/w10_snap7_config.png" width="600" align="center"/>
</div>

## Installing Snap7 in SimaticIOT2040

Comming soon.

## Connecting to PLC s7-1200

###  How to configure data-blocks of PLC correctly

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

### Python example

```python
import snap7
import struct
from snap7.common import Snap7Library
from snap7.util import *

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

plc.destroy()
```

### Node-red example

Comming soon.


### Snap7 Documentation: 

- https://python-snap7.readthedocs.io/en/latest/installation.html#compile-from-source
- https://readthedocs.org/projects/python-snap7/downloads/pdf/latest/
- https://www.npmjs.com/package/node-snap7/v/0.1.2

# More Information

- Siemens-IOT2000 configuration: https://www.automation.siemens.com/sce-static/learning-training-documents/tia-portal/hw-config-iot2000/sce-014-101-hardware-configuration-iot2000edu-r1806-en.pdf
- https://www.elastic.co/es/blog/industrial-internet-of-things-iiot-with-the-elastic-stack
- https://github.com/apache/plc4x
- https://secureiot.eu/sites/default/files/SECUREIoT_D3.3-Intelligent%20Data%20Collection%20Mechanisms%20and%20APIs-First%20Version-Final_v11.pdf
- https://www.maffucci.it/wp-content/uploads/2020/02/SIMATIC_IOT2000_Setting_up_V2.1.1.pdf
