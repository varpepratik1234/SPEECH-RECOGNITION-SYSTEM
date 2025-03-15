# SPEECH-RECOGNITION-SYSTEM
COMPONY: CODETECH IT SOLUTIONS

NAME: PRATIK BHASKAR VARPE

INTERN ID: CT12NUW

DOMAIN: EMBEDDED SYSTEMS

DURATION: 8 WEEKS

START DATE: 20TH JANUARY 2025

MENTOR: NEELA SANTOSH

DESCRIPTION
Project Description: Voice Recognition System
A Voice Recognition System is a technology that enables machines and devices to recognize and process human speech. It converts spoken language into a format that a computer can understand, analyze, and act upon. With advancements in Artificial Intelligence (AI) and machine learning, voice recognition has become an integral part of many modern technologies, including virtual assistants like Siri, Alexa, and Google Assistant, as well as security systems, transcription tools, and customer service applications.

Objectives and Purpose of the Project
The primary goal of a Voice Recognition System project is to develop a system that can accurately recognize and interpret human speech. This system has various use cases, such as automating tasks through voice commands, transcribing speech into text, identifying individual speakers for security purposes, or integrating it with smart devices for a hands-free experience.

Key objectives of the project include:

Accuracy: Achieving a high degree of accuracy in speech recognition, ensuring that the system can understand speech even in noisy environments or when various accents or speech patterns are involved.
Efficiency: Processing the voice commands and inputs quickly, without noticeable delays, to provide a seamless user experience.
Adaptability: The system should be able to recognize different languages, dialects, and even adapt to new words or phrases over time.
Integration: Ensuring the system can be easily integrated into existing software, mobile apps, or smart devices for wider accessibility and usability.
Core Components of the System
The design of a Voice Recognition System involves several key components and processes:

Speech Acquisition: The first step involves capturing the voice signal. This is typically done through microphones or voice-enabled devices that record the audio signal. The quality of the microphone and the clarity of the voice input play a crucial role in the system's effectiveness.

Preprocessing: The recorded voice input is then preprocessed to remove noise and irrelevant sounds. Techniques such as Noise Reduction, Echo Cancellation, and Volume Normalization are employed to improve the quality of the audio before analysis.

Feature Extraction: The system breaks down the speech into features that represent the sound and structure of the speech. For example, Mel-Frequency Cepstral Coefficients (MFCCs) are commonly used to capture the unique characteristics of speech sounds. These features allow the system to recognize speech patterns more efficiently.

Speech Recognition Algorithm: The extracted features are then fed into a machine learning algorithm or model. Common algorithms include Hidden Markov Models (HMM), Deep Neural Networks (DNN), and more recently, Convolutional Neural Networks (CNN) and Recurrent Neural Networks (RNN), which help in recognizing the spoken words and converting them into text.

Post-Processing: Once the speech is transcribed into text, post-processing techniques such as language models are applied to refine the output. This helps in understanding context and improving accuracy, especially when dealing with homophones or ambiguous terms.

Natural Language Processing (NLP): After speech has been transcribed into text, NLP algorithms can be used to further analyze the meaning, context, and intent behind the words. This is particularly important for systems designed to understand and act upon user commands, such as virtual assistants or customer service bots.

Action Execution: Once the system has recognized and processed the speech, it must take appropriate actions. This could include playing music, making a phone call, sending a message, or even controlling IoT devices like smart lights or thermostats.

Applications of Voice Recognition Systems
Voice recognition systems are used in various industries, including:

Consumer Electronics: Smart devices such as voice assistants (Amazon Alexa, Google Assistant, Apple Siri) rely on voice recognition to assist users in performing tasks like setting reminders, playing music, or checking the weather.
Healthcare: Doctors and medical professionals use voice recognition systems to transcribe patient notes or issue voice commands to medical devices, improving workflow efficiency and reducing manual data entry errors.
Automotive: In vehicles, voice recognition allows drivers to operate navigation systems, make phone calls, and control in-car entertainment systems without taking their hands off the wheel.
Security: Voice biometrics is increasingly being used in security systems to authenticate users based on their unique voice patterns, adding an extra layer of protection in high-security environments.
Customer Service: Automated voice recognition systems are widely used in call centers and customer support lines to handle routine inquiries, resolve issues, and provide efficient customer service.
Challenges in Voice Recognition Systems
While voice recognition technology has come a long way, there are still several challenges that need to be addressed:

Accents and Pronunciations: A system must be able to recognize various accents, dialects, and pronunciation variations. Failure to do so can result in inaccuracies, especially in a globalized world.
Background Noise: Voice recognition systems struggle in noisy environments where multiple people are speaking or there is a lot of ambient sound.
Language and Context Understanding: While the transcription of speech into text has improved, understanding the context and meaning behind the words remains a complex task.
Conclusion
The Voice Recognition System is a revolutionary tool that simplifies interaction with technology, creating more efficient and accessible experiences. With continuous improvements in machine learning algorithms and voice processing techniques, the accuracy and adaptability of voice recognition systems will continue to enhance, enabling a wide range of applications across industries and making it an indispensable part of our daily lives.

#CODE

#include<LiquidCrystal.h> String voice; int led1 = 7, //Connect LED 1 To Pin #7 led2 = 8, //Connect LED 2 To Pin #8 led3 = 9, //Connect LED 3 To Pin #9 led4 = 10; //Connect LED 4 To Pin #10 void turn_on() { digitalWrite(led1, HIGH); digitalWrite(led2, HIGH); digitalWrite(led3, HIGH); digitalWrite(led4, HIGH); }

   void turn_off()
   {
        digitalWrite(led1, LOW);
        digitalWrite(led2, LOW);
        digitalWrite(led3, LOW);
        digitalWrite(led4, LOW);
   }

   const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
   void setup() 
   {
    lcd.begin(16,2);
    analogWrite(6,15);

    Serial.begin(9600);
    pinMode(led1, OUTPUT);
    pinMode(led2, OUTPUT);
    pinMode(led3, OUTPUT);
    pinMode(led4, OUTPUT);
    lcd.print("Password Please");
   }
   void loop() 
    {
      // Print a message to the LCD.

      while (Serial.available()){  //Check if there is an available byte to read
      delay(10); //Delay added to make thing stable
      char c = Serial.read(); //Conduct a serial read
      if (c == '#') {break;} //Exit the loop when the # is detected after the word
      voice += c; //Shorthand for voice = voice + c
      } 
      if (voice.length() > 0) {
        Serial.println(voice);
        lcd.setCursor(0, 1);
    //-----------------------------------------------------------------------//   
      //----------Control Multiple Pins/ LEDs----------// 
           if(voice == "*turn on") 
           {
            turn_on();
            lcd.clear();
            lcd.print("Accepted");
           }  //Turn On All Pins (Call Function)
      else if(voice == "*turn off"){turn_off(); lcd.clear();lcd.print("Accepted");} //Turn Off  All Pins (Call Function)

      //----------Turn On One-By-One----------//
      else if(voice == "*TV on") {digitalWrite(led1, HIGH);lcd.clear();lcd.print("Accepted");}
      else if(voice == "*fan on") {digitalWrite(led2, HIGH);lcd.clear();lcd.print("Accepted");}
      else if(voice == "*computer on") {digitalWrite(led3, HIGH);lcd.clear();lcd.print("Accepted");}
      else if(voice == "*bedroom lights on") {digitalWrite(led4, HIGH);lcd.clear();lcd.print("Accepted");}
      //----------Turn Off One-By-One----------//
      else if(voice == "*TV off") {digitalWrite(led1, LOW);lcd.clear();lcd.print("Accepted");}
      else if(voice == "*fan off") {digitalWrite(led2, LOW);lcd.clear();lcd.print("Accepted");}
      else if(voice == "*computer off") {digitalWrite(led3, LOW);lcd.clear();lcd.print("Accepted");}
      else if(voice == "*bedroom lights off") {digitalWrite(led4, LOW);lcd.clear();lcd.print("Accepted");}
    //-----------------------------------------------------------------------// 
    voice="";}
    delay(2000); //Delay 
    lcd.print("Password Please"); //Reset the LCD display
    }
