# choco install

## install choco 
Install Chocolately if not auto loaded by WIM
o Open cmd prompt (elevated) 

@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://github.intel.com/raw/tcase/chocolatey-packages/master/scripts/corporate_install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
 
## Install tightvnc
choco install tightvnc -y

## Install 3dmark11
Choco install 3dmark11 -y