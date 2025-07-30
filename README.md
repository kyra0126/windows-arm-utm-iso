# [Mac OS/M1] Installing Windows 11 Virtual Machine on UTM

> **Jump to Section:**  
> - [Environment](#environment)  
> - [Installation Methods: VHDX vs ISO](#two-main-installation-methods-vhdx-vs-iso)  
> - [ISO Installation Method](#iso-installation-method)  
>   - [Quick Summary](#quick-summary)  
>   - [Step-by-Step Instructions](#step-by-step-instructions)  
>     - [1. Download Windows 11 ARM64 ISO](#1-download-windows-11-arm64-iso)  
>     - [2. Install UTM](#2-install-utm)  
>     - [3. Create a New Windows VM](#3-create-a-new-windows-vm)  
>     - [4. Start the VM and Connect to Internet](#4-start-the-vm-and-connect-to-internet)  
>     - [5. Change Region / Language Settings](#5-change-region--language-settings)  
> - [Troubleshooting](#troubleshooting)  
>   - [VM boots but OS doesn’t start](#vm-boots-but-os-doesnt-start)


## Environment

- **Chip**: MacBook M1 Pro  
- **macOS Version**: macOS Sonoma 14.6.1  
- **UTM Version**: 4.6.5  
- **Windows Build**: Windows 11 (multi-edition for ARM64)

## Two Main Installation Methods: VHDX vs ISO

| Category | ISO File                          | VHDX File                               |
|----------|----------------------------------|-----------------------------------------|
| Purpose  | Installation disk image          | Virtual hard disk image                 |
| Description | Used for installing or booting OS | Pre-installed Windows that runs directly |
| Analogy  | Windows installation CD          | A virtual PC with Windows already installed |

## ISO Installation Method

> [VHDX Installation Method](https://github.com/kyra0126/windows-arm-utm-vhdx/blob/ce9e6197affd7cd4b0862b5623b173b3a6191e78/README.md)

### Quick Summary

1. Download the Windows 11 ARM64 ISO file  
2. Install UTM  
3. Create a new Windows VM  
4. Run the VM and connect to the internet  
5. Change language/region settings  

### Step-by-Step Instructions

#### 1. [Download Windows 11 ARM64 ISO](https://www.microsoft.com/en-us/software-download/windows11arm64)
Select **Windows 11 (multi-edition for ARM64)** and start download  
![Download File](screenshots/iso/iso_download_arm64.png)

#### 2. [Install UTM](https://mac.getutm.app)

![Download File](screenshots/utm_download.png)

#### 3. Create a New Windows VM

<img src="screenshots/utm_vm.png" width="250"><img src="screenshots/utm_vm2.png" width="250"><img src="screenshots/utm_vm3.png" width="250">

- Attach the ISO file downloaded in step 1 to the **Boot ISO Image**  
  ![Attach ISO](screenshots/iso/utm/utm_vm_windows_iso.png)

<img src="screenshots/utm_vm4.png" width="250"><img src="screenshots/utm_vm5.png" width="250"><img src="screenshots/utm_vm6.png" width="250">

#### 4. Start the VM and Connect to Internet

- Press any key to begin Windows installation  
- Choose language/keyboard options  

<img src="screenshots/iso/utm/utm_vm_windows_start.png" width="250"><img src="screenshots/iso/utm/utm_vm_windows_language.png" width="250"><img src="screenshots/iso/utm/utm_vm_windows_keyboard.png" width="250">

- Select Windows image  
- Click "I don’t have a product key"  

<img src="screenshots/iso/utm/utm_vm_windows_image.png" width="250"><img src="screenshots/iso/utm/utm_vm_windows_productkey.png" width="250"><img src="screenshots/iso/utm/utm_vm_windows_install.png" width="250">

- After installation, the **utm-guest-tools** installer should pop up automatically  
- If not, open drive D and manually run the **utm-guest-tools** installer  
- Check internet connection and reboot  

<img src="screenshots/vhdx/utm/utm_vm_windows_network7.png" width="250"><img src="screenshots/vhdx/utm/utm_vm_windows_network8.png" width="250"><img src="screenshots/iso/utm/utm_vm_network.png" width="250">

#### 5. Change Region / Language Settings

- Go to Settings > Time & Language > Region: Set to Korea  

<img src="screenshots/vhdx/utm/utm_vm_windows_region.png" width="250"><img src="screenshots/vhdx/utm/utm_vm_windows_region2.png" width="250">

- Add language > Korean > Set as Windows display language  
- Use Command + Space to toggle input languages  

<img src="screenshots/vhdx/utm/utm_vm_windows_language.png" width="250"><img src="screenshots/vhdx/utm/utm_vm_windows_language2.png" width="250"><img src="screenshots/vhdx/utm/utm_vm_windows_languague3.png" width="250">

---

## Troubleshooting

### VM boots but OS doesn’t start

#### Symptoms
- System halts at "UEFI Interactive Shell v2.2" screen  
- Shows `Shell>` prompt  
- Fails to run `startup.nsh`  
![Frozen screen](screenshots/troubleshooting/utm_vm_troubleshooting.png)

#### Causes
- Incorrect ISO file (e.g., "Windows 11 for x64 devices" intended for Intel/AMD architecture)
- ISO disconnected after reboot during installation process

#### Solution
When searching online for the ISO, you might be directed to [Windows 11 x64 ISO download](https://www.microsoft.com/en-us/software-download/windows11arm64)  
Since Apple Silicon uses ARM64 architecture, **do not** download the x64 version  
Click the **"here"** link to access the correct ARM64 ISO download page  
![Wrong ISO](screenshots/iso/iso_download_x64.png)

Make sure to download the ARM64 version  
![Correct ISO](screenshots/iso/iso_download_arm64.png)

After reboot, press any key quickly when prompted  
![Press Any Key](screenshots/iso/utm/utm_vm_windows_start.png)

If the same error persists after reboot, consider switching to the VHDX installation method  
> [VHDX Installation Method](https://github.com/kyra0126/windows-arm-utm-vhdx/blob/ce9e6197affd7cd4b0862b5623b173b3a6191e78/README.md)
