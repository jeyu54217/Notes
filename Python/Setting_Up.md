**CONTENTS**
- [Installation](#installation)
  - [macOS](#macos)
    - [Website](#website)
    - [Homebrew \& pyenv](#homebrew--pyenv)
  - [Windows](#windows)
    - [Install](#install)
    - [Uninstall](#uninstall)
  - [Linux](#linux)
    - [Install](#install-1)
    - [Uninstall](#uninstall-1)
- [Dev-Enviroment](#dev-enviroment)
  - [Os layer (Python version management)](#os-layer-python-version-management)
  - [App layer](#app-layer)
- [Directories](#directories)
- [Process \& thread](#process--thread)
- [Time](#time)
  

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
### [Homebrew](https://brew.sh/) & [pyenv](https://github.com/pyenv/pyenv)
1. Install [Homebrew](https://brew.sh/)
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh"
   ```
   ```bash
   brew --version
   ```
2. install [pyenv](https://github.com/pyenv/pyenv) (Python version management)
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

- Uninstall pyenv
   ```bash
   brew uninstall pyenv
   ```
- Uninstall Homebrew
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
## Os layer (Python version management)
- [pyenv](https://github.com/pyenv/pyenv)
1. ```bash 
   python3 --version
   ```
2. ```bash 
   brew install pyenv
   ```
3. ```bash 
   eval "$(pyenv init -)"
   ```
4. ```bash 
   brew install pyenv
   ```
5. ```bash 
   brew install pyenv
   ```
6. ```bash 
   brew install pyenv
   ```
- [conda](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html)
## App layer

1. `venv` (Python 3):

   - Installation: `venv` is included in Python 3 by default, so there's no need for separate installation.

   - Create a virtual environment:
     ```
     python3 -m venv <your_proj/venv>
     ```

   - Activate the virtual environment:
     - macOS/Linux:
       ```
       source <your_proj/venv/bin/activate> 
       ```
     - Windows:
       ```
       venv\Scripts\activate 
       ```

   - Deactivate the virtual environment:
     ```
     deactivate
     ```

   - Delete the virtual environment:
     Simply delete the `myenv` directory.

2. `virtualenv`:

   - Installation:
     ```
     pip install virtualenv
     ```

   - Create a virtual environment:
     ```
     virtualenv myenv
     ```

   - Activate the virtual environment:
     - macOS/Linux:
       ```
       source myenv/bin/activate
       ```
     - Windows:
       ```
       myenv\Scripts\activate
       ```

   - Install packages using `pip`:
     ```
     pip install package_name
     ```

   - Deactivate the virtual environment:
     ```
     deactivate
     ```

   - Delete the virtual environment:
     Simply delete the `myenv` directory.

3. `conda`:

   - Installation:
     Follow the official instructions to install Anaconda or Miniconda from the Anaconda website (https://www.anaconda.com/products/individual).

   - Create a virtual environment:
     ```
     conda create --name myenv
     ```

   - Activate the virtual environment:
     ```
     conda activate myenv
     ```

   - Install packages using `conda` or `pip`:
     ```
     conda install package_name
     ```

   - Deactivate the virtual environment:
     ```
     conda deactivate
     ```

   - Delete the virtual environment:
     ```
     conda env remove --name myenv
     ```

4. `pipenv`:

   - Installation:
     ```
     pip install pipenv
     ```

   - Create a virtual environment and install packages:
     ```
     pipenv install package_name
     ```

   - Activate the virtual environment:
     ```
     pipenv shell
     ```

   - Install packages using `pipenv`:
     ```
     pipenv install package_name
     ```

   - Deactivate the virtual environment:
     ```
     exit
     ```

   - Delete the virtual environment:
     ```
     pipenv --rm
     ```

# Directories
# Process & thread
# Time
