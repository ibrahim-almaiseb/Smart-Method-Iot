# Smart-Method-Iot
Speach To textWebapp
1. Create a project on the Google Cloud Platform and enable the 'Cloud Speech-to-Text API' for the project.

2. Create and download a service account key using the guide in the link below:

	https://cloud.google.com/docs/authentication/getting-started

3. Add the full path to the create service key in the HomeController ProcessAudioRecording method:

	Line 35: Environment.SetEnvironmentVariable("GOOGLE_APPLICATION_CREDENTIALS", @"<path-to-service-key>");

Users can record audio on the front-end, and once they have stopped their recording a fetch request is made to the 'ProcessAudioRecording' action in the AudioController class.
The controller action uses the Speech-to-Text API to get the text transcription of the user's audio recording and return the result to the user.
////
