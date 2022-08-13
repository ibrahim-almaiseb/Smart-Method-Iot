# Smart-Method-Iot
the sorting of the read me file :

1-Speach To textWebapp

2-turning robot arm.

3.POST and GET from database

4.Control robot movement using a website


Speach To textWebapp
1. Create a project on the Google Cloud Platform and enable the 'Cloud Speech-to-Text API' for the project.

2. Create and download a service account key using the guide in the link below:

	https://cloud.google.com/docs/authentication/getting-started

3. Add the full path to the create service key in the HomeController ProcessAudioRecording method:

	Line 35: Environment.SetEnvironmentVariable("GOOGLE_APPLICATION_CREDENTIALS", @"<path-to-service-key>");

Users can record audio on the front-end, and once they have stopped their recording a fetch request is made to the 'ProcessAudioRecording' action in the AudioController class.
The controller action uses the Speech-to-Text API to get the text transcription of the user's audio recording and return the result to the user.

///////////////////////////////////////////////////////////////////////////////////////////////////////


turning robot arm:

// 1. modify the SSID and Password below to match your WiFi router details

String ssid_sta = "SAMJI";
String pass_sta = "ELECTRICAL12";

// 2. assign a fixed/static IP to your ESP32 to bypass DHCP IP,

IPAddress local_IP(192, 168, 1, 200);

// 3. Compile and Upload the code to the ESP32

// 4. go to Chrome browser in your mobile phone/PC, type in  "chrome://flags/" NO QUOTES

// dev panel will show up, inside the text box/area just under "Insecure origins treated as secure" type in the ESP32 IP you just modified above

// eg : http://192.168.1.200  and then choose "Enabled" next to it, save if prompted to save, or relauch the chrome if prompted

// you can close the Chrome

// 5. Now connect your phone/PC to the same router as ESP32, so your phone/PC will be on the same network with the ESP32


// 6. Open up Chrome again, and visit  http://192.168.1.12 to open a portal that ESP32 hosts

// if all is good the page will be rendered and prompts you to grant microphone access to it, click yes

// 7. start to speak , and the text will show up on serial monitor on Arduino IDE

// 8. here is the command to turn arm left, you can modify it

String leftTurnCommand = "motor left";

// 8. here is the command to turn arm right, you can modify it

String rightTurnCommand = "motor right";

// 9. see function called controlRobotArm()

// that's where your spoken speech-converted to text is being compared against two pre-defined commands above to turn the robotic arm

// 10. the variable that actually carries the command text is: textReceived


///////////////////////////////////////////////////////////////////////////////////////
## Task 3: POST and GET from database:
In this task we will have a ESP32 with dht11 sensor (temperature & humidity sensor).
we will read the temperature and humidity values and send it to MYSQL database, then we will get data from the database and display the values to a website.
Note: we can collect any type of data from any sensor and send it to the database.

Pre-requisites:
To be able to send and get data from MYSQL database we have to install MYSQL database, you can use XAMPP which is an open-source cross-platform web server.

Explanation Walkthrough:
1.After installing XAMPP create a folder named "sensors" in xampp path xampp>htdocs

2.Copy the two files in Task3, insert_temp.php and getSensorValues.php to sensors folder

3.connect dht sensor to the ESP32 like this circut
![image](https://user-images.githubusercontent.com/109418411/184507230-bc795580-20d0-4eef-ae67-aeac3ef15536.png)

4.Before uploading the code DHT_MYSQL.ino in Task3 folder, make sure to change the ssid and password to your WiFi

5.In phpMyAdmin, create a database named "esp32", then create a table named "dht" with values shown in below image
![image](https://user-images.githubusercontent.com/109418411/184507300-fe2467c3-2342-4666-9c1f-6f2ed7e4ceea.png)

6.Now power ON the ESP32 and use the index.html and app.css files in Task3 to test it.

7.Let the ESP32 run for few minutes to send data to MYSQL database, and as you can see database now have temperature and humidity data as shown below: 
![image](https://user-images.githubusercontent.com/109418411/184507324-090150e2-1b7d-451b-ac09-d2392053bfa1.png)

8.the website should GET these data from the database and display it (display last added row) as shown below:

![image](https://user-images.githubusercontent.com/109418411/184507348-4da71be8-b180-4e14-95d3-9866b7f6ef1e.png)

///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////


Task 4: Control robot movement using a websiteControl robot movement using a website:

In this task we have made a website with buttons to control the robot, either move forward/backward or turn right/left
![image](https://user-images.githubusercontent.com/109418411/184507449-cf726c8a-ab2e-4de4-9057-1203cd1ea3ac.png)

The way this work, we made a new table name "movement" in the database, similar to Task3, and the ESP32 code Movement.ino in Task4 will read the data from the database frequently using GET method.
when the user click the forward button, the website will send "forward" to the database and ESP32 will read it to move forward, and when the user click the right button, we will send "right" to the database and ESP32 will also turn right.
![image](https://user-images.githubusercontent.com/109418411/184507463-44ce0b4f-8fce-419c-9afa-0b1c621a2f5a.png)


As you see in the image above, we also register how long did the user pressed the button, he clicked the forward button for 3.3 seconds and clicked the right button for 1.6 seconds. This is useful later if we want the robot replay what the user clickd before.


