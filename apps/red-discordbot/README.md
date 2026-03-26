# Red-Discordbot

## General 

I wanted a simple bot for the discord server my friends and I play on. The most important feature for me was the ability to save youtube playlists and play them and of course a simple installation. 
Redbot uses it's own plugins, which are called "cogs". They add functions and abilitys to the bot. After the default installation redbot can't play  music on it's own, fortunately the audio cog solves this problem. I will cover it's installation later. 
> ⚠️ Note: This guide will assume, that you're using a Linux-based OS (e.g. Ubuntu). Most commands used here will only work on Linux.

## Preperations 

- To be able to follow my instructions here you need the docker engine and docker compose installed. You can use the official guide for this: https://docs.docker.com/compose/install/
<br>

> You can check if the install was successfull with this command:  
> ```
> docker version && docker compose version
> ```

<br>

- The other thing we need for later, is a discord-bot-token. You can get this in the discord developer portal (https://discord.com/developers/applications). Simply create an application and go to the "bot" tab and reset the token there and copy the then given token. You also have to activate those three options: Presence Intent, Server Members Intent, Message Content Intent.

<br> 

## Installation 

### Folder environment 
- First we'll create a folder for the docker-compose-file and within another folder for it's data. This command will create a folder named "redbot" in your home directory and another "data" folder inside it. 
```
cd ~/ && mkdir redbot && cd redbot && mkdir data 
```

### Creating the service 
- Next we'll create the docker-compose-file, which will start the redbot. 
```
nano docker-compose.yaml
```
- An editor should´ve opened, where we can now paste in our service. 
```
# You can add a "networks:" section here if you want. I chose not to, so 
# docker will create a default-network for this stack. 


services:
  redbot:

    # Simply the name of the service
    container_name: redbot

    # The docker-image which will be getting pulled. You can exchange "latest" to a specific version  
    image: phasecorex/red-discordbot:latest

    # Define this volume in the .env-file 
    volumes:
      - ./data/:/data


    environment:
      # Define this in the .env-file as well. You can get this on the discord-developer-website. 
      - TOKEN=${BOT_TOKEN}
      # The prefix which the bot will listen on (e.g. ".play" or "/help")
      - PREFIX=.
      # Change this to your timezone
      - TZ=Europe/Berlin
      # The user the docker "use". Normally "PUID=1000" is your default user. 
      - PUID=1000
    
    # The service will always try to restart, except you stopped manually 
    restart: unless-stopped
```
> You might have to change some of these values, e.g. the timezone (TZ) or the PUID. 


### Creating the .env-file 

- Next we have to set some variables and create the .env-file. 
```
nano .env
```
- Now we can paste in our discord-bot-token. Paste this into the .env-file (insert your token ofc)
```
BOT_TOKEN=insert_your_bot_token_here
```
> ⚠️ If your token starts with an "$", you might have to enclose your token in quotation marks

### First start and configuration 

- Now we can start the service 
```
docker compose up -d 
```
- To invite the bot to your service, we have to look into the logs of the service and copy the link, which the service will give us 
```
docker logs -f redbot
```
- Copy the shown link into your browser and choose the discord server which you want the bot to be added to 

---   
<br>

The bot is now added and should work just fine. For me, the only purpose of this bot is to play music, so I will cover how you can activate this function.  
- The only thing missing is the audio cog, which is installed by default, however it is not "loaded". You can do that with this command in your discord server. 
```
.load audio
```
> You can view all available cogs with:  
```
.cogs 
```

---

After you did all that you have yourself a fully working discord bot. If you want to explore more functions you can check the original documentation out or type ```.help``` inside discord. Have fun!
<br>

## Credits 
Check out the original documentation: 
- https://github.com/PhasecoreX/docker-red-discordbot
- https://docs.discord.red/en/stable/


