# IntuneWin32AppPackager
This project aims at making it easier to package, create and at the same time document Win32 applications for Microsoft Intune. A manifest file name App.json needs to be configured to control how the application is created. Configurations such as application name, description, requirement rules, detection roles and other is defined within the manifest file. Create-Win32App.ps1 script file is used to start the creation of the application, based upon configuration specified in the manifest file, App.json.

## File and folder structure
For each application that has to be packaged as a Win32 app, a specific application folder should be created with the IntuneWin32AppPackager files and folder residing inside it. Below is an example of how the folder structure could look like:

- Root
  - Application 1.0.0 (this is the folder where the IntuneWin32AppPackager is contained within)
    - Package (Folder)
    - Source (Folder)
    - Scripts (Folder)
    - Create-Win32App.ps1
    - Icon.png
    - App.json

## Detection Rule sample

```Json
{
    "Type": "Registry",
    "DetectionMethod": "VersionComparison",
    "KeyPath": "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\123",
    "ValueName": "DisplayVersion",
    "Operator": "greaterThanOrEqual",
    "Value": "1.0.0",
    "Check32BitOn64System": "false"
}
```