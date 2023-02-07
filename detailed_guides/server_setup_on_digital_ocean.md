# Create the Bot on Discord

##### Create a new Bot on Discord Developer Portal
1. Go to https://discord.com/developers/applications
2. Navigate to Applications
3. Select **New Application** 
4. Name your Bot

##### Generate "<discord_bot_token>"
1. Select App (Bot)
2. Select **Bot** in the Panel
3. Click **Reset Token**
4. Copy and Save this Token

##### Toggle Intents:
On the same “Bot” page, Toggle the following Intents:
- PRESENCE INTENT
- SERVER MEMBERS INTENT
- MESSAGE CONTENT INTENT

##### Add the new Bot to your Discord Server
1. Select **OAuth2** in the Panel
2. Select **URL Generator** below that
3. Toggle Scopes
  - “bot”
  - “application.commands”
4. Toggle Bot Permissions
  - Depending on the features you want access to, you will need to toggle different Permissions.
    - For Automatic AI Moderation, **Administrator** is required
    - For /gpt converse, toggle the various **“Threads”** permissions
5. Copy the “Generated URL” below, and navigate to that URL
6. Add the bot to the Discord Server

# Aqcuire the Tokens:
- `DISCORD_TOKEN = "<discord_bot_token>"`
This is the token you generated and noted above

- `DEBUG_GUILD = "<server id>"`  # discord_server_id
On your Discord Server, right click the Server icon and “Copy ID”

- `DEBUG_CHANNEL = "<channel id>"`  # discord_chanel_id
On your Discord Server, right click on the channel you want to use for debug and “Copy ID”

- `ALLOWED_GUILDS = "<server id>,<server id>"` 
If you only have one Discord Server, you can delete the second <server id>, otherwise enter each <server id> by the same method as described above



# Setting Up Digital Ocean

##### Create the Droplet
1. Choose Region: Select the closest
2. Choose an image: Select Ubuntu 20.04
3. CPU options: Premium Intel
4. $14/mo
5. Choose Authentication Method: Password
6. Create root password: You will use this to connect to your virtual machine using SSH
7. Hostname: Give your VM a name
8. Create Droplet

##### Connect to your VM
1. On DigitalOcean, under the Projects Tab, select your Project
2. Under "Resources", in the "Droplets" section you will see your Droplet's IP Address
3. Using the IP Address of your VM, connect via SSH
4. Use the username “root” and the password you created above
5. To use Comand Line on Windows: `ssh root@{IP ADDRESS}`
  
  ###### Note: I suggest using PuTTY to connect (enter the IP address, use Port 22, connection type "SSH" and click "Open")
  

##### Get GPT3Discord and navigate to the directory
  
`git clone https://github.com/Kav-K/GPT3Discord.git`
  
`cd GPT3Discord/`

##### Install the system packages
  
`sudo apt-get update`
  
`sudo apt install software-properties-common`
  
`sudo add-apt-repository ppa:deadsnakes/ppa`
  
`sudo apt install python3.9`
  
`sudo apt install python3.9-distutils`


##### Install Pip for python3.9
  
`curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py`
  
`python3.9 get-pip.py`

##### Install project dependencies
  
`python3.9 -m pip install --ignore-installed PyYAML`
  
`python3.9 -m pip install torch==1.9.1+cpu torchvision==0.10.1+cpu -f https://download.pytorch.org/whl/torch_stable.html`
  
`python3.9 -m pip install -r requirements.txt`
  
`python3.9 -m pip install .`

##### Copy the sample.env file into a regular .env file.
  
`cp sample.env .env`

##### Edit the .env file and to enter in your API keys
  
`nano .env`

1. Replace the API keys and Discord IDs with your own (from above) 
2. Press "Ctrl + O" and then "Enter" to Save, and then "Ctrl + X" to close

##### Run the bot using screen to keep it running after you disconnect from your SSH session:
  
`screen gpt3discord`
