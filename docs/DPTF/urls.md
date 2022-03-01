- [Validation links for work](#validation-links-for-work)
- [DPTF All Wiki](#dptf-all-wiki)
    + [Learning material](#learning-material)
      - [Automation](#automation)
    + [Training](#training)
    + [How To](#how-to)
      - [Automation](#automation-1)
      - [ESIF](#esif)
      - [ESIF Event/Driver tracing and logging](#esif-event-driver-tracing-and-logging)
      - [Tools](#tools)
    + [DPTF UI](#dptf-ui)
    + [Tips & Tricks](#tips---tricks)
- [Misc](#misc)
    + [IP](#ip)
    + [File server location:](#file-server-location-)
    + [Intel General Links](#intel-general-links)
    + [Misc training](#misc-training)
    + [HID Event Filter Driver Testing](#hid-event-filter-driver-testing)
    + [iMBO](#imbo)


------------


# Validation links for work
- [DPTF Validation JIRA scrum Board](https://jira.devtools.intel.com/secure/RapidBoard.jspa?rapidView=938)  validation team  
- [DPTF Jira Scrum Board](https://jira.devtools.intel.com/secure/RapidBoard.jspa?rapidView=941)  story grooming with developer  
- [HSD DPTF Open Defect](https://hsdes.intel.com/appstore/community/#/1205881510?queryId=22027323)  
- [HSC ES sighting database](https://hsdes.intel.com/home/default.html#magazine?id=1205881510&contentId=1205945722&articleId=1205617597)  
- [DPTF Test Results ](http://idt_val_vm_srv:8081)  new link for checking automation test  
- [JAMA dashboard](https://jama4.intel.com/perspective.req#/projects/104/dashboard)  
- [Teamcity Results](http://idt_val_vm_srv/teamcity)  
- [Team city triage results](https://ubit-teamcity-hf.intel.com/project.html?projectId=DptfEsif_WindowsBuilds_4abatRunnersCriticalConfigs&tab=projectOverview)  
- [Teamcity for staging or automation](https://ubit-teamcity-hf.intel.com/project.html?projectId=DptfEsif_WindowsBuilds_Main_AutomationIntegrationRunners&tab=projectOverview)  
- [artifcats builds specific one](https://ubit-artifactory-or.intel.com/artifactory/dptf-local/Build_Artifacts/Windows/8.7.10099.10716/)  
- [build location](https://owrpilot-cbjenkins.fm.corp.intel.com/teams-dptf/job/dptf/view/Main%20Builds/job/WindowsPipeline/)  
- [DPTF reports](http://idt_val_vm_srv/)  
- [TWS UI# https://sx-cycler-rem-vm:7072](https://sx-cyclr-rem-vm:7072)  
- [TWS UI](https://sx-cyclr-rem-vm:8000/index.html)  
- [teamcity](https://ubit-teamcity-hf.intel.com/project.html?projectId=DptfEsif&branch_DptfEsif=%3Cdefault%3E)  
- [jenkins](https://owrpilot-cbjenkins.fm.corp.intel.com/teams-dptf/job/dptf/job/AutomationPipeline/build?delay=0sec)  
- [Ramp Up Test Plan](https://jama4.intel.com/perspective.req#/testPlans/24415445?projectId=104)  
- [DPTF reports](https://pbiprovisioned.intel.com/Reports/browse/CQN/ISQ/SSG%20CSS/DPTF )  
- [GITlab dev repo](https://gitlab.devtools.intel.com/OWR/DPTF/dptf) `https://gitlab.devtools.intel.com/OWR/DPTF/dptf`  
- [Platform information](https://wiki.ith.intel.com/display/DPTF/Platforms) Target SUt  
  - AML     CNL-U/Y    CFL-H/S/U    CML   ICL-U/Y   KBL-G    KBL-H (kbl.rvp11)  KBL-U    LKF    WHL-U   Old-Platforms
  - System BIOS/OS/DPTF preparation
- [platform legacy](http://wiki.ith.intel.com/pages/viewpage.action?pageId=420619789)  
- [Power BI](https://pbiprovisioned.intel.com/Reports/powerbi/CQN/ISQ/SSG%20CSS/DPTF/DPTF-Ingredients%20Test%20Results)  
- [Artifactory](https://ubit-artifactory-or.intel.com/artifactory/webapp/home.html?0)  PreBKC drivers
- [Milestone Release](https://wiki.ith.intel.com/display/DPTF/DPTF+Milestone+Releases)  
- [BKC](https://onebkc.intel.com/#/filter/)  
- [Power Share](https://wiki.ith.intel.com/display/DPTF/Getting+Started+with+Power+Share+Policy)  
- [Lab port ip setup](https://ilab.intel.com)  

# DPTF All Wiki

### Learning material 
- [Overall Validation Wiki](https://wiki.ith.intel.com/display/CPS/6+-+CPS+Validation+Wiki)    for projects IDTT/ XTU/ IPM/ IPTS 
  - [VAC](https://wiki.ith.intel.com/pages/viewpage.action?pageId=1308384562) Quarterly assessment  
  - [itouch BKC validation](https://wiki.ith.intel.com/display/CPS/iTouch%3A+BKC+Validation+Test+Procedures)   
  - [validation ownership matrix](https://wiki.ith.intel.com/display/CPS/Intel%28R%29+Dynamic+Tuning+Technology+Feature+Validation+Ownership)  
- [DPTF Home](https://wiki.ith.intel.com/display/DPTF/Home)  basic overview / architecture  
  - [DPTF Policies](https://wiki.ith.intel.com/display/DPTF/DPTF+Policies)  
  - [Tuning assistant for PB](https://wiki.ith.intel.com/display/DPTF/Power+Boss+Tuning+Assistant)  
- [c TDP policy](https://wiki.ith.intel.com/display/DPTF/ConfigTDP+Policy+Testing)  
- [temp chamber](https://wiki.ith.intel.com/display/DPTF/Temperature+Chamber)  
- [RFIM validation](https://wiki.ith.intel.com/display/DPTF/RFIM+Validation+Page)  
- virtual sensor
  - [data import](https://wiki.ith.intel.com/display/DPTF/Virtual+Sensor+Data+import+to+UI)  
  - [thermal design studio ](https://wiki.ith.intel.com/display/DPTF/Virtual+Sensor+-+Thermal+Design+Studio)
- [Wireless Paticipant](https://wiki.ith.intel.com/display/DPTF/Wireless+Participant+%28WLAN%29+-+WiFi+Testing)   Wifi Testing 
- [Storage Participant](https://wiki.ith.intel.com/display/DPTF/Storage+Participant)  
- [Charger Participant](https://wiki.ith.intel.com/display/DPTF/Charger+Participant)  
- [DPW - Dynamic Participen Wizard](https://wiki.ith.intel.com/display/DPTF/Dynamic+Participant+Wizard)  
- [DPTF Test Strategy](https://wiki.ith.intel.com/display/DPTF/Test+Strategy)   PPT files
- [BKM](https://wiki.ith.intel.com/display/ESIF/BKM)  
    - New Team Member DevChecklist
    - Perforce BKMs
    - Linux Perforce client installation
    - ACPI Event information (how to force)
    - Rebuilding DSP DataVault
    - Chrome SDK Issues Workarounds
    - Using Conjure
    - Trace Logging Configuration
    - DPTF Startup Configuration
    - Data Vaults Overview
    - [how to test exported data vault](https://wiki.ith.intel.com/display/DPTF/How+to+test+an+exported+data+vault)  
    - ESIF Code Review Process
    - Building DPTF ESIF
    - Primitive Decoding
    - UMDF Driver Debugging
    - ESIF Code Style Guide
    - Making ESIF Upstreamable
    - Setting up Chrome SDK And Building ChromeOS
    - VM Images
    - DSP Adding, Modifying, and Generating
    - Updating Copyright Notices 
    - Basic DPTF Testing User Guide for Coreboot/EC Engineers
    - Step by Step Approach for Coreboot/EC engineers to test basic DPTF functionality
    - Build and Test Image Remotely on Chrome-based Targets
    - Capturing ETW Traces from ESIF
    - Working with Microsoft eWDK BuildKits
- [DPTF Framework](https://wiki.ith.intel.com/display/DPTF/DPTF+Framework)  
  - Code structure
- [release cycle](https://sx-cyclr-rem-vm:7072/index.html )  
- [DPTF Testing](https://wiki.ith.intel.com/display/DPTF/DPTF+Testing)  
    - BIOS
    - DPTF Security
    - DPTF Participants
    - DPTF Tests
    - DPTF Features
    - DPTF UI
    - ESIF Event/Driver tracing and logging
    - HID Event Filter Driver Testing
    - Tips & Tricks 
      - [Acronyms](https://wiki.ith.intel.com/display/DPTF/DPTF+Acronyms)  
      - [DPTF control knobs](https://wiki.ith.intel.com/pages/viewpage.action?pageId=634127056)  
    - Sensors
- [DPTF Validation](https://wiki.ith.intel.com/display/DPTF/Validation)  Collections of guides
  - [New hire check list](https://wiki.ith.intel.com/display/DPTF/New+Hire+Checklist)  ramp up
  - [new employee information](https://wiki.ith.intel.com/display/DPTF/Employee+Checklist)  PPT template, orgchart
  - [validation on boarding](https://wiki.ith.intel.com/display/DPTF/Dynamic+Tuning+%28DPTF%29+On-Boarding)  
    - Flashing and configureing BIOS
    - Wimager
    - Installing DPTF
    - Select SPI Flash Programming Solution
    - SF600 Plus SPI Flash IC Programmer 
    - need to download DediProg Software and USB Driver  (1st and 3rd item in the list) 
  - [BIOS settings](https://wiki.ith.intel.com/display/DPTF/BIOS+-+DPTF+related+settings)  
  - [CPS Learnings: Jira Training (session 1)](https://wiki.ith.intel.com/download/attachments/1259099934/Session1-Test%20Management_rev1.pptx?api=v2)  ppt direct download
  - [TART](https://wiki.ith.intel.com/display/DPTF/TART+-+Telemetry+Analytics+Reporting+Tool)  
     - telemetry Analytics Reporting Tool
  - [Validation Team](https://wiki.ith.intel.com/display/DPTF/Validation+Team)  
    - roles and responsibility
    - validation expertise Matrix
  - [WHQL](https://wiki.ith.intel.com/display/DPTF/WHQL+-+Windows+Hardware+Quality+Labs+testing)  
    - Windows Hardware Quality Labs Testing
  - [WER Crash Check](https://wiki.ith.intel.com/display/DPTF/WER+Crash+Check)  
  - [Debug Methods](https://wiki.ith.intel.com/display/DPTF/Debug+methods)  
- [c-state residency](https://wiki.ith.intel.com/pages/viewpage.action?pageId=1032233500)  
- [Security Validation](https://wiki.ith.intel.com/pages/viewpage.action?pageId=1080562241)  Security Tools
  - [CPS security training](https://wiki.ith.intel.com/x/THR4RQ)  

#### Automation 
- [Automated Testing](https://wiki.ith.intel.com/display/DPTF/Automated+Testing)  
  - Overall links
- [Automation Triage](https://wiki.ith.intel.com/display/DPTF/Automation+Triage)  
- [Automation ENV setup](https://wiki.ith.intel.com/display/DPTF/New+Automation+Developer+Environment+Setup)  
  - Setting up the automation environment  
- [DPTF validation Automation](https://wiki.ith.intel.com/display/DPTF/Introduction+to+DPTF+Validation+Automation)  
- [Infrastructure](https://wiki.ith.intel.com/display/DPTF/DPTF+Validation+Automation+Infrastructure+Introduction)  
- [TeamCity and perforce](https://wiki.ith.intel.com/display/DPTF/TeamCity+and+Perforce+Process)  
- [Teamcity Jenkins gitlab](https://wiki.ith.intel.com/display/DPTF/TeamCity%2C+Jenkins%2C+and+GitLab+Process)  
- [duplicate function](http://10.23.244.154:5000/)  To find duplicate in automation. 
- [Automated Testing](https://wiki.ith.intel.com/display/DPTF/Automated+Testing)  
- [Coding Standard](https://wiki.ith.intel.com/display/DPTF/Automation+Coding+Standards)  
- [Remote Automation Specifics](https://wiki.ith.intel.com/display/DPTF/Remote+Automation+Specifics)  
- [local system setup](https://wiki.ith.intel.com/pages/viewpage.action?pageId=742230898)  
- [feature setup using SpecFlow Hooks](https://wiki.ith.intel.com/display/DPTF/Feature+Setup+Using+SpecFlow+Hooks)  
- [Gherkin Help](http://behat.readthedocs.org/en/v2.5/guides/1.gherkin.html)  
- [new platform](https://wiki.ith.intel.com/display/DPTF/New+Platform+Process)  

### Training
- [DPTF Training](https://wiki.ith.intel.com/display/DPTF/Training)  
  - [virtual ftf](https://wiki.ith.intel.com/display/DPTF/Virtual+F2F) RFIM / Optane / BIOS Lite / UVTH / Multibattery / new AP feature/ Power Boss Tuning / CCE / Dynamic Participant / Diagnostic Settings / Project Elsa  
  - [Software Desgin](https://wiki.ith.intel.com/display/DPTF/Software+Design)  
  - [DPTF framework](https://wiki.ith.intel.com/display/DPTF/DPTF+Framework)  
- [git jenkin artifact training OWR - One Windows Recipe 2.0 ](https://wiki.ith.intel.com/display/owr2/OWR+2.0+Training)  
- [Jenkin Tutorial](https://wiki.ith.intel.com/display/DPTF/Jenkins+Tutorial)  
- [jenkins world](https://wiki.ith.intel.com/display/owr2/Jenkins+World+2018+-+Notes)  
- [Validating DPTF controls/knobs E2E](https://wiki.ith.intel.com/pages/viewpage.action?pageId=634127056)  
  - PL(power Limit) / Time window 
- [Git for Visual Studio](https://wiki.ith.intel.com/display/owr2/Visual+Studio+Git+User+Interface)  
- [GIT with visual studio hands on](https://wiki.ith.intel.com/display/DPTF/Hands-on+Exercise)  
- [Power Limit](https://wiki.ith.intel.com/pages/viewpage.action?pageId=831423568)  
- [Power Limit wiki](https://wiki.ith.intel.com/display/DPTF/PSys+Power+Limits )  
- [Power and Turbo](https://wiki.ith.intel.com/display/DPTF/Understanding+Power+and+Turbo+Related+Control+Parameters)  
  - PL1 
  - TAU 
  - PL2 
- [git cheat sheet](https://wiki.ith.intel.com/pages/diffpagesbyversion.action?pageId=1059500155&selectedPageVersions=2&selectedPageVersions=3)  
- [git basics](https://wiki.ith.intel.com/display/owr2/Git+and+GitLab+Training#GitandGitLabTraining-Gitbasics)  
- [artifactory jfrog](https://wiki.ith.intel.com/display/owr2/Artifactory+Training)  
- [exploratory test](https://wiki.ith.intel.com/display/DPTF/Exploratory+Testing)  
- [test Strategy](https://wiki.ith.intel.com/display/DPTF/Test+Strategy)  
- [CCE training](https://wiki.ith.intel.com/display/DPTF/2019+CCE+Training+Series)  

### How To

- [Story Verification process ](https://wiki.ith.intel.com/display/DPTF/Story+Verification+Process )  
- [creating test case in jama](https://wiki.ith.intel.com/display/DPTF/Test+Case+Development+v2)  
- [defect Management Process](https://wiki.ith.intel.com/display/DPTF/Defect+Management+Process)  
- [HSD Process](https://wiki.ith.intel.com/display/DPTF/HSD+Process+-+Dynamic+Tuning)  
- [IO Meter - Bench Marking Tool for NVMe devices](https://wiki.ith.intel.com/display/DPTF/IO+Meter+-+Bench+Marking+Tool+for+NVMe+devices)  
- [Dynamic Participant wizard](https://wiki.ith.intel.com/display/DPTF/Dynamic+Participant+Wizard)  
- [Power Boss Tuning Assistant](https://wiki.ith.intel.com/display/DPTF/Power+Boss+Tuning+Assistant)  
- [KBL-G Board bring up](https://wiki.ith.intel.com/display/DPTF/Kaby+Lake-G+-+KBL-G)  
- [Regex for C#](http://www.tutorialspoint.com/csharp/csharp_regular_expressions.htm)  
- [DPTF Testing for Coreboot/EC Engineers](https://wiki.ith.intel.com/pages/viewpage.action?pageId=467148884)  
- [usecase tortoise git](https://wiki.ith.intel.com/display/owr2/DPTF+Use+Cases+Using+TortoiseGit)  
- [simics virtual platfor](https://wiki.ith.intel.com/display/DPTF/Simics+Virtual+Platform)  
    - How-To: Install and Run Simics (for GSD and other platforms)  
    - How to Install and Run Simics for DPTF validation (PC)  
    - How to Access and Run Simics in the Farm  
- [sx cycler details](https://wiki.ith.intel.com/display/DPTF/Sx+Cycler+Details)  
- [how to](https://wiki.ith.intel.com/display/DPTF/How-To+Documents)  
    - How to: Setup build environment
    - How-To: Generate ESIF application SDK header files from a DSP.
    - How-To: Install and Run Simics (for GSD and other platforms)
    - How to Install and Run Simics for DPTF validation (PC)
    - How To: Access and Run Simics in the Farm
    - How To Capture BIOS Logs Using Serial Cable
    - How-To: Access Windows Error Report (WER) Data
    - How To: Capture a DPTF configuration
- [Test Plan Creation](https://wiki.ith.intel.com/display/DPTF/Test+Plan+Creation)  
- [Debug Method](https://wiki.ith.intel.com/display/DPTF/Debug+methods)  
  - flash pd controller 
  - IFWI stithcing 
- [DPTF logs](https://wiki.ith.intel.com/pages/viewpage.action?pageId=1269216092)  
  - Enable / collect DPTF logs.
- [logman commands](https://wiki.ith.intel.com/display/ESIF/ESIF+Event+Tracing+for+Windows+%28ETW%29+Support)  Mainly esif commands  
- [OEM Value](https://wiki.ith.intel.com/display/DPTF/AP+-+Changing+OEM+variable+values)  Changing OEM Variable Values  
- [DPTF Polling Mode How to pull polling values from ETW trace log](https://wiki.ith.intel.com/display/DPTF/DPTF+Polling+Mode+-+How+to+pull+polling+values+from+a+ETW+trace+log)  
- [DCFG testing](https://wiki.ith.intel.com/display/DPTF/DCFG+Testing)  
- [dsp compiler](https://wiki.ith.intel.com/pages/viewpage.action?pageId=974227958)  
- [GDDV testing](https://wiki.ith.intel.com/display/DPTF/GDDV+Testing)  
- [HDC Policy testing](https://wiki.ith.intel.com/display/DPTF/HDC+Policy+Testing)  
- [Interrupt-polling Interrupt Mode vs Polling Mode Testing ](https://wiki.ith.intel.com/display/DPTF/Interrupt+Mode+vs+Polling+Mode+Testing)  
- [IO Meter Bench Marking tool for NVMe](https://wiki.ith.intel.com/display/DPTF/IO+Meter+-+Bench+Marking+Tool+for+NVMe+devices)  
- [LPM testing](https://wiki.ith.intel.com/display/DPTF/LPM+Testing)  
- [Optane setup](https://wiki.ith.intel.com/display/DPTF/Optane+Setup)  
- [DPTF PID How to Pull PID values from DPTF trace log  ](https://wiki.ith.intel.com/display/DPTF/DPTF+PID+-+How+to+pull+PID+values+from+DPTF+trace+log)  
- [Responsiveness & velocity](https://wiki.ith.intel.com/pages/viewpage.action?pageId=634127164)  
- [RST validation](https://wiki.ith.intel.com/display/DPTF/RST+Validation)  
- [SOC workload](https://wiki.ith.intel.com/display/DPTF/SOC+Workload)  
- [SX cycling testing](https://wiki.ith.intel.com/display/DPTF/Sx+Cycling+Testing)  
- [Secure Web Socket](https://wiki.ith.intel.com/pages/viewpage.action?pageId=568233452)  
  - Setup DCA/QHST
  
#### Automation

- [Automation Triage](https://wiki.ith.intel.com/display/DPTF/Automation+Triage)  
- [Automation Hardware](https://wiki.ith.intel.com/display/DPTF/Automation+Hardware)  
- [Automation Reimaging](https://wiki.ith.intel.com/display/DPTF/Automation+Reimaging)  
- [TestCase Development](https://wiki.ith.intel.com/display/DPTF/Test+Case+Development+v2)  
- [Automation Servers](https://wiki.ith.intel.com/display/DPTF/DPTF+Automation+Servers)  
- [Nunit Test Automation](https://wiki.ith.intel.com/display/DPTF/Developing+NUnit+Test+Automation+Code)  
- [GTEST Automation](https://wiki.ith.intel.com/display/DPTF/Developing+GTEST+Automation+Code)  
- [mark test automated](https://wiki.ith.intel.com/display/DPTF/Process+For+Marking+Test+As+Automated)  
- [Run Test on Teamcity](https://wiki.ith.intel.com/display/DPTF/Running+Tests+in+TeamCity)  
- [Checkin Process](https://wiki.ith.intel.com/display/DPTF/Automation+Code+Checkin+Process)  
- [Android NDK development environment Setup](https://wiki.ith.intel.com/display/DPTF/Android+NDK+Development+Environment+Setup)  
- [Regex for C#](http://www.tutorialspoint.com/csharp/csharp_regular_expressions.htm)  


#### ESIF

- [ESIF command](https://wiki.ith.intel.com/display/DPTF/Commonly+Used+ESIF+Commands)  
- [Esif Development page](https://wiki.ith.intel.com/display/ESIF/ESIF+Development+Page)  
- [Event Tracing](https://wiki.ith.intel.com/display/ESIF/ESIF+Event+Tracing+for+Windows+%28ETW%29+Support)  
- [DataVault](https://wiki.ith.intel.com/display/ESIF/Data+Vault+Overview)  
- [How to test datavault dv](https://wiki.ith.intel.com/display/DPTF/How+to+test+an+exported+data+vault)  
- [my ESIF all together](esif.md)  

#### ESIF Event/Driver tracing and logging
- [DPTF setting Capture](https://wiki.ith.intel.com/display/DPTF/DPTF+Settings+Capture)
- [ESIF Event Tracing for Windows -ETW Support](https://wiki.ith.intel.com/display/ESIF/ESIF+Event+Tracing+for+Windows+%28ETW%29+Support)  
- [How to use trace messages](https://wiki.ith.intel.com/display/DPTF/How+to+use+trace+messages)  
- [Participant Logging Commands](https://wiki.ith.intel.com/display/DPTF/Participant+Logging+Commands)  

#### Tools 

- [IO Meter BenchMarking Tool](https://wiki.ith.intel.com/display/DPTF/IO+Meter+-+Bench+Marking+Tool+for+NVMe+devices)
- [Virtual Sensor](https://wiki.ith.intel.com/display/DPTF/Virtual+Sensor+Help+and+Calculator)  
- [PB data Import](https://wiki.ith.intel.com/display/DPTF/Power+Boss+Data+Import+Tool)  
- [PB hot key](https://wiki.ith.intel.com/display/DPTF/Power+Boss+Hot+Keys)  
- [iperf3](https://iperf.fr/iperf-download.php#windows)  
- [DediProg software:](https://www.dediprog.com/pd/spi-flash-solution/sf100)  
- [Data Migration Tool](https://hsdes.intel.com/appstore/data-migrator/#/home)  


### DPTF UI
- [UI Timing/Responsiveness Targets](https://wiki.ith.intel.com/download/attachments/634126863/ui-responsiveness-targets.xlsx?version=1&modificationDate=1501687626693&api=v2)   excel file download
- [Differences Between DPTF UIv1 & UIv2](https://wiki.ith.intel.com/pages/viewpage.action?pageId=998484255)  
- [UI Reference Table](https://wiki.ith.intel.com/display/DPTF/UI+Reference+Table)  information about the tables of policy.





### Tips & Tricks 

- [DPTF Acronyms](https://wiki.ith.intel.com/display/DPTF/DPTF+Acronyms)  
- [Understanding Turbo Related Control Parameters](https://wiki.ith.intel.com/display/DPTF/Understanding+Power+and+Turbo+Related+Control+Parameters)  
- [Validating DPTF controls/knobs E2E](https://wiki.ith.intel.com/pages/viewpage.action?pageId=634127056)  
- [Windows Upgrade and Boot up tricks](https://wiki.ith.intel.com/display/DPTF/Windows+Upgrade+and+Boot+up+tricks)  





# Misc

### IP
|system|Name|ip|
|---|---|---|
|SUT1  KBL-G||10.23.242.250|
|SUT2 ICL-U|desktop-4oqfmic|10.23.243.216|
|lab PC|rahmanma-Desk - 10.23.240.228|
|SUT3|Desktop-ugpmksk - 10.23.243.81|

### File server location: 

     file://pcse-fs1/DPTF%20Validation/Automation  
    \\dptf-imager\imaging    
    \\dptf-imager\imager  
    \\chakotay\SoftVal\DPTF_tools  
    DPTF Test Results:  \\alice.hf.intel.com\dptf  
    Boot Manager Files:  \\orsvpd105\PDSE-Public\BIT_Imaging\Releases
    Specflow old version: \\chakotay\SoftVal\DPTF_tools\SpecFlow.DamageControl  
    Script to install dptf: \\chakotay.hf.intel.com\SoftVal\DPTF_tools\Update-DPTF-and-UI-teamcity.ps1
    Boot Manager Files:  \\orsvpd105\PDSE-Public\BIT_Imaging\Releases
    public fileserver location: \\pcse-fs1\IntelPublic\#To Be Deleted
  
### Intel General Links
- [goto/careerservices]()
- [goto/dot](https://ease.intel.com/es/DOT/Default.aspx?LinkID=24100)  
- [goto/bluehire](https://bluehire.intel.com/)  
- [goto/careerzone](https://employeecontent.intel.com/content/hr/learning/empl-dev/career-zone.html)  
- [goto/degreed](https://degreed.com/atikeee/dashboard#/feed)  
- [goto/careerconnections](https://careerconnections.intel.com/)  
- [goto/jobsinside](https://www.applytracking.com/optin.aspx?c=39FaE%2bMO99yGYL6JYdgCCg%2bR5ph7OEcf&tags=InternalMobility&utm_campaign=Internal%20Mobility&utm_medium=Intel-Owned%20Properties&utm_source=Direct%20Acccess&utm_content=Jobs%20Inside%20GoTo%20Link)  

### Windows Core OS (WCOS)
- [WCOS Wiki page](https://wiki.ith.intel.com/display/UniversalDriversFAQ/Windows+Core+OS)   
- [WCOS Overview training](https://videoportal.intel.com/media/WCOS+Overview+for+CCE+-+presented+by+Michael+Zhu+-+MTC+-+ww21+May+22+2019/0_79e8oeph/)  
- [State Separation](https://wiki.ith.intel.com/display/UniversalDriversFAQ/State+Separation)  
- [How to build WCOS CDG image?](https://wiki.ith.intel.com/pages/viewpage.action?pageId=1207039413)  
- [How to add driver to an existing WCOS image?](https://wiki.ith.intel.com/pages/viewpage.action?pageId=963949457)  

### Misc training
- [python](https://realpython.com/tutorials/best-practices/)  
- [AI / ML skills](https://wiki.ith.intel.com/pages/viewpage.action?pageId=1165522076)  

### HID Event Filter Driver Testing
- [HID & VB Drivers with Hotkeys](https://wiki.ith.intel.com/pages/viewpage.action?pageId=634127294)  

### iMBO 
- [validation goal](https://wiki.ith.intel.com/display/CPS/2019+iMBOs)  



# AGS access:

### JIRA
DevTools - JIRA - DPTF - QA
DevTools - JIRA - DPTF - Software Developer
DevTools - JIRA - DPTF - User
DevTools - JIRA - DPTF Architecture - JIRA - Software Developer
DevTools - JIRA - DPTF Validation - QA
DevTools - JIRA - DPTF Validation - Software Developer
DevTools - JIRA - DPTF Validation - User 

