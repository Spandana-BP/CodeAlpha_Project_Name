<!DOCTYPE html>
<html lang="en">
<body>
    <div class="container">
        <h1>Translate Tool</h1>


   # Import the following module
import tkinter as tk  # install Tkinter
from tkinter import *
from tkinter import ttk
from PIL import ImageTk, Image  # install pillow
from googletrans import Translator  # install googletrans==3.1.0a0 , newer versions may or may not work
from tkinter import messagebox
import pyperclip as pc # install paperclip for copy function
from gtts import gTTS  # install gTTS for text to speech, speech to text functionality
import os
import speech_recognition as spr # install speech recognition for speech to text functionality

# ---------------------------------------------------Language Translator--------------------------------------------------------------
''' This python file consist of all functionalities required for the language translator application to work  '''

# UI is developed using Tkinter library
root = tk.Tk()
root.title('Langauge Translator')
root.geometry('1060x660')
root.maxsize(1060, 660)
root.minsize(1060, 660)
# Tittle bar icon image used in Tkinter GUI
title_bar_icon = PhotoImage(file="resources/icons/translation.png")
root.iconphoto(False,title_bar_icon)
cl =''
output=''

# For Performing Main Translation Function
def translate():
    language_1 = t1.get("1.0", "end-1c")
    global cl
    cl = choose_langauge.get()

    if language_1 == '':
        messagebox.showerror('Language Translator', 'Please fill the Text Box for Translation')
    else:
         t2.delete(1.0, 'end')
         translator = Translator()
         global output
         output = translator.translate(language_1, dest=cl)
         output = output.text
         t2.insert('end', output)

# For Clearing Textbox Data
def clear():
    t1.delete(1.0, 'end')
    t2.delete(1.0, 'end')

# For Copying Textbox Data after Translation
def copy():
    pc.copy(str(output))

# For Converting Translated Text to Speech
def texttospeech():
 global cl
 cl = choose_langauge.get()
 if os.path.exists("text_to_speech.mp3"):
  os.remove("text_to_speech.mp3")
 mytext =output
 language='en'
 if cl == 'English':
     language = 'en'
 elif cl == 'Afrikaans':
     language = 'af'
 elif cl == 'Albanian':
     language = 'sq'
 elif cl == 'Arabic':
     language = 'ar'
 elif cl == 'Armenian':
     language = 'hy'
 elif cl == 'Azerbaijani':
     language = 'az'
 elif cl == 'Basque':
     language = 'eu'
 elif cl == 'Belarusian':
     language = 'be'
 elif cl == 'Bengali':
     language = 'bn'
 elif cl == 'Bosnian':
     language = 'bs'
 elif cl == 'Bulgarian':
     language = 'bg'
 elif cl == 'Catalan':
     language = 'ca'
 elif cl == 'Cebuano':
     language = 'ceb'
 elif cl == 'Chinese':
     language = 'zh'
 elif cl == 'Corsican':
     language = 'co'
 elif cl == 'Croatian':
     language = 'hr'
 elif cl == 'Czech':
     language = 'cs'
 elif cl == 'Danish':
     language = 'da'
 elif cl == 'Dutch':
     language = 'nl'
 elif cl == 'English':
     language = 'en'
 elif cl == 'Esperanto':
     language = 'eo'
 elif cl == 'Estonian':
     language = 'et'
 elif cl == 'Finnish':
     language = 'fi'
 elif cl == 'French':
     language = 'fr'
 elif cl == 'Frisian':
     language = 'fy'
 elif cl == 'Galician':
     language = 'gl'
 elif cl == 'Georgian':
     language = 'ka'
 elif cl == 'German':
     language = 'de'
 elif cl == 'Greek':
     language = 'el'
 elif cl == 'Gujarati':
     language = 'gu'
 elif cl == 'Haitian Creole':
     language = 'ht'
 elif cl == 'Hausa':
     language = 'ha'
 elif cl == 'Hawaiian':
     language = 'haw'
 elif cl == 'Hebrew':
     language = 'he'
 elif cl == 'Hindi':
     language = 'hi'