# smart_shutdown
shut down your system with voice !!!
import speech_recognition as sr
import os

class VoiceAssistant:
    def __init__(self):
        self.recognizer = sr.Recognizer()

    def takeCommands(self):
        with sr.Microphone() as source:
            print("Listening...")
            self.recognizer.pause_threshold = 1
            audio = self.recognizer.listen(source)
            try:
                print("Recognizing...")
                query = self.recognizer.recognize_google(audio, language='en-in')
                print(f"You said: {query}\n")
                if "shut down" in query.lower():
                    os.system("shutdown /s /t 1")
            except Exception as e:
                print(e)
                print("Unable to Recognize your voice.")
                return "None"
            return query

if __name__ == '__main__':
    assistant = VoiceAssistant()
    assistant.takeCommands()

while True:
        assistant.takeCommands()
        
                     
