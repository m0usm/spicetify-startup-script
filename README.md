<p align="center">
  <img src="./img/banner.png" alt="Spicetify Setup Banner" width="35%"/>
</p>

---

# Spicetify CLI Auto-Install for Windows

**An automated Batch script for Windows designed to recurrently install and update the Spicetify CLI every time a user logs into their system.**

## 🚀 How It Works

The script automates the following steps to execute the official installation command (`iwr ... | iex`) **silently** on every system startup:

1.  **Script Folder Creation:** It creates a persistent directory at `C:\Scripts`.
2.  **PowerShell Script Creation:** The file `spicetify_install.ps1` containing the official install command is saved to `C:\Scripts`.
3.  **Wrapper Script Creation:** The file `spicetify_start.bat` is created to execute PowerShell **invisibly** (`start /min`).
4.  **Startup Shortcut:** A shortcut (`.lnk`) pointing to `spicetify_start.bat` is placed in the current user's Startup folder (`%APPDATA%...\Startup`).

## 🛠️ Usage

### Project Files

The two main files used in this setup are:

* **Setup Script:** [`setup_autostart.bat`](setup_autostart.bat) (The executable installer)
* **Core Command:** [`spicetify_install.ps1`](spicetify_install.ps1) (The underlying PowerShell command)

### Prerequisites

* Administrator rights for the initial setup.

### Setup Instructions (How to Run)

1.  **Download:** Download the [`setup_autostart.bat`](setup_autostart.bat) file from this repository (click the file, then click "Download Raw File").

2.  **Execute as Administrator:**
    * Right-click the downloaded `setup_autostart.bat` file and select **"Run as administrator"**.

3.  **CRITICAL INTERRUPTION: Type 'Y' and Enter**
    Immediately after execution, a PowerShell window may appear asking to install a necessary provider (e.g., **NuGet**).
    
    * **You MUST type `Y` and press Enter** to allow the script to proceed with the Spicetify installation. This manual confirmation is mandatory.

4.  **Alternative Execution via Terminal (Drag & Drop):**
    * Open the Command Prompt (`cmd`) or PowerShell **as Administrator**.
    * **Drag the `setup_autostart.bat` file** into the Terminal window to automatically insert its full path.
    * Press **Enter** to run the script (and perform the **CRITICAL INTERRUPTION** if prompted).

5.  **Finished:** The routine is set up. The script will now execute automatically upon every subsequent user login.

---

## ⚠️ Important Notes

### Antivirus/Malwarebytes Warning (False Positive)

Due to the nature of the script—downloading and executing remote code via PowerShell (`iwr ... | iex`)—your antivirus software (such as Malwarebytes) may flag the `setup_autostart.bat` file or the execution process as a **Generic Payload** or **Suspicious Behavior**.

* This is generally a **False Positive** because the script is only executing the official Spicetify installation command.
* If you trust the Spicetify source, you can safely **add an exclusion** for the `setup_autostart.bat` file in your antivirus program before running it.

### Security

This script executes a command that downloads code from an external server and runs it immediately (`iwr -useb ... | iex`). Ensure you trust the source (Spicetify CLI) before running the automated script, and consider reviewing the contents of the official installation script periodically.

### Uninstallation

To stop the automatic execution, simply delete the created shortcut:

1.  Press `Win` + `R` and type `shell:startup` and press Enter.
2.  Delete the shortcut named **`Spicetify Autostart.lnk`**.
3.  Optional, you can also delete the `C:\Scripts` folder to remove the script files.

---

## 📜 License

This project is licensed under the **[MIT License](LICENSE)**.
