# Setting Up
## Postgresql

### macOS
  ```bash
          psql -version
  ```
  - [postgres.app](https://postgresapp.com/)
     - Installing
       1. [Download](https://postgresapp.com/downloads.html) ➜ Move to Applications folder ➜ Double Click
       2. Click "Initialize" to create a new server
       3. Configure your $PATH to use the included command line tools
         ```bash
          sudo mkdir -p /etc/paths.d && echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp
         ```
     - Unstalling
       1. Quit Postgres.app & drag it to the Trash
       2. Delete the data directory
         ```bash
          rm -r ~/Library/Application\ Support/Postgres
         ```
       4. Delete preferences for Postgres.app 
         ```bash
         defaults delete com.postgresapp.Postgres2
         ```
     - Start/End Server
  - [Homebrew](https://brew.sh/)
     - Installing
          ```bash 
          /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
          ```
     - Unstalling
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
