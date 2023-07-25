**CONTENTS**
- [Installation](#installation)
  - [macOS](#macos)
    - [Website](#website)
    - [`Homebrew` \& `pyenv` (Python version management)](#homebrew--pyenv-python-version-management)
  - [Windows](#windows)
    - [Install](#install)
    - [Uninstall](#uninstall)
  - [Linux](#linux)
    - [Install](#install-1)
    - [Uninstall](#uninstall-1)
- [Dev-Enviroment](#dev-enviroment)
  - [**`venv` (Built-in in Python 3)**](#venv-built-in-in-python-3)
  - [**`virtualenv` (Third-party for Python2 \& 3)**](#virtualenv-third-party-for-python2--3)
  - [**`conda` (Anaconda/Miniconda)**](#conda-anacondaminiconda)
  

# Installation
## macOS
### Website
  - Install
     1. [**Download**](https://www.python.org/downloads/macos/)
     2. ```bash
        python3 --version
        ```
  - Uninstall
     1. Locate Python in the list of installed programs.
     2. Select Python and click on the "Uninstall" or "Remove" button.
### [`Homebrew`](https://brew.sh/) & [`pyenv`](https://github.com/pyenv/pyenv) (Python version management)
1. Install [`Homebrew`](https://brew.sh/)
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh"
   ```
   ```bash
   brew --version
   ```
2. install [`pyenv`](https://github.com/pyenv/pyenv) 
   ```bash
   pyenv --version
   ```
   ```bash
   brew install pyenv
   ```
   ```bash
   pyenv --help
   ```
   ```bash
   pyenv install --list
   ```
   ```bash
   pyenv install 3.11.4
   ```
- choose versions
  
   ```bash
   pyenv versions
   ```
   ```bash
   pyenv global 3.11.4
   ```
   or

   ```bash
   cd ../project
   ```
   ```bash
   pyenv local 3.9.6
   ```
   ```bash
   pyenv versions
   ```

- Uninstall `pyenv`
   ```bash
   brew uninstall pyenv
   ```
- Uninstall `Homebrew`
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
   ```
## Windows
### Install
   1. [Download](https://www.python.org/downloads/windows/waddawdaw)
   2. Verify the installation
        ```bash
        python3 --version
        ```
### Uninstall
   1. Locate Python in the list of installed programs.
   2. Select Python and click on the "Uninstall" or "Remove" button.

## Linux
### Install
   1. ```bash
      sudo apt-get install python3
      ```
   2. Verify the installation
      ```bash
      python3 --version
      ```
### Uninstall
   ```bash
   sudo apt-get remove python3
   ```

# Dev-Enviroment

## **`venv` (Built-in in Python 3)**
   - Create a new virtual environment in the current directory:
     ```bash
     python3 -m venv venv
     ```
   - Activate the virtual environment:
     - On macOS/Linux:
       ```bash
       source venv/bin/activate
       ```
     - On Windows (Command Prompt):
       ```bash
       venv\Scripts\activate.bat
       ```
       Or on Windows (PowerShell):
       ```bash
       venv\Scripts\Activate.ps1
       ```
   - Deactivate the virtual environment:
     ```bash
     deactivate
     ```
## **`virtualenv` (Third-party for Python2 & 3)**
   - Install `virtualenv` using `pip` :
     ```bash
     pip install virtualenv
     ```
   - Create a new virtual environment in the current directory:
     ```bash
     virtualenv virtualenv
     ```
   - Activate the virtual environment (same as `venv`):
     - On macOS/Linux:
       ```bash
       source virtualenv/bin/activate
       ```
     - On Windows (Command Prompt):
       ```bash
       virtualenv\Scripts\activate.bat
       ```
       Or on Windows (PowerShell):
       ```bash
       virtualenv\Scripts\Activate.ps1
       ```
   - Deactivate the virtual environment (same as `venv`):
     ```bash
     deactivate
     ```
## **`conda` (Anaconda/Miniconda)**
   - Install Anaconda or Miniconda by downloading the installer from their respective websites.
   - Create a new conda environment:
     ```bash
     conda create --name myenv python=3.9
     ```
     This will create a new conda environment named `myenv` with Python 3.9.

   - Activate the conda environment:
     - On macOS/Linux:
       ```bash
       conda activate myenv
       ```
     - On Windows:
       ```bash
       conda activate myenv
       ```
   - Deactivate the conda environment:
     ```bash
     conda deactivate
     ```
