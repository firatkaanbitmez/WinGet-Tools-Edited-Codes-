# WinGet Tools (Edited Codes)
Update and Install your software using WinGet and PowerShell

# Features 

*Detailed Table

*C programing

*use for Powershell


# WinGet Basic Codes

Winget search App-Name
-------------
winget search firefox
winget search "adobe acrobat"
  
Winget Upgrade
---------
winget upgrade --all --accept-package-agreements --accept-source-agreements --override --silent

winget upgrade --all

winget upgrade App-ID

winget upgrade Adobe.Acrobat.Reader.64-bit

Winget list
------------
winget list >>> Yours all installed programs listed

winget install App-ID
---------------
Winget install  Mozilla.Firefox        

WinGet Install Adobe.Acrobat.Reader.64-bit

Winget Install --id Adobe.Acrobat.Reader.64-bit

Winget Install --silent --id Adobe.Acrobat.Reader.64-bit

Winget Install --silent --accept-source-agreements --id Adobe.Acrobat.Reader.64-bit

Winget Install --silent --accept-source-agreements --id Adobe.Acrobat.Reader.64-bit

winget uninstall App-ID
-----------------------
Winget UnInstall --help

Winget UnInstall --id Adobe.Acrobat.Reader.64-bit

WinGet UnInstall Adobe.Acrobat.Reader.64-bit

WinGet UnInstall --silent --id Adobe.Acrobat.Reader.64-bit

winget uninstall "microsoft teams" --version 1.5.00.14473

winget uninstall Notepad++.Notepad++ --silent


winget source
------------------
winget source list

winget source add --name [name] [url]

winget source add --name newwinget https://winget.azureedge.net/cache

winget source update

winget source remove --name [name]

winget source remove --name newwinget 

winget source reset --force


Help
--------------------

-m,–manifest – The path to the manifest of the package

–id – Filter results by id

–name – Filter results by name

–moniker – Filter results by moniker

-v,–version – Use the specified version; default is the latest version

-s,–source – Find package using the specified source

-e,–exact – Find package using exact match

-i,–interactive – Request interactive installation; user input may be needed

-h,–silent – Request silent installation

-o,–log – Log location (if supported)

–header – Optional Windows-Package-Manager REST source HTTP header

–accept-source-agreements – Accept all source agreements during source operations



# Winget_Upgrade.ps1 Example Image

![example](https://user-images.githubusercontent.com/74864221/217322309-fa6ae15c-08c4-450e-9a0f-2d3516a2c9f8.png)



# WinGet for App Packager Automatic Last Version Installer Batch Codes

cd %userprofile%\downloads

curl -L https://github.com/microsoft/winget-cli/releases/latest/download/Microsoft.DesktopAppInstaller_8wekyb3d8bbwe.msixbundle -o winpackageins.msixbundle



powershell -command "Add-AppPackage -path "%userprofile%\downloads\winpackageins.msixbundle""

winget search zoom --accept-source-agreements
winget source reset --force
winget source add -n winget "https://cdn.winget.microsoft.com/cache"
winget source update --accept-source-agreements
winget search vlc --accept-source-agreements
taskkill /f /im Infinity.exe
cd %userprofile%\desktop
Infinity.lnk
