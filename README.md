# Personal Assistant
This is a Python-based personal assistant which can process user voice and perform various tasks based on the user's input.

## Features
The personal assistant can perform the following tasks based on user's voice input:

1. Open a website on the internet (e.g., "Hey open website"), It will open the website in system default web browser.
2. Play audio (e.g., "Play audio"), It ill play music randomly from the directories configured in configuration.csv
3. Tell the current time (e.g., "What is the time"), It will inform you the current time.
4. Launch a specified application (e.g., "Start appname"), it will start the application installed in the machine.
5. Send an email to a specific contact (e.g., "Send email to contactname"), It will send email to correspondence email of the contact name configured in contact.csv
6. Quit the program (e.g., "Quit"), It will quite the program

## Usage
To use the personal assistant, follow these steps:

Clone the repository and install the necessary dependencies (python modules).
Run the personal_assistant.py script using a Python interpreter.
Speak your command to the personal assistant and it will perform the task accordingly.

## Configuration
### Preparation
- configuration_encrypted.csv <br>
  - **Step-1** <br>
    Update below information in configuration.csv <br>
    `Name` <br>
    `Email` <br>
    `Password` <br>
    `audio` <br>
  - **Step-2** <br>
generate configuration_encrypted.csv by encrypting the configuration.csv <br>
you can follow these steps: <br>
 Import the necessary modules: <br>
`from cryptography.fernet import Fernet` <br>
Generate a new Fernet key: <br>
`key = Fernet.generate_key()` <br>
Save the key to a file: <br>
`with open('key.key', 'wb') as key_file:` <br>
    `key_file.write(key)` <br>
Load the key from the file: <br>
`with open('key.key', 'rb') as key_file:` <br>
    `key = key_file.read()` <br>
Initialize a Fernet object using the key: <br>
`fernet = Fernet(key)` <br>
Read the contents of the file configuration.csv: <br>
`with open('configuration.csv', 'rb') as file:` <br>
    `original = file.read()` <br>
Encrypt the file contents: <br>
`encrypted = fernet.encrypt(original)` <br>
Write the encrypted data to a new file: <br>
`with open('configuration_encrypted.csv', 'wb') as encrypted_file:` <br>
    `encrypted_file.write(encrypted)` <br>
    
    Note that the Fernet module uses symmetric encryption, meaning that the same key is used for both encryption and decryption. Therefore, you will need to keep the key file safe and secure in order to be able to decrypt the file later. <br>
  - **Step-3** <br>
    Remove configuration.csv:
- contacts.csv <br>
Update the contacts.csv with name and correspondence email address.

At the end, root folder should have below files;
1. main.py (python program)
2. key.key (generated in step-2 of above step)
3. configuration_encrypted.csv (generated in step-2 of above step)
4. contacts.csv (updated in above step)

### Install Dependencies (Python Imports)
- `from cryptography.fernet import Fernet` - Decrypting the email id password and other user details from configuration_encrypted.csv.
- `import datetime` - To check current time
- `from time import sleep` - To manage sleep
- `from pyttsx3 import init` - To use sapi and its properties to get list of installed voices
- `from speech_recognition import Recognizer, Microphone` - To use voice engine to recognize voice
- `from webbrowser import open` - To access browser
- `from os import listdir, startfile, path` - To use system properties
- `from random import randint` - To generate random number
- `from subprocess import Popen, PIPE, STDOUT` - To run window commands
- `from smtplib import SMTP` - To access SMTP to send emails
- `from email.mime.text import MIMEText` - To format so can use subject, etc

## Disclaimer
This personal assistant is a basic implementation and may not have the full functionality of a commercial product. Use it at your own risk.
