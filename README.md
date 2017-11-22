# Fridgebot

Symlink sink modules, you want to use, to under the *sinks*
folder and run *AlertBot.py* with Python3. For Mattermost
one needs a bit more config, help for that is included below.
Couple of sinks included can be found under *sinks-available*.

## Mattermost integration
Include following config-file in project directory:
	mattersend.conf
	
	[DEFAULT]
	url = https://mattermost.example.com/hooks/XXXXXXXXXXXXXXXXXXXXXXX
	icon = :ghost:
	username = users_name
	channel = channels_name

Install following dependencies:

	pip3 install -r requirements.txt

Start project with Python3

## Writing more sinks

The basic concept for a Fridgebot sink is simple:

1. The sink to be loaded must find itself under the *sinks* folder.
2. It must run its setup tasks, eg. opening processes into global variables,
   when the module is loaded. No code under functions inside methods like
   *setup_initialise_or_something()* but just strait below module level.
3. Its filename must end in *.py*.
4. It must implement methods *notify()* and *thanks()*. These are called
   sending notifications and thanks for closing the fridge door.
