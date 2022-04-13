# Overview


**LiBot** is a bot for Lichess. Strongly inspired by [ShailChoksi/lichess-bot](https://github.com/ShailChoksi/lichess-bot). It extends its features with a matchmaking mode where the bot automatically challenges other bots with similar ratings.
 The main idea taken from [Torom bot Li](https://github.com/Torom/BotLi) and has been made with the help of my friend.

# Maintenerce 
[Soloboy4](https://lichess.org/@/Soloboy4) and [Endogenetic Bot](https://lichess.org/@/Endogenetic-Bot)

# Heroku

### Chess Engines

- [Stockfish](https://github.com/official-stockfish/Stockfish)
- [Stockfish Multi Variant (dev)](https://github.com/ddugovic/Stockfish)
- [Fairy Sf](https://github.com/Lichess-Bot/Lichess-bot-BotLi-/blob/main/engines/fairy-sf)
- [Stockfish dev](https://abrok.eu/stockfish/builds/3ec6e1d2450183ed4975cf569b5a1286cb9d8369/linux64/stockfish_22021301_x64.zip)

### Chess polyglot Opening Books

- Allplay.bin
- Lichess-Book.bin
-  In case you want to use other book you found it in Engine folder
-  Just copy the name of the book and put in the line 10 or 11 as your choice


## How to Install on Heroku
- Import or [Fork](https://github.com/LichessBot-Coders/Lichess-Coded-Bots/fork) this repository to your Github.
- Open the `config.yml` file and insert your [API access token](https://lichess.org/account/oauth/token/create?scopes[]=bot:play&description=Lichess+Bot+Token) in to token option and commit changes over [here](/config.yml#L1).
- Install [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#download-and-install) and [create a new app](https://dashboard.heroku.com/new-app) in Heroku. <br/>
**Do note that in certain operating systems Heroku CLI doesn't get added to path automatically. If that's the case you'll have to add heroku to your path manually.**
- Run this command in cmd or powershell `heroku stack:set container -a appname`, where `appname` is replaced with your Heroku app's name.
- In heroku, in the `Deploy` tab click on `Connect to GitHub` and then click on `search` and select your fork/import of this repository.
- Now scroll down and under `Manual deploy`, click on `deploy` with the `master` branch selected. <br/> <br/>
Note: You could also `Enable Automatic Deploys` with the `master` branch selected if you would like each commit you make to get automatically and easily deployed onto your bot. It is your choice whether you'd like to Enable or Disable Automatic Deploys.
- After deploying wait for about 5 minutes till the build finishes and then in the `Resources` tab in heroku turn `worker` dynos. If you do not see any option to enable any dynos, then you'll have to wait for about 5 minutes and then refresh your page on heroku.

**You're now connected to lichess and awaiting challenges! Your bot is up and ready!**

__CAUTION:__ Be careful with matchmaking mode, lichess will rate limit you if you let it run for too long!

## Lichess OAuth
- Create an account for your bot on [Lichess.org](https://lichess.org/signup).
- **NOTE: If you have previously played games on an existing account, you will not be able to use it as a bot account.**
- Once your account has been created and you are logged in, [create a personal OAuth2 token with the "Play games with the bot API" ('bot:play') scope](https://lichess.org/account/oauth/token/create?scopes[]=bot:play&description=lichess-bot) selected and a description added.
- A `token` (e.g. `xxxxxxxxxxxxxxxx`) will be displayed. Store this in the `config.yml` file as the `token` field.
- **NOTE: You won't see this token again on Lichess, so do save it.**

## Setup Engine
Within the file `config.yml`:
- Enter the directory containing the engine executable in the `engine: dir` field.
- Enter the executable name in the `engine: name` field.
- You need to adjust the settings in `engine: uci_options` depending on your system.

## Setup polyglot opening book
To use a polyglot opening book the name of the book and the path to the book must be entered at the end of the config in the section `books`.

Several books can be entered here. In the upper area `eninge: polyglot: books` only the name of the book must be entered. In addition, different books can be used for white, black and chess960. If no specific book is defined, the `standard` book is used.

## Matchmaking mode

You can activate the matchmaking mode in your 'run.py'
To activate matchmaking remove the text that have been written there and type 
import os

os.system("python3 heroku_matchmaking.py -u")
To remove matchmaking and want to accept Challenge again remove all text  and type
import os

os.system("python3 heroku_challenges.py -u")

__CAUTION:__ Be careful with matchmaking mode, lichess will rate limit you if you let it run for too long!

## Greetings Chat ** 
__In other repo which have chat of greeting dont have matchamking but this repo have chat of greeting and matchmaking__
For chat there is a file name gami_api.py,  there is a line start with self.api.send_chat_message(self.game_id, "player",
and written the chats for greeting. Other you will understand by seeing that file.
## Acknowledgements
Thanks to the Lichess team, especially T. Alexander Lystad and Thibault Duplessis for working with the LeelaChessZero team to get this API up. Thanks to the [Niklas Fiekas](https://github.com/niklasf) and his [python-chess](https://github.com/niklasf/python-chess) code which allows engine communication seamlessly. In addition, the idea of this bot is based on [ShailChoksi/lichess-bot](https://github.com/ShailChoksi/lichess-bot) and
 [Torom bot Li ](https://github.com/Torom/BotLi) and it have been made with the help of my friend [Codingforhelp](https://github.com/codingforhelp)
## License

**LiBot** is licensed under the AGPLv3 (or any later version at your option). Check out the [LICENSE file](/LICENSE) for the full text. 
