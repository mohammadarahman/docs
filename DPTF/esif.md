# ESIF Commands
## Generic info
esif command line 

`c:\Windows\System32\DriverStore\FilreRpository\dptf_cpu.inf*\esif_uf.exe client`  

## Important Commands

Reloading DPTF
esif_uf.exe reload

Headless shell usage 
%windir%\system32\intel\dptf\esif_uf.exe client -c "trace module 4 dptf && trace route 4 log && trace level 4" –q


## Basic Commands

|command example|explaination|
|---------------|----|
|apps|Show list of apps|
|appstart ipfsrv|start ipfsrv * see below|
| parts|get parts information| 
| infofpc icl_proc|get information for CPU participent|
| dstn TCPU| select the part|
| dst &lt; participant id &gt; | select part|
| getp 14|getting temperature|
| setp 241 d0 255 12|set temp to 12&ordm; C|
| setp 382 D0 255 15000| set PMAX to 15000|
| getp 291| getting PMAX val|
| rstp 214| reset temp to default|
| setp 368 D0 255 100| set battery percent|
| getp 485 D0 255| get rfprofile SSC|
| setp 492 D0 255| set rfprofile SSC|
| setp 474 D0 255 10| set residency utilization|
| getp 443 D0 255| get the residency utilization|
| idsp| to get policy gui id use only one policy active|

> from client you can connect to IPF using ipfclient.

## Config Commands


|command example|explaination|
|---------------|----|
|config get @override *|get config override|
|config delete @override|delete config DPTF|
|config get @dptf *|get config DPTF|
|List Configuration Files and MetaData|	config files <filespec> [...]|
|Delete Configuration File|config drop <filename> [...]|
|Rename Configuration File|config rename <oldname> <newname>|
|Update Configuration File Description|config comment <filename> "Some Description"|
|Upload Configuration File|config upload [overwrite/append] <filename> <base64-encoding>|
|Reset to Factory Defaults|config gddv set @@factory|
|Set a GDDV Override (Activate Configuration File)|config gddv set <filename>|
|Remove a GDDV Override (Deactivate)|config gddv reset|
|Get Active Mode (Normal/Emulation)|config gddv mode|
|Get Active Status (Unchanged/Modified)|config gddv status|
|Get Active GDDV Hash|config hash @gddv|
|Get Active GDDV Description|config comment @gddv|
|Backup GDDV-related DataVaults|config gddv backup|
|Restore GDDV-related Datavaults|config gddv restore|
|Convert Binary GDDV file to ASL file|config asl encode <infile> <outfile>|
|Convert ASL file to Binary GDDV file|config asl decode <infile> <outfile>|


## Logging Command

|Paradigm|Command|
|---|---|
| Participant by name | participantlog start TCPU all all SEN2 all all SEN3 all all TPWR all all |
| Participant by LPID | participantlog start 14 all all 4 all all 6 all all 9 all all |
| Participant by combination of names and UPIDs | participantlog start TCPU all all 4 all all GEN1 all all 6 all all |
|select logging with capability|participantlog start TCPU D0 0xFFFBDCFF|
|schedule logging|participantlog schedule 3000 all|
| check capabilities|domains|

## Table Data Set

tableobject set <table_name> <participant_ID> <domain> <revision>:<row1col1data>[[, row1col2data>][, <row1col3data>]...]![<row2col1data>[[, <row2col2data>][, <row2col3data>]]!...]  
After the revision # and ':', the remaining data is the raw data for the table.  
The rows are separated by '!' characters, and the columns are separated by ',' characters.  
Any typo or mistake in this will result in a bad table loading (NO INPUT VALIDATION).  

|command example|explaination|
|---------------|----|
|tableobject set odvp 0 d0 0!0!0!0!0!1| set oem var|
|tableobject set psha 0 D0 01:\_SB_.MCPP,38,0xFFFFFFFF!\_SB_.PCI0.B0D4,9,2!\_SB_.DGFC,36,8!| set BIAS of CPU 20%, Graphics 80%| 
|tableobject set psha 0 D0 01:\_SB_.MCPP,38,0xFFFFFFFF!\_SB_.PCI0.B0D4,9,5!\_SB_.DGFC,36,5!|set BIAS of CPU 50%, Graphics 50%:| 
|tableobject get pppcc 46 D0 | 
## power boss related primitive

|Name|Method|Get|Set|Units|
|----|------|---|---|-----|
|Adapter Rating|ARTG|296|438|mW|
|Platform Rest of Power|PROP|298|437|mW|
|Battery Steady State|PBSS|294|383|mW|
|Battery Max Peak Power|PMAX|291|382|mW|
|AC Source Nominal Voltage|AVOL|412|413|mV|
|AC Source Nominal Current|ACUR|414|415|mA|
|AC Source %overload for 1ms @5% duty cycle|AP01|416|417|%|
|AC Source %overload for 2ms @10% duty cycle|AP02|418|419|%|
|AC Source %overload for 10ms @10% duty cycle|AP03|420|421|%|
|Bat_Resist|RBHF|511|512||
|BNL_Voltage|VBNL|513|514|mV|

## Power Share 

dstn MCP

|power share var|get primitive|set premative|
|---|---|---|
|PID Target|getp 38 D0 0 - getp 38 D0 200|setp 130 D0 0|
| Kp| getp 456 D0 255|setp 457 D0 255|
|Ki|getp 458 D0 255|setp 459 D0 255 |
|Tau or alpha?|getp 460 D0 255|setp 461 D0 255|
|Fast Polling Interval|getp 462 D0 255|setp 463 D0 255 |
|Slow Polling Interval|getp 464 D0 255|setp 465 D0 255 |
|Slow Poll Weighted AveragingConstant|getp 466 D0 255|setp 467 D0 255|
|Slow Poll Power Threshold|getp 479 D0 255|setp 480 D0 255|

Dstn TCPU

|power share var|get primitive|set premative|
|---|---|---|
|Processor Temperature Threshold|getp 468 D0 255|setp 469 D0 255|
|Processor Utilization Threshold|getp 470 D0 255|setp 471 D0 255 |

Dstn DGFC

|power share var|get primitive|set premative|
|---|---|---|
|Discrete Graphics Energy Threshold|getp 472 D0 255|setp 473 D0 255|
|Discrete Graphics UtilizationThreshold|getp 470 D0 255|setp 471 D0 255|
|Participant Utilization|getp 443 D0 255|setp 474 D0 255 |
|Participant Energy Counter|getp 128 D0 255|Just for Graphics: setp 476 D0 255|
|Participant Energy Unit|getp 123 D0 255|N/A|
|Participant Energy Counter Width|getp 475 D0 255|N/A|
|AC Peak Power| |setp 448 D0 255|
|DC Peak Power| |setp 452 D0 255|
|set gfx enegy threshold counter| |setp 453 D0 255|
|check interrupt fired | |setp 454 D0 255 1|

### Getting data ETW tracing for collecting powershare alg data

  Launch shell: esif_uf.exe client  
        Enable DPTF traces: trace module 4 dptf  
   Set trace route: trace route 4 log  
        Set trace level: trace level 4  

## app level command
|command|description|
|--|--|
|appstart dptf| start the DPTF application|
|appstop dptf|stop DPTF|
|web start| start webserver|
|web stop| stop webserver|


## mm command 
|command|Explaination|
|---|----|
|mm 66 f3 -w 1 -io|turn off fan for ICL/TGL|



## mm command 
|command|Explaination|
|---|----|
|mm 66 f3 -w 1 -io|turn off fan for ICL/TGL|


## paths
|command|description|
|--|--|
|paths| to check all different path|


## add participant
partsK is to see kernel participants

participant create ACPI IDG1 "desc"



## help

|command|description|
|--|--|
|actions| all dsp actions|
|actionsk|all kenel|
|actionsu|all user|
|devices <action> | alldevice by UPE|
|event [enable|disable] <eventType> [participant] [domin] | enable disable send event. |
	selene.alvarado.legaria@intel.com