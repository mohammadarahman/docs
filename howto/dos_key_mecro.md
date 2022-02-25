# doskey macro 

## how to use:
copy the below text and put into c:\dkm.txt
and then run this registry command in command line with admin privilage. 
'''
reg add "HKLM\Software\Microsoft\Command Processor" /v Autorun /d "doskey /macrofile=c:\dkm.txt /f
'''

## c:/dkm.txt
'''
ipfshell=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client"  
odvp1=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client -c \"tableobject set odvp 0 d0 $1!0!0!0!0!0\" -q"  
odvp2=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client -c \"tableobject set odvp 0 d0 0!$1!0!0!0!0\" -q"  
ip=ipconfig $B findstr IPv4  
f=dir /s/b $1  
http=python -m http.server 80  
watermark=slmgr /skms kms.intel.com $t slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX $t slmgr /ato  
unzip=forfiles /m *.zip /c "cmd /c mkdir @fname & tar -xf @path -C @fname"  
un7z=forfiles /m *.7z /c "cmd /c 7z e @path -o@fname -y"  
unzipdir=forfiles /p $1 /m *.zip /c "cmd /c mkdir $1\\@fname & tar -xf @path -C $1\\@fname"   
getdtt=mkdir c:\build\$1 & cd c:\build\$1 & curl -u rahmanma:$2 https://ubit-artifactory-or.intel.com/artifactory/dptf-local/Build_Artifacts/Windows/1.0.$1/IPF-WindowsIpfUiInstaller-1.0.$1.zip -o IPF-WindowsIpfUiInstaller-1.0.$1.zip & curl -u rahmanma:$2 https://ubit-artifactory-or.intel.com/artifactory/dptf-local/Build_Artifacts/Windows/1.0.$1/IPF-WindowsPACInstaller-1.0.$1.zip -o IPF-WindowsPACInstaller-1.0.$1.zip & curl -u rahmanma:$2 https://ubit-artifactory-or.intel.com/artifactory/dptf-local/Build_Artifacts/Windows/1.0.$1/IPF-WindowsDttUiInstaller-9.0.$1.zip -o IPF-WindowsDttUiInstaller-9.0.$1.zip & curl -u rahmanma:$2 https://ubit-artifactory-or.intel.com/artifactory/dptf-local/Build_Artifacts/Windows/1.0.$1/IPF-WindowsDttPACInstaller-9.0.$1.zip -o IPF-WindowsDttPACInstaller-9.0.$1.zip  
install=forfiles /m *install.exe /s /c "cmd /c @path -s -overwrite & pause"  
remdtt="C:\Program Files\Intel\Intel(R) Dynamic Tuning Technology\Uninstall\install.exe" -uninstall -s & timeout 15  
remdttui="C:\Program Files\Intel\Intel(R) Dynamic Tuning Technology User Interface\Uninstall\install.exe" -uninstall -s & timeout 15  
remipf="C:\Program Files\Intel\Intel(R) Innovation Platform Framework\Uninstall\install.exe" -uninstall -s & timeout 15  
remipfui="C:\Program Files\Intel\Intel(R) Innovation Platform Framework User Interface\Uninstall\install.exe" -uninstall -s & timeout 15  
'''