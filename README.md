# brain-computer-interface

## Conda and Conda Env

Install mini conda 
	bash Miniconda3-py310_22.11.1-1-Linux-x86_64.sh

Create and activae a conda environment
	conda create -n muse_env python=3.10
	conda activate muse_env


## Muse LSL https://github.com/alexandrebarachant/muse-lsl

Install Muse LSL
	
	pip install muselsl
	
A bug in Muse LSL
muselsl is istalled in ~/opt/anaconda3/envs/muse_env/lib/python3.8/site-packages/muselsl
and there is a bug in backends.py that need to be fixed (add .handle as shown in below)

	value_handle = declaration_handle.handle + 1

Start streaming

	muselsl stream --address BBA4C136-A9F1-4EE3-1BF9-7CB055CBE223

View the EEG stream

	muselsl view

## Dino Game
	pip install pyautogui
	python blink_detection

## speechrecognition (has dependency on Pyaudio
	pip install speechrecognition

## Pyaudio
	/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
	brew install portaudio
	pip install pyaudio

## text tp speech
	pip install -U pyobjc

	pip install pyttsx3

```bash
# Python program to translate
# speech to text and text to speech


import speech_recognition as sr
import pyttsx3

# Initialize the recognizer
r = sr.Recognizer()

# Function to convert text to
# speech
def SpeakText(command):
	
	# Initialize the engine
	engine = pyttsx3.init()
	engine.say(command)
	engine.runAndWait()
	
	
# Loop infinitely for user to
# speak

while(1):
	
	# Exception handling to handle
	# exceptions at the runtime
	try:
		
		# use the microphone as source for input.
		with sr.Microphone() as source2:
			
			# wait for a second to let the recognizer
			# adjust the energy threshold based on
			# the surrounding noise level
			r.adjust_for_ambient_noise(source2, duration=0.2)
			
			#listens for the user's input
			audio2 = r.listen(source2)
			
			# Using google to recognize audio
			MyText = r.recognize_google(audio2)
			MyText = MyText.lower()

			print("Did you say ",MyText)
			SpeakText(MyText)
			
	except sr.RequestError as e:
		print("Could not request results; {0}".format(e))
		
	except sr.UnknownValueError:
		print("unknown error occurred")
```
