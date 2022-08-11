# Smart-Method-Iot
the sorting of the read me file :

1-Speach To textWebapp

2-turning robot arm.


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



