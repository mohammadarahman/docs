# Policies
## [Critical Policy](https://wiki.ith.intel.com/display/owr2/DPTF+Use+Cases+Using+TortoiseGit)

  - It turns the system off under extreme thermal condition.  
  - Upto 3 trip points per participants.   
    - Warm (CR3)  
      - sleep (S3)  
      - Hibernate (S4) for connected standby  
    - Hot (HOT)  
      - Hibernate (S4)  
    - Critical (CRT)  
      - Shutdown (S5)  


## [Active Policy](https://wiki.ith.intel.com/display/DPTF/Active+Policy) 
  
  - Actively Cooling the system using FAN. Policy 1 or 2 only one at a time will be active.  
  - Active Relation Table (ART)  
    - 10 trip point possible from AC0~9  
    - only this to configure in the policy   
  - A source participant is fan which can cool the system actively.
  - Manager status has the trip points table  

### Table
#### ART 

|target |source |AC0|AC1|AC2|AC3|AC4|AC5|AC6|AC7|AC8|AC9|
|-------|-------|---|---|---|---|---|---|---|---|---|---|
|CPU|FAN|100|80|50|---|---|---|---|---|---|---|


## [Active Policy2](https://wiki.ith.intel.com/display/DPTF/Active+Policy+2)
  
  - Active Control Point RelationShip Table (ACPR) 
  - ACPR defines periodic change of active cooling  
  - It has additional Control Knob to choose RPM or percentage fan control
  - there are two mode Stepwise which allows more smooth change and directmode  

### Table
#### ACPR

| Targe | Source | ControlKnob | Trip point | control point | control increament | sample period |
|-------|--------|-------------|------------|---------------|--------------------|---------------|
| SEN | TFN | RPM | 40 | 5000 | 10 | 5 |
| SEN | TFN | RPM | 50 | 10000 | 10 | 5 |



## [Passive Policy](https://wiki.ith.intel.com/display/DPTF/passive+Policy) 

 - Controling the power performance to cool down  
 - Relies on Relationship table (TRT)  


### limiting algorithm

```
if temperature > PSV:
    monitor target
    for each source target can limit:
        if the source is available for requests from the target:
            if source == target:
                if there is a package domain with controls to limit:
                    choose the package domain.
                else:
                    choose domains that don't report temperature.
                    choose the domain with the highest temperature.
            if source != target:
                if there is a package domain with controls to limit:
                    choose the package domain.
                else:
                    choose domains that do not report utilization.
                    choose the domain with the highest utilization and priority.
            request limit to the next available control knob for each domain chosen for the target.
        schedule a callback after the sample period for the target and source relationship.
        limit the source if it has not been adjusted within the minimum active sample period.

```

### unlimiting algorithm

```
if temperature < PSV:
    for each source target can unlimit:
        if the source is available for requests from the target:
            if source == target:
                choose domains that do not report temperature.
                choose the domain with the lowest temperature.
                if no domains were chosen:
                    choose the package domain.
            if source != target:
                choose domains with the lowest priority.
                if no domains were chosen:
                    choose the package domain.
            request unlimit to the next available control knob for each domain chosen for the target.
            schedule a callback after the sample period for the target and source relationship.
        unlimit the source if it has not been adjusted within the minimum active sample period
    if no sources remain to be unlimited:
        if temperature >= PSV - hysteresis:
            schedule a callback after the shortest sample period for the target.
        else:
            stop monitoring target.
            remove all outstanding control requests for target.
```

### Table
#### TRT 

|Target|Source|Influence|Sample Period| 
|------|------|---------|-------------|
|storage|CPU|8|20| 
|CPU|CPU|8|20| 

### Control Limit 
 
 - Power controls
 - P-state controls + Core Controls  (if core control can be limited limit them)
 - T-state controls
 - Display controls  
 `unlimit is opposite`

## [Passive Policy2](https://wiki.ith.intel.com/display/DPTF/passive+Policy+2)  

 - Direct and stepwise control  
 - PSVT Passive Table
 - value should be closed rounded multiple of step size  
 - When multiple targets are requesting different values from the same source, the source control will arbitrate on the side of 'limiting' itself.  
 - Unlike direct mode, stepwise mode is more of a gradual move towards its preferred state.  
 - Highest priority lower number.  
 - When LIMITING: highest priority (highest number) is limited first  
 - When UNLIMITING: lowest priority is unlimited first  
 - Mainly useful for poewer limiting.  

### Table
#### PSVT 

| Targe | trip point | Sample period | Priority | Source | Domain | Control Knob | Limit | StepSize | Limit Coeff | Unlimit Coeff |
|-------|------------|---------------|----------|--------|---------------|--------------|-------|----------|-------------|---------------|
| CPU | 50 | 5 | 20 | TCPU | Multifunction | PL1 | MAX | 500 | 10 | 10 |
| CPU | 50 | 5 | 20 | TCPU | Multifunction | PL1 | MAX | 1 | 10 | 10 |  



## [Adaptive Performance](https://wiki.ith.intel.com/display/DPTF/Adaptive+Performance+Policy)  

 - dynamically adjust the thermal envelope by detecting the system usage mode and provide the user with extra performance benefits  
 - it can be used on a system without requiring extra work in the BIOS  
 - APCT and APAT table defines the condition and corresponding action  
 - max 10 minterms to combine conditions for complex one.  it can end with `And` or `FOR`  
 - only one action will be taken  
 - for is being used for time condition.  
 - APAT can alter any other policy table.  
 - AP does not restore any capabilities
 - Policy of Policies
 - All action will be executed if condition is true and points to same action. 

### Features Training. 
  - config set @dptf/features/soc_workload 1
  - idle / semi active / bursty/ sustained / battery life
  - These uses avg power / C0 residency/ Transition count/  TDP
  - EPP(Energy Performance Preference) sensitivity Hint
  - on table detection - 0- unknown/1-in motion off/2
  - Notify Platform
    - this is to send notification to bios. 

### Supported conditions

 - Display Orientation  
 - Platform/Device Orientation  
 - In Motion  
 - WorkLoad  
 - Dock Mode  
 - Cooling Mode  
 - Power Source  
 - Lid State  
 - Platform Type  
 - Aggregate Battery Percentage  
 - OEM Variables  
 - Power Scheme Personality  
 - Screen State  
 - APPC Temperature with/witout hysteresis condition
 - Time  
 - Mixed Reality  
 - User Presence  
 - Temperature with / without hysteresis  
 - Power slider  
 - SOC workload  

### Tables

#### APCT

 It will point to one row in action tably by action. It might contains 10 minterms. And FOR will be considered as different minterms.  

|Action|Condition|Participant|Domain|Comparator|Argument|Operator|  
|------|---------|-----------|------|---------|---------|--------|  
|1|Power Slider|IETM|Other|==|Better Performance|AND|  


#### APAT

 It will contain action to trigger from the condition table and multiple participant action can be tied with it.  

 |Action Set|Participent|Domain|Code|Argument|
 |--|--|--|--|--|
 |1|CPU|Multifunction|PL1|15000|

#### WorkLoad Hint Configuration

 Can be used for checking with application and take action based on the application. 

|Workload Hint Value| Application Names|
|----|----|
|1|notepad.exe|


## [Power Boss](https://wiki.ith.intel.com/display/DPTF/Power+Boss+Policy)  

- Condition driven policy that adjusts the peak and steady state power draw of the platform components as a power delivery capability for the platform changes.  
- The goal of the policy is to prevent platform shutdown due to a power “brown out”  
- PBCT and PBAT table defines the condition and corresponding action 
- it can be used on a system without requiring extra work in the BIOS  
- The Power Boss policy does not restore any capabilities
- The Requested Values table shows all the requests that the policy successfully made to the DPTF manager and will show a "FAILED" message if that action failed.
- to add default condition add **last row** in PBCT with condition **No Op: Take Default Action**

### Supported conditions

- Power Source  
- Aggregate Battery Percentage  
- Battery Max Peak Power  
- Platform Power Source  
- Adapter Power Rating  
- Charger Type  
- Rest of Platform Power  
- Battery State  
- Battery Present Rate  
- Battery Remaining Capacity  
- Battery Present Voltage  
- Battery Sustained Peak Power  
- Battery Cycle Count  
- Last Full Charge Capacity  
- Design Capacity  
- OEM Variables  
- AC Volt  
- AC Current  
- AC Peak Percentage  (1/2/10ms)
  - 0~250%
  - Overload for 1/2/10ms @ 10% duty cycle
- Battery Count  
- Power Slider  


### Supported Actions 

And here is a list of all supported action codes for PB:

- PL1MAX  
- PL1MIN  
- PL1STEP  
- PL1PowerLimit  
- PL2PowerLimit  
- PL3PowerLimit  
- PL4PowerLimit  
- PL1TimeWindow  
- PL3TimeWindow  
- PL3DutyCycle  
- PSysPL1Limit  
- PSysPL2Limit  
- PSysPL3Limit  
- PSysPL1TimeWindow  
- PSysPL3TimeWindow  
- PSysPL3DutyCycle  
- CoreControlLpo  
- DisplayBrightness  
- PerformanceState- P-state
- ACPeakPower  
- DCPeakPower  
- UsbcPowerLimitPort1, UsbcPowerLimitPort2, ..., UsbcPowerLimitPort8  
- UVTH  
- PL4AndUVTH  

### different scenario  

|Scenario | Expectations|
|----|----|
|set an invalid value| Value is added to the "Requested Values" but shows "FAILED" since the action will fail|
|set value outside the range| value snapped to the allowable range before being requested. snapped value will be in the table.|
|set a valid value after invalid one| request updated to show failed. arbitrator status tab will show valid request|

### TABLES
#### PBCT

 It will point to one row in action tably by action. It might contains 10 minterms. And FOR will be considered as different minterms.  

|Action|Condition|Participant|Domain|Comparator|Argument|Operator|  
|------|---------|-----------|------|---------|---------|--------|  
|1|Power Source|IETM|Other|==|AC|AND|  
|2|Power Source|IETM|Other|==|DC|AND|  

#### PBAT

 It will contain action to trigger from the condition table and multiple participant action can be tied with it.  

 |Action Set|Participent|Domain|Code|Argument|
 |--|--|--|--|--|
 |1|CPU|Multifunction|PL1|15000|
 |2|CPU|Multifunction|PL1|PBMT1|

### PBMT
- Power Boss Math Table contains all the input for the equation to be applied. 
- Naming convention for the name of table. 
  - first Digit -> DC=0 ; AC in watts =1; AC in V and I = 2
  - second & third -> PL1 =01, PL2 = 02; PL3 = 03, PL4 = 04; PsysPL1 = 10, PsysPL2 =20, PsysPL3 = 30;
  - forth - Battery state


### VTMT
- Voltage Threshold Math Table contains all input for voltage calculation.

### Extra. 
|what|where|
|--|--|
|excel for math calculation|\\\chakotay\SoftVal\DPTF_tools\_Policies\PowerBoss\Power_Boss_Testing_Aids|
|tuning assistant link|[link](https://wiki.ith.intel.com/display/DPTF/Power+Boss+Tuning+Assistant)|


## [Virtual Sensor Policy ](https://wiki.ith.intel.com/display/DPTF/Virtual+Sensor+Policy)  

- Virtual sensor participant represents a virtual or ambient temperature sensor that implements intel developed estimation algorithms to calculate the virtual temperature. 
- [Virtual sensor help and calculator](https://wiki.ith.intel.com/display/DPTF/Virtual+Sensor+Help+and+Calculator) 
- [Virtual Sensor calculator](https://wiki.ith.intel.com/download/attachments/632885995/UIv2_Tested_VS-Calculator.xlsx?version=1&modificationDate=1542738257223&api=v2) 
  - \\\chakotay\SoftVal\DPTF_tools\_Policies\VirtualSensor\Virtual_Sensor_Calc
- calculation of average
  - avg(t) = alpha x curVal + ((1-alpha) x avg(t-1))
  - avg(0) = curVal(0)
- virtual temp
  - Vir_Temp = Sum( coeff x operation x avg)  - for all target participents
- Virtual sensor behaves like hardware sensor But they have 2 tables
  - VSCT - Calibration Table
  - VSPT - Polling Table.


### Tables
#### VSCT

|Target|Domain|Coefficent Type|Coefficient|Operation|Alpha|TriggerPoint|  
|------|---------|-----------|------|---------|---------|--------|  
|TCPU|Multifunction|Temperature|500|Addition|700|20|  
|sen2|Other|Temperature|600|Subtraction|300|30|  

- Coefficient type options
  - Constant
  - Power
  - Temperature
- Alpha  is gain. 

### VSPT
this table data is 1/10th precision.
|temp|sample period|
|--|--|
|29.9|30|
|39.2|10|
|49.9|1|

### Polling vs One-Time Calculation

1. Initializing the temperature on DPTF start. This is a one-time calculation that is performed each time a new target comes online and is used to calculate the virtual temperature.
2. If no trigger points exist in the VSCT at initialization, begin polling. If all trigger points are 'X' or invalid, polling can begin based on the temperature calculated at initialization.
3. When the VSCT table is changed, the virtual sensor re-evaluates all the targets in its table then re-initializes its temperature value as a one-time calculation. If no triggers exist, it begins to poll in order to calculate temperature.
4. If one or more trigger points are crossed, begin polling until all trigger points are uncrossed.
5. A one-time calculation can be forced at any time by sending DPTF the recalculation event. Details for that are in the BIOS Writer's Guide.


## Dynamic Participent 
- User can not create two disply so for creating a dynamic participent user will have to disable display participent from bios. 
- 



## [RFIM](https://wiki.ith.intel.com/display/DPTF/RFIM+Policy) (RF Interference Mitigation)
- FIVR (fully integrated Voltage Regulator) 
- wifi / WWAN 
- switching frequency so that it doesnt interfere
- No Hardware requirement. 
- SSC - spread spectrum clocking frequency. 
- wifi temperature shows -136 when it is turned off. 


## [Power Share](https://wiki.ith.intel.com/display/DPTF/Power+Share+Policy)  
- rebalance power to CPU and graphics 
- kabylake.
- kabylake MCP -> intel CPU +AltoDie (Graphics and HBM)
- Utilization and Energy
- set CPU Power and set GFX Power. 
- PID Target 
- KP 
- Ki
- Alpha
- Fast polling interval. (100ms)
- Slow Polling interval (10s)
- GFX enerty threshold
- Proc Temp Threshold
- Proc Utilization threshold
- GFx Util thres

### Algorithm
Interface between CPU and Graphics is PCIe
1. Get CPU Energy Consupmtion. 
2. Get CPU Utilization. 
3. Get Alto Energy Consupmtion. 
4. Get Alto Utilization. 
5. Set CPU Power 
6. Set Alto Power. 

- get Utilization of CPU and Grpahics Die (Residency utilization primitives)
- Calculate total MCP Power
  - get time delta of callback
  - get energy unit
  - get energy counter (rapl energy counter cpu=64bit graphics=32bit)
  - cpu power = (energy counter * unit)/time  * 1000
  - total mcp power = cpu+graphics 
- Calculate PID Budget and Available TDP Headroom
  -PID_budget[t] = PID_budget[t-1] * alpha + (1-alpha) * (PID_Target – total_mcp_power),
- Calculate CPU and Graphics Effective BIAS 