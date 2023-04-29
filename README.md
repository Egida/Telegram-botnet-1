## Contents
* [Main information](#main-information)
    * [Features](#features)
    * [Api ID and Api hash](#api-id-and-api-hash)
    * [Default credentials](#default-credentials)
    * [Supported methods for adding an account](#supported-methods-for-adding-an-account)
    * [Functions](#functions)
* [How run](#how-run)
    * [Docker compose](#docker-compose)
    * [Docker compose local](#docker-compose-local)
    * [Python](#python)
* [Screenshots](#screenshots)
### Features
- Web interface (Dark and light theme, WOOOW)
- Ability to import an account using all popular methods
- Ability to select random or specific accounts to perform the function
- Ability to export account as TData
- Convenient account setting (Basic data and profile photo)
- Possibility to get a code from a telegram on the site
- Ability to configure global proxies and personal proxies for each account
- Ability to add your own list of account names
- Live logs with the ability to save them
- And many other small features

### Api ID and Api hash
You can find instructions on how to get an Api ID and Api hash [here](https://core.telegram.org/api/obtaining_api_id)

### Default credentials
By default, the website is launched on port 8080 but you can change this
```
Login: root
Password: roottoor
```

### Supported methods for adding an account
- Phone number (Will automatically create an account if it does not exist)
- Session file (Pyrogram and Telethon)
- Session string (Pyrogram)
- QR Code
- TData

### Functions
- Join groups
- Leave groups
- Reaction raid
- Spam chat
- Spam chat by channel
- Spam comments
- Spam comments by channel
- Spam PM
- Vote poll
## How run
[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/YGdHQR?referralCode=cTSsKD)
### Docker compose
- Install docker and docker-compose
- Create file docker-compose.yml
```yml
# docker-compose.yml
version: "3.9"
services:
  botnet:
    container_name: frt
    image: botnet/frt:latest
    restart: always
    volumes:
      - ./data:/data
    ports:
      - '8080:80' # any_port_you_like:8080
    depends_on:
      postgres:
        condition: service_healthy
    environment:
      DATABASE_URL: postgresql://root:secret_password@postgres/data

  postgres:
    container_name: postgres_container
    image: postgres:latest
    restart: always
    volumes:
      - ./data/postgres_data:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: data
      POSTGRES_PASSWORD: secret_password
      POSTGRES_USER: root
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U $$POSTGRES_USER -d $$POSTGRES_DB"]
      interval: 5s
      timeout: 5s
      retries: 5
```
- Run commands
```
$ docker-compose pull
$ docker-compose run -d
```

### Docker compose local
- Install docker and docker-compose
```
$ git clone git@github.com:HarismaLZT/Telegram-botnet.git
$ cd FRT
$ docker-compose build
$ docker-compose run -d
```

### Python
- Install Python 3.10+
```
$ git clone git@github.com:HarismaLZT/Telegram-botnet.git
$ cd FRT
$ python -m venv env

### Linux
$ source env/bin/activate
$ export DATABASE_URL=postgresql://root:secret_password@127.0.0.1/data

### Windows
$ .\env\Scripts\activate
$ set DATABASE_URL=postgresql://root:secret_password@127.0.0.1/data

$ pip install -r requirements.txt

$ python main.py
OR
$ uvicorn main:app --host 0.0.0.0 --port 8080
```

## Screenshots
<details><summary>Screenshots of pages</summary>
  <img src="/images/accounts.png" />
  <img src="/images/functions.png" />
  <img src="/images/tasks.png" />
  <img src="/images/task.png" />
  <img src="/images/settings.png" />
</details>
