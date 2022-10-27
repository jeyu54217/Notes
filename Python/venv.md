**CONTENTS**
- [VENV](#venv)
  - [macOS](#macos)
  - [windows](#windows)
  - [Linux](#linux)
- [pip](#pip)
  
```bash
python3 --version
```
## VENV
### macOS
```bash
python3 -m pip install virtualenv
```
```bash
python3 -m venv <path/venv>
```
```bash
source <path/to/activate>
```
```bash
deactivate
```
### windows
```bash
python -m venv <path/venv>
```
```bash
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```
```bash
deactivate
```
### Linux
```bash
sudo apt-get update
```
```bash
sudo apt-get install python3-virtualenv
```
```bash
python3 -m ensurepip
```
```bash
python3 -m venv <path/venv>
```
```bash
source <path/to/activate>
```
```bash
deactivate
```



## pip 
```bash
pip help    
```
```bash
pip list
```
```bash
pip freeze > requirements.txt
```
```bash
pip install -r requirements.txt
```


