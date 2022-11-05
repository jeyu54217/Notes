**CONTENTS**
- [Setting Up](#setting-up)
  - [Postgresql](#postgresql)
    - [macOS](#macos)
      - [postgres.app](#postgresapp)
      - [Homebrew](#homebrew)
    - [Linux (ubuntu)](#linux-ubuntu)
    - [Windows](#windows)
  - [Mysql](#mysql)
    - [macOS](#macos-1)
    - [Linux (ubuntu)](#linux-ubuntu-1)
    - [Windows](#windows-1)
  - [MongoDB](#mongodb)
    - [macOS](#macos-2)
    - [Linux (ubuntu)](#linux-ubuntu-2)
    - [Windows](#windows-2)
- [Server - Start/ Restart/ Stop](#server---start-restart-stop)
  - [Postgresql](#postgresql-1)
    - [macOS](#macos-3)


# Setting Up
## Postgresql
### macOS
  - Version Check 
    ```bash
    postgres -V
    ```
    ```bash
    brew search postgres
    ```
  - Get help
      ```bash
      pg_ctl --help
      ```
      ```bash
      brew services --help
      ```
  - postgres = pg_ctl > psql
#### [postgres.app](https://postgresapp.com/)
   - **Installing**
     1. [Download](https://postgresapp.com/downloads.html) ➜ Move to Applications folder ➜ Double Click
     2. Click "Initialize" to create a new server
     3. Configure ```$PATH``` to use CLI
         ```bash
         sudo mkdir -p /etc/paths.d && echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp
         ```
     4. Configure ```PGDATA``` to use ```pg_ctl``` (PostgreSQL server controller)
         ```bash
         export PGDATA=/Users/<user_name>/Library/Application\ Support/Postgres/<var-15>
         ```
         - You can also check the ```PGDATA``` path from GUI server settings
         - <img width="400" alt="image" src="https://user-images.githubusercontent.com/73396926/200126667-b76b7017-b81e-4057-9716-207ba5ec5433.png">

   - **Unstalling**
     1. Quit Postgres.app & drag it to the Trash
     2. Delete the data directory
         ```bash
         rm -r ~/Library/Application\ Support/Postgres
         ```
     3. Delete preferences for Postgres.app 
         ```bash
         defaults delete com.postgresapp.Postgres2
         ```
#### [Homebrew](https://brew.sh/)
   - **Installing**
     1. Setting Up Homebrew
         ```bash 
         /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
         ```
         ```bash 
         echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/<user_name>/.zprofile
         ```
         ```bash 
         eval "$(/opt/homebrew/bin/brew shellenv)"
         ```
     2. Starting brew
         ```bash 
         brew install postgresql@<version>
         ```
   - **Unstalling**
       ```bash 
       brew remove postgresql
       ```
### Linux (ubuntu)
### Windows
## Mysql
### macOS
### Linux (ubuntu)

### Windows
## MongoDB
### macOS
### Linux (ubuntu)
### Windows


# Server - Start/ Restart/ Stop
## Postgresql
### macOS
  - **Check Status**
     ```bash 
     pg_ctl status
     ```
     ```bash 
     brew services 
     ```
     ```bash 
     brew services info --all
     ```
     ```bash 
     sudo lsof -i:5432
     ```
      
  - **Start**
      ```bash 
      postgres -D /usr/local/pgsql/data
      ```
      ```bash 
      brew services start --all 
      ```
      ```bash 
      pg_ctl start
      ```
      with log writing
      ```bash 
      pg_ctl start -l <postgresql.log>
      ```
       - ```log``` path in GUI settings
       - <img width="400" alt="image" src="https://user-images.githubusercontent.com/73396926/200126762-d9aed930-8043-4570-a88c-2d25c4b4330e.png">
  - **Restart**
      ```bash 
      pg_ctl restart
      ```
      ```bash 
      brew services restart --all 
      ```
  - **Stop**
      ```bash 
      pg_ctl stop 
      ```
      ```bash 
      brew services stop --all 
      ```
      or
      ```bash 
      kill -15 -<PID> 
      ```

https://dataschool.com/learn-sql/how-to-start-a-postgresql-server-on-mac-os-x/
