**CONTENTS**
- [Setting Up](#setting-up)
  - [Postgresql](#postgresql)
    - [macOS](#macos)
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
- [Start/ Restart/ Stop Server](#start-restart-stop-server)
  - [Postgresql](#postgresql-1)
    - [macOS](#macos-3)


# Setting Up
## Postgresql
### macOS
  ```bash
  postgres -V
  ```
  - postgres = pg_ctl > psql
  - [postgres.app](https://postgresapp.com/)
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
       4. Delete preferences for Postgres.app 
         ```bash
         defaults delete com.postgresapp.Postgres2
         ```
  - [Homebrew](https://brew.sh/)
     - **Installing**
          ```bash 
          /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
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


# Start/ Restart/ Stop Server
## Postgresql
### macOS
  - Check Status
    - from ```pg_ctl```
      ```bash 
      pg_ctl status
      ```
    - from OS
      ```bash 
      sudo lsof -i:5432
      ```
    - from postgres.app GUI
  - Start
    1. ```pg_ctl```
        ```bash 
        pg_ctl -D start
        ```
      - With log writing
        ```bash 
        pg_ctl start -l <postgresql.log>
        ```
      - You can also check the ```log``` path from GUI server settings
      - <img width="400" alt="image" src="https://user-images.githubusercontent.com/73396926/200126762-d9aed930-8043-4570-a88c-2d25c4b4330e.png">

    2. postgres command
        ```bash 
        postgres -D /usr/local/pgsql/data
       ```
    3. GUI
  - Restart
    - ```pg_ctl```
        ```bash 
        pg_ctl restart
        ```

