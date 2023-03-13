# doskey macro 

## how to use:  

copy the below text and put into c:\dkm.txt
and then run this registry command in command line with admin privilage. 
```
reg add "HKLM\Software\Microsoft\Command Processor" /v Autorun /d "doskey /macrofile=c:\dkm.txt /f"
```

## c:/dkm.txt  

```
ipfshell=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client"  
ipfscript=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client -f $1 -q"  
ipfdg2=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client -f c:\dg2.txt -q"  
ipftpg=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client -f c:\tpg.txt -q"  
odvp1=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client -c \"dptf tableobject set odvp $1!0!0!0!0!0\" -q"  
odvp2=forfiles /P C:\Windows\System32\Driverstore\FileRepository /M ipf_uf.exe /s /c "cmd /c taskkill /f /fi \"imagename eq ipf_uf.exe\" /fi \"session eq 1\" & @path client -c \"dptf tableobject set odvp 0!$1!0!0!0!0\" -q"  
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
autologon = echo y| reg add "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon" /v AutoAdminLogon  /d 1 & echo y| reg add "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultUserName   /d Administrator & echo y| reg add "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon" /v DefaultPassword   /d intel123  
```

## c:/tpg.txt  

```  
config set @dptf /features/tpg_policy 1  
tableobject set idsp 1 D0 "63BE270F-1C11-48FD-A6F7-3AF253FF3E2D!9E04115A-AE87-4D1C-9500-0F3E340BFE75!FF227DFE-2324-A543-81A9-5C70423ADC2E!6ED722A7-9240-48A5-B479-31EEF723D7CF!92951065-6427-4B30-9737-13CC70EFA21A"  
tableobject set idsp 1 D0 "63BE270F-1C11-48FD-A6F7-3AF253FF3E2D!9E04115A-AE87-4D1C-9500-0F3E340BFE75!FF227DFE-2324-A543-81A9-5C70423ADC2E!6ED722A7-9240-48A5-B479-31EEF723D7CF"  
participant create CONJURE MCPP 'Multi Chip Package Participant' INT3530 38  
tableobject set ppcc MCPP d0 02:0,30000,65000,0,0,500!1,105000,105000,0,0,500!2,4294967295,4294967295,4294967295,4294967295,4294967295!3,195000,195000,0,0,500  
setp_part mcpp 393 d0 255 1  
participant create ACPI NVDG 'NV Discrete GFX Participant' INT340D 44  
sleep 1000  
tableobject set ppcc NVDG d0 02:0,6000,25000,0,32000,500!1,40000,42000,0,32000,500!2,4294967295,4294967295,4294967295,4294967295,4294967295!3,74000,74000,0,32000,500  
setp_part nvdg 393 d0 255 1  
dptf tableobject set tpga "01:\_SB_.PC00.TCPU,9,50!\_UP_.MCPP,38,4294967295!\_LP_.NVDG,44,50" dptf /shared/tables/tpga/t  
dptf tableobject set tpga "01:\_SB_.PC00.TCPU,9,50!\_UP_.MCPP,38,4294967295!\_LP_.NVDG,44,50"  
```  

## c:/dg2.txt  

```
tableobject set idsp 1 D0 "A75E38B4-A7AC-4A7B-8BDC-1A1572BE318E"
tableobject set idsp 1 D0 "A75E38B4-A7AC-4A7B-8BDC-1A1572BE318E!92951065-6427-4B30-9737-13CC70EFA21A"
participant create CONJURE MCPP 'Multi Chip Package Participant' INT3530 38  
tableobject set ppcc MCPP d0 02:0,30000,65000,0,0,500!1,105000,105000,0,0,500!2,4294967295,4294967295,4294967295,4294967295,4294967295!3,195000,195000,0,0,500  
setp_part mcpp 393 d0 255 1 
participant create ACPI IDG2 'IA Discrete GFX Device 2 Participant' INT340D 43
sleep 1000
tableobject set ppcc 65589 D0 "02:0,5000,25000,0,32000,500!1,41000,41000,0,32000,500!2,4294967295,4294967295,4294967295,4294967295,4294967295!3,74000,74000,0,32000,500"
setp_part IDG2 SET_PARTICIPANT_CAPABILITIES_EVAL D0 255 "1"
setp_part IDG2 393 d0 255 1  
tableobject set psh2 1 D0 dptf /shared/tables/psh2/dg2bias "01:\_SB_.PC00.TCPU,9,50!\_UP_.MCPP,38,4294967295!\_LP_.IDG2,43,50"
tableobject set psh2 1 D0 "01:\_SB_.PC00.TCPU,9,50!\_UP_.MCPP,38,4294967295!\_LP_.IDG2,43,50"

```