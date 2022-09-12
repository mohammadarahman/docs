# DPTF-Imager mapping issue

So up until this point, anyone with access to DPTF imager has been using Administrator credentials. This makes the DPTF-Imager drive vulnerable to accidental deletion and unauthorized movement of assets.

If you currently have the DPTF-Imager drive mapped to your computer you need to delete that map (Right click on the network option in windows explorer and select: disconnect a network drive) and re-connect using the following method and credentials.

1.	Open the Windows menu (Bottom right on your desktop)
2.	Search for “Manage Windows Credentials” to find the Windows Credential manager.
3.	From the Manager, Click on the large Widows Credentials button
4.	If you already have DPTF-Imager Credentials listed, then expand that listing and click the Edit button.
5.	If you do not have a DPTF-Imager credential listed, click on the Add a Windows Credential button.
6.	When making a new credential enter:
‘\\dptf-imager’ as the network address
‘dptf-imager\basic’ as the user name
‘welcome2019’ as the password and click OK
7.	If editing a current administrator credential enter:
‘dptf-imager\basic’ as the User name
‘welcome2019’ as the password
8.	Once these changes are made, close Credential manager and open windows explorer.
9.	In the address bar type ‘\\dptf-imager\imaging’ and hit Enter
10.	Click and drag from the address bar over the left to Pin this location to your quick access (now it will show up listed as if mapped when you go to flash an IFWI through DediProg)


# FLashing BIOS

https://www.dediprog.com/download?u=42&l=SF600+Plus+SPI+Flash+IC+Programmer
for KBL-G 
Download the .BIN file from \\\DPTF-Imager\imaging\Image\KBL\KBL-G\RS4\18WW38\BKC_KBL-G-RVP-2018WW38.3.745\Drivers\BIOS v134_02 EC v1_11\KBG_HR17_CONS_NO-PTT_SPI_2018WW26_5_01.bin
This will be in the Drivers folder under "BIOS"
Start the Dediprog Engineering program
Plug the Dediprog hardware into your IT machine
Locate the SPI Header on the board
This is commonly located near the battery on the board
Look closely and see if you can find text that reads "SF600"/"SF 600 TPM"/"SPI" HDR. These are the BIOS headers. If "EC" is nearby, that port is for the Embedded Controller
Some boards require the EC to be flashed independently. These boards will also include a KSC file in the Imager BKC Driver folder
Plug the Dediprog into the SPI Header
In the Dediprog Engineering program:
Click "Detect"
Click "File"
Point the program to your .BIN file that works on the board
Click "Config"
Ensure the Batch Operation Option is on "Download a whole file to chip (Without Blank Check)"
Click "Batch"
After 3-5 minutes, the BIOS will be fully flashed
This will erase all BIOS settings


# Installing and configuring visual studio

1. Download and install [Windows Driver Kit](https://docs.microsoft.com/en-us/windows-hardware/drivers/download-the-wdk)  .
2. Install VS from software market. 
3. Select the following feature. 
		- Workloads  
		  - Windows  
		    - Desktop development with C++  
		    - Universal Windows Platform development  
		  - Other Toolsets  
		    - Visual Studio extension development  
		- Individual components  
		  - .NET  
		    - .NET Framework 3.5 development tools  
		    - .NET Framework 4 targeting pack  
		    - .NET Framework 4.5 targeting pack  
		    - .NET Framework 4.5.1 targeting pack  
		    - .NET Framework 4.5.2 targeting pack  
		  - Compilers, build tools, and runtimes  
		    - VC++ 2015.3 v140 toolset for desktop (x86, x64)  
		  - SDKs, libraries, and frameworks  
		    - Windows 10 SDK (10.0.14393.0)  
		    - Windows 10 SDK (10.0.15063.0) for Desktop C++ [x86 and x64]  
4. Under Installation Details
  - Universal Windows Platform Development
    - C++ Universal Windows Platform tools
    - Graphic debugger and GPU profiler for DirectX
    - Windows 10 SDK (10.0 15063.0) for UWP: C#, VB, JS
    - Windows 10 SDK (10.0.14393.0)
  - Desktop Development with C++
    - VC++ 2017 latest v141 tools
    - C++ profiling tools
    - Visual C++ tools for CMake
    - Visual C++ ATL for x86 and x64
    - Visual C++ MFC for x86 and x64
    - Windows 10 SDK (10.0.14393)
    - Windows 10 SDK (10.0.15063.0) for Desktop C++ (x86 and x64)
    - Windows 10 SDK (10.0.16299.0) for Desktop C++ (x86 and x64)
    - VC++ 2015 4 v140 toolset for desktop (x86, x64)
  - Visual Studio extension development
    - .NET profiling tools
    - Text Template Transformation
    - Visual C++ runtime for UWP
    - Developer Analytics tools
    - Visual C++ ATL for x86 and x64
    - Visual C++ MFC for x86 and x64
    - Visual Studio C++ core feature
    - VC++ 2017 latest v141 tools
5. Open tools-> Extensions and Updates goto online and install
  - NUnit 2 test adapter
  - specflow for visual studio 2017
6. install [Microsoft build tools](https://www.microsoft.com/en-us/download/details.aspx?id=48159) .
  - this will add MSBuild toolset 14.0 in registry. 

# Connected Standby

- change bios settings acpi -> low Power S0 Capability
- can check status using powercfg -a commmand. 



# RFIM related

## change channel number

- do it from router . (admin\'') 
- network key welcome2012 
- calculator is on 
- \‪\\chakotay.hf.intel.com\SoftVal\DPTF_tools\_Policies\RFIM\HarmonicCalculator(Latest & Greatest).xlsx 


### esif shell to change rf profile center freq 
open esif shell
set destination to TCPU participant
cal GET_RFPROFILE_CENTER_FREQUENCY
Expect: returns default value, 139500000
Actual: returns 0
call SET_RF_PROFILE_CENTER_FREQUENCY with a value within bounds (ex: 139500000)
call GET_RFPROFILE_CENTER_FREQUENCY

https://hsdes.intel.com/appstore/article/#/2204755850 
https://hsdes.intel.com/appstore/article/#/2201903010 

## reload esif shell. 
from device manager -> system devices
remove the processor 
and scan again. 


# access

Permissions on ags.intel.com:  
DevTools - OWR Artifactory - Viewer  
DevTools - TeamCity - Production - DPTF Validation - Developer  
DevTools - TeamCity - Production - DPTF Validation - Project Admin  
DevTools - TeamCity - Production - DPTF Validation - Project Viewer  
OWR Viewer  
Unified Build Image & Test UBIT - Standard DPTF8 Project - Developer  

#Automation  fix

### specflow fix
install this and deselect autoupdate. 
\\chakotay\SoftVal\DPTF_tools\SpecFlow.DamageControl

# MISC

## how to hibernate 
- sometime hibernate icon might be missing. 
- use command shutdown /h 

## Turn off fan - mm command 

- goto bios shell 
- mm 66 f3 -w 1 -io 

## UI folder / other folder 
- c:\program files\intel\intel(r) dynamic tuning\ 

## log path 
- c:\windows\system32\drivers\driverdata\intel\dptf\log 

- windowx + x to get the windows shortcut control pannel
  - m for device manager
  - k for disk manager
  - v for event viewer

## command string

findstr /M /R /S /c:"8cdadc931c4053e7a7e1bf1ff399215d" *.* 
