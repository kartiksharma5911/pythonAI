import pyttsx3
import wikipedia
import datetime
import speech_recognition as sr
import webbrowser
import os
import smtplib


def detail():
    """
Author - Kartik Sharma
Date - 31/08/2022
Purpose - Program for doing task through COMMANDS
"""


print(detail.__doc__)


def audio(speak):
    engine = pyttsx3.init("sapi5")
    # v = engine.getProperty('voices')
    # engine.setProperty('voice', v[1].id)
    engine.say(speak)
    engine.runAndWait()


def wish_me():
    hour = datetime.datetime.now().hour
    if hour > 00 and hour <= 12:
        audio("Good morning Sir")

    elif hour > 12 and hour <= 17:
        audio("Good Afternoon Sir")

    else:
        audio("Good Evening Sir")

    audio("I m Your assistant Please tell me how can i help you")


def take_command():

    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 1
        audio = r.listen(source)

    try:
        print("Recognizing...")
        query = r.recognize_google(audio, language='en-in')
        print(f"User said: {query}\n")

    except Exception as e:
        # print(e)
        print("Say that again please...")
        return "None"
    return query


def send_email(to, content):
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.ehlo()
    server.starttls()
    with open("pass.txt") as f:
        c = f.read()
    server.login('kritikasharma5027@gmail.com', f'{c}')
    server.sendmail('kritikasharma5027@gmail.com', to, content)
    server.close()


def music(x):
    dir = r"C:\Users\cools\OneDrive\Desktop\testing"
    songs = os.listdir(dir)
    os.startfile(os.path.join(dir, songs[x]))


if __name__ == '__main__':

    wish_me()
    while True:
        query = take_command().lower()

        if 'wikipedia' in query:
            audio("Searching Wikipedia")
            query.replace('wikipedia', '')
            result = wikipedia.summary(query, sentences=2)
            audio(result)
            print(result)

        elif 'time' in query:
            x = datetime.datetime.now().strftime("%H:%M")
            audio(f"Sir the time is {x}")

        elif 'open google' in query:
            webbrowser.open("google.com")

        elif 'open youtube' in query:
            webbrowser.open("youtube.com")

        elif 'play music' in query:
            audio("Which Singer")
            hero = take_command().lower()

            if 'karan' in hero:
                music(0)
            elif 'gill' in hero:
                music(1)
            elif 'sidhu' or 'wala' in hero:
                music(2)
            else:
                pass

        elif 'open code' in query:
            cod = r"C:\Users\cools\AppData\Local\Programs\Microsoft VS Code\Code"
            os.startfile(cod)

        elif 'my name' in query:
            audio("Your name is Kartik Sharma,Sir")

        elif 'your name' in query:
            audio("My name is Alexa")

        elif 'how are you' in query:
            audio("I m fine ,How r u Sir")
            take = take_command()
            if 'good' or 'fine' or 'great' in take:
                audio("Great sir")

        elif 'email' in query:
            audio("To whom sir, Kartik or Arvind")
            x = take_command().lower()

            if 'kartik' in x:
                try:
                    audio("What should I say?")
                    content = take_command()
                    to = "coolsharmakartik22@gmail.com"
                    send_email(to, content)
                    audio("Email has been sent!")
                except Exception as e:
                    print(e)
                    audio("Sorry my friend. I am not able to send this email")

            elif 'arvind' in x:
                try:
                    audio("What should I say?")
                    content = take_command()
                    to = "arvindsharma5027@gmail.com"
                    send_email(to, content)
                    audio("Email has been sent!")
                except Exception as e:
                    print(e)
                    audio("Sorry my friend. I am not able to send this email")

        elif 'quit' or 'exit' or 'bye' in query:
            audio("thank you Sir")
            break
