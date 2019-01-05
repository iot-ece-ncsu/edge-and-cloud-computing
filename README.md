# Edge-and-Cloud-Computing
## MQTT Implementation using Raspberry Pi and AWS IoT<br /><br />
### Configuring AWS IoT<br /><br />
1.Sign in to the AWS IoT console using the following link: https://aws.amazon.com/iot<br />
2.Click on Get Started<br />
3.Click on Manage in the left navigation pane and then choose Things<br />
4.To proceed with registering a thing with AWS IoT, click on Create at top right corner of the page<br />
5.Click on Create a single thing<br />
6.Enter the name (say demo-thing) of thing and click Next<br />
7.Click on Create certificate to generate an X.509 certificate and key-pair<br />
8.Download the certificate for thing, public key, private key and root CA (you can choose any CA type)<br />
9.Click on Activate to activate the X.509 certificates and keys.<br />
10.Add a policy for the thing by clicking on Register Thing and then choosing Create a policy<br />
11.Enter the name of policy in Name, iot:* in Action, and * in Resource ARN. Choose Allow in Effect and then click Create<br />
12.Click on Manage and choose Things in AWS IoT Console Navigation Pane. Choose the thing you created in step 6.<br />
13.Go to Security and choose the certificate created in step 7.<br />
14.Go to certificate’s Details page by clicking on certificate<br />
15.Click on Actions on top right of the page and click on Attach policy <br />
16.Choose the policy created in steps 10 and 11 and click Attach<br />
17.Click on Secure in Navigation Plane and cli k on Certificates. Click on the certificate created earlier to ensure that the thing and policy is attached and the certificate is activated.<br />
18.Click on Test in Navigation Pane and click on Subscribe to a Topic<br />
19.Enter Subscription Topic (say demo-topic), choose Quality of Service as 0 or 1 and click on Subscribe to topic<br /> 
20.Go to Monitor in Navigation Pane to check messages published and received, successful connections and related statistics<br />
<br /><br />
### Configuring Raspberry Pi to connect with AWS IoT<br /><br />
1.Turn on the Raspberry Pi by connecting it to a power source and let it boot<br />
2.After it turns on, ensure that it is connected to internet<br />
3.Verify OpenSSL version is 1.0.1+ by typing the following commands in the Python shell:<br />
  import ssl<br /> 
  ssl.OPENSSL_VERSION<br />
4.Install the AWS IoT Device SDK for Python using any of the following methods:<br />
a)Install using git:<br />
  i.Open terminal and install git by typing: sudo apt install git-all<br />
  ii.Clone the git repository for SDK by typing: <br />
     git clone https://github.com/aws/aws-iot-device-sdk-python.git<br />
  iii.Go to the directory where repository is cloned by typing: <br />
      cd 	aws-iot-device-sdk-python<br />
  iv.Install the SDK by typing: python setup.py install<br />
b)Install by downloading the SDK:<br />
  i.Download the SDK from here: https://s3.amazonaws.com/aws-iot-device-sdk-python/aws-iot-device-sdk-python-latest.zip<br />
  ii.Unzip the package and install by typing: python setup.py install<br />
c)Install using pip:<br />
  i.Open terminal and install pip by typing: sudo apt install pip<br />
  ii.Install SDK by typing: pip install AWSIoTPythonSDK<br />
5.Copy the certificates, public key and private keys downloaded from AWS IoT Console for the device to Raspberry Pi in a directory /home/pi/demo<br />
6.Copy the AWSIoTPythonSDK directory to demo directory<br />
7.Create a file in the same directory for code of MQTT publisher - mqttpub.py<br />
<br /> <br />
## Introducing Cisco IoT Gateway into MQTT Ecosystem<br /><br />
### Steps to connect PC to Cisco IR800:<br /><br />
1.Following packages are required:<br />
  a)Stty<br />
  b)screen<br />
2.Connect the power cable to the IR800 router (port 1)<br />
2.Connect the console (mini USB) port of IR800 router to the USB port of the local PC (port 9)<br />
3.Open the terminal<br />
4.Set-up a serial port with baud rate of 9600<br />
  a)sudo dmesg | grep -i tty<br />
    It will return the USB ports emulating the serial connection. Select the 	device which is connected to USB Serial Device     converter, say ttyUSB0<br />
  b)stty -F /dev/ttyUSB0 9600 -cstopb<br />
    It will set the baud rate as 9600<br />
5.Press Enter<br />
