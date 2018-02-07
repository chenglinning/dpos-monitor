# DPoS Monitor
Current version 0.9

Currently the dpos-monitor can monitor nodes for Lisk, Lwf, Onz, Oxy and Shift

The monitor.py can:

* Ping your nodes from remote servers
* Check if the block heights of your nodes are correct.
* Check if the versions of your nodes are up to date.

Block height and versions checks can also be used to check if your node is still running.

## Prerequisites
```
sudo apt install python3-pip
pip3 install requests
```

When you get errors about an incorrect locale, it can help to use the following commands
```
export LANGUAGE=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```

## Installation
Clone the git
```
git clone https://github.com/dutchpool/dpos-monitor.git
```
* Change settings inside config.json to match your needs.
* config.json will be loaded by default, but with the parameter -c you could load another config file.
* For more information about the config please check [Configuration description](docs/Config_description.md)

## Dpos config change
For the dpos platform of your choosing, add your ip-addresses (from were you will be running monitor.py) to the config.json of the node.
```
"api": {
        "enabled": true,
        "access": {
            "public": false,
            "whiteList": [
                "127.0.0.1", "1.2.3.4"
            ]
        },
```

## Example crontab
Edit your crontab with the example below (command: crontab -e)

```
*/15 * * * * cd ~/dpos-monitor && python3 ~/dpos-monitor/remote_check.py >> ~/dpos-monitor/logs/remote_check.log 2>&1
```

## Telegram bot
dpos-monitor comes with Telegram functionality which will allow dpos-monitor to send you a message if anything requires your attention. It's very easy to set up: 
* Open Telegram and start a conversation with: <b>userinfobot</b>
* Put your ID inside config variable "chat_id". 
```
"chat_id": "12345678"
```
* Start a conversation with: <b>botfather</b>
* Say: /newbot
* Tell botfather your bot's name
* Tell botfather your bot's username
* Botfather will say "Congratulations!" and give you a token
* Put your token inside config variable "bot_key". 
```
"bot_key": "1122334455:AAEhBOweik6ad9r_QXMENQjcrGbqCr4K-bs"
```
* Edit the telegram toggle "use_telegram" (true/false)
* Start a conversation with your bot (username) to enable communication between you two

## Documentation
Read the documentation in the docs folder for more information on the config files and the monitoring dashboard

## Roadmap

* Android App as monitoring dashboard
* Push messages in Android App
* Support for more DPoS networks