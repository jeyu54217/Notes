**CONTENTS**
- [Installation](#installation)
  - [macOS](#macos)
    - [Install](#install)
    - [Uninstall](#uninstall)
    - [Switching Version](#switching-version)
  - [Windows](#windows)
    - [Install](#install-1)
    - [Uninstall](#uninstall-1)
    - [Switching Version](#switching-version-1)
  - [Linux](#linux)
    - [Install](#install-2)
    - [Uninstall](#uninstall-2)
    - [Switching Version](#switching-version-2)
- [Enviroment](#enviroment)
- [Directories](#directories)
- [Process \& thread](#process--thread)
- [Time](#time)
  

# Installation
## macOS
### Install
  1. [**Download**](https://www.python.org/downloads/macos/)
  2. ```bash
      python3 --version
     ```
### Uninstall
  ```Finder``` -> ```Applications``` -> ```Python``` -> Trash

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
    1.  ```bash
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

# Enviroment


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
