# Setting Up
## Postgresql
### macOS
  - [postgres.app](https://postgresapp.com/)
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
