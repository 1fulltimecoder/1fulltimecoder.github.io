---
title: "Real-Time Voice🎙️ Translator🔊"
summary: "Real-Time Voice Translator"
date: 2024-01-01
series: [Projects]
tags: [python, voice-translator]
published: true
sitemap: true
keywords: ["Real-Time Voice Translator", "Coding blog", "Computer Science"]
aliases: ["/blog/posts/real-time-voice-translator", "/real-time-voice-translator", "/blog/real-time-voice-translator"]
cover:
  image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:Real-Time Voice Translator/og-image.webp
  alt: Real-Time Voice Translator
  hiddenInList: true
  hiddenInSingle: false
---


Real-Time Voice Translator is a machine learning project that aims to provide a seamless and natural experience of cross-lingual communication. It uses deep neural networks to translate voice from one language to another in real time while preserving the tone and emotion of the speaker. It is a desktop application that supports Windows, Linux, and Mac operating systems.

The application is easy to use: simply select the languages you want to translate between and start speaking. The application will listen to your voice and provide instant translations in real-time. You can also use the application to translate conversations between two or more people.

<b>Repository Link: [github.com/SamirPaulb/real-time-voice-translator](https://github.com/SamirPaulb/real-time-voice-translator)</b>

## Dependencies

 ```<=Python3.11, gTTS, pyaudio, playsound==1.2.2, deep-translator, SpeechRecognition, google-transliteration-api, cx-Freeze```


## Getting started

1. Clone this project and create virtualenv (recommended) and activate virtualenv.
    ```bash
    # Create virtualenv
    python -m venv env
 
    # Linux/MacOS
    source env/bin/activate
    
    # Windows
    env\Scripts\activate
    ```
    
2. Install require dependencies.
    ```bash
    pip install --upgrade wheel
    
    pip install -r requirements.txt
    ```

3. Run code and speech (have fun).
    ```bash
    python main.py
    ```

## Program Flow:

![Block Diagram of Voice Translator](https://github.com/SamirPaulb/real-time-voice-translator/assets/77569653/73dd62d6-798d-4129-aff3-16d6d932a817)


## Install Windows/Linux/Mac Application [![DOWNLOAD](https://user-images.githubusercontent.com/132539454/278971282-8d676023-a03a-463c-8e55-3f0afe6e3e58.svg)](https://github.com/SamirPaulb/real-time-voice-translator/releases/latest)


I am using <a href="https://github.com/marcelotduarte/cx_Freeze/tree/main">cx_Freeze</a> to build executable file of this app. The build settings can be changed by modifying the <a href="https://github.com/SamirPaulb/real-time-voice-translator/blob/main/setup.py">setup.py</a> file.

##### Build installer containing all the files:
- Windows: ```python setup.py bdist_msi```
- Linux: ```python setup.py bdist_rpm```
- Mac: ```python setup.py bdist_mac```


### GUI 
![App GUI](https://github.com/SamirPaulb/real-time-voice-translator/assets/77569653/f96a4115-a88f-4096-9a00-954b8527d872)
