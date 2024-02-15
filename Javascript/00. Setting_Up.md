- [Installing](#installing)
  - [Mac](#mac)
  - [Linux](#linux)
  - [Windows](#windows)


# Installing 
## Mac
1. **Download**

   - Download the Java JDK: [Oracle Downloads](https://www.oracle.com/java/technologies/javase-jdk15-downloads.html).
   - Choose the macOS version and download the `.dmg` installer file.

2. **Install**

   - Open the downloaded `.dmg` file.
   - Double-click on the JDK installer package.
   - Follow the on-screen instructions to complete the installation.

3. **Verify**
    ```bash
    java -version
    ``` 

## Linux
1. Update Package Index
```bash
sudo apt update
```
2. **Download & Install**
- For most Linux distributions, you can install Java directly from the package manager.
```bash
sudo apt install default-jdk
```
3. **Verify Installation**
```bash
java -version
```

## Windows

1. **Download & Install**
- Download the Java JDK: [Oracle Downloads](https://www.oracle.com/java/technologies/javase-jdk15-downloads.html).
- Choose the Windows version and download the `.exe` installer file.
- Run the downloaded installer.

2. **Set Environment Variables** (Optional but Recommended)

- Right-click on ‘My Computer’ and select ‘Properties’.
- Click on ‘Advanced system settings’.
- In the System Properties window, click on the ‘Environment Variables’ button.
- Under System Variables, find and select the ‘Path’ variable, then click on ‘Edit’.
- Add the path to the `bin` directory of the Java installation to the Path variable. Typically, this will be something like `C:\Program Files\Java\jdk-15\bin`.
- Click OK to close each dialog.

1. **Verify** 
```bash
java -version
``` 
