# ETW Event Tracing for windows. 

- in ETW there are 3 types of participants. 
  - Providers - Generate the event and tracing information. 
  - Consumers - listens for event and messages. 
  - Controllers - Enables providers and controls routing data.
- 
- 

## provider

- esiflfetw
- dptfacpi
- dptfcpu
- dptfpch
- esifumdf
- esifumdf2

## Tools for tracing. 

- logman 

> default storing location: c:\windows\system32
> logman create trace SessionName -p ProviderName keywordMask level -o OutputFilename.etl  
> Example: logman create trace sess1 -p EsifUmdf2EtwProvider 0xFFFFFFFF 5 -o trace.etl  
logman create trace lf_all_sess -p EsifLfEtwProvider 0x200000 5 -o lf_all_1.etl
> start Capture: logman start SessionName  
> Stop Capture : logman stop SessionName  
> logman update SessionName -p ProviderName keywordMask level -o OutputFilename.etl  

[logman commands](https://wiki.ith.intel.com/display/ESIF/ESIF+Event+Tracing+for+Windows+%28ETW%29+Support)  
[logging on boot](https://wiki.ith.intel.com/display/DPTF/ETW%3A+Enable+ETW+Logging+at+boot+on+an+existing+system+via+the+AutoLogger)  

|function| command|
|---|---|
|create trace|logman create trace sessionA –p EsifUmdf2EtwProvider 0x8000005 –o sessionA.etl|
|start session|logman start sessionA|
|stop session|logman stop sessionA|
|process trace| tracerpt sessionA_000001.etl -o sessionA.csv -of CSV|
|get list of logging| logman query|

- tracerpt   

>This is needed for the log to format as human readable. 
> tracerpt filename.etl -o outputFilename.csv -of CSV  
> XML output: tracerpt filename.etl  
> tracerpt filename.etl -o outputFilename.csv -of CSV  

- XPERF

> xperf -start ms -on Microsoft-Windows-LimitsManagement -BufferSize 1024 -MinBuffers 10 -MaxBuffers 16  
> xperf -capturestate ms Microsoft-Windows-LimitsManagement  
> xperf -stop ms -d filename.etl  / this file will be stored in c:  




