

# Acceptance criteria  

1) Power sharing loop starts when two or more participants with activity status capability in PSH2 table and the MCP participant **have been bound** . The loop time comes from **min_default_sample_period** primitive, which can be overridden in the data vault. The default should be 100ms. The sample period is only read **once** by the policy at **start up**. 
IETM participatnt and premitive 426/427. 




2) ~~If there is only one activity status participant bound and MCP participant is present, set 100% share of power to the bound participant. The control loop shall not be active.~~  
- not applicable. 

3) No action should be taken when MCP participant is not present. 
Policy is not enabled if the MCP is not present. 


4) Utilization of the CPU participant calculated and written as a debug message to the log every time through the loop. Value also appears in the policy monitor page. Message is tagged with "PSP_UTILIZATION". 
no print in log 


5) Utilization of the IDG1 participant calculated and written as a debug message to the log every time through the loop. Value also appears in the policy monitor page. Message is tagged with "PSP_UTILIZATION". We will need to use simulated (through automation) or manually faked values for utilization (through data vault override) at this time. 

6) IA energy calculated and written as a debug message to the log every time through the loop. Value also appears in the policy monitor page. Log message is tagged with "PSP_ENERGY". 

7) Energy calculated for IDG1 participant and written as a debug message to the log every time through the loop. Message is tagged with "PSP_ENERGY". Value also appears in the policy monitor page. We will need to use simulated (through automation) or manually faked values for energy (through data vault override) at this time. 

8) Add SET_RAPL_ENERGY, SET_RAPL_ENERGY_UNIT, SET_RAPL_ENERGY_COUNTER_WIDTH to IDG1 participant to override values in override.dv 
set_rapl_energy_unit missing. 
SET_RAPL_ENERGY_COUNTER_WIDTH missing


9) If IDG1 exists in PSHA and primitive fails, want to set MCP power from just CPU participant 
Q? PSHA or PSH2


10) Total power consumed by MCP participant written as a debug message to the log every time through the loop. Message is tagged with "PSP_ENERGY" and includes participant scope. Value also appears in the policy monitor page. 

11) Time delta written as a debug message to the log every time through the loop. Message is tagged with "PSP_ENERGY". Value also appears in the policy monitor page. 


12) PID Budget calculated and written as a debug message to the log every time through the loop. Message is tagged with "PSP_TDP_HR". Value also appears in the policy monitor page. 

13) Available TDP headroom calculated and written as a debug message to the log every time through the loop. Value also appears in the policy monitor page. 

14) BIAS calculated for both CPU and IDG1 and written as a debug message to the log every time through the loop. Message is tagged with "PSP_BIAS" and includes participant scope. Values also appear in the policy monitor page. 

15) CPU and IDG1 TDP budgets calculated and written as a debug message to the log every time through the loop. Message is tagged with "PSP_BIAS". Value also appears in the policy monitor page. 

16) Budgets that were calculated for CPU and IDG1 are written to the participant power controls 

17) Control loop slows down when the EWMA power is below the threshold, utilization is below the threshold, and the policy is not limiting (see calculations in the description) 

18) Slow polling values shown in UI as well as the current control loop rate (notLimiting, ewmaPowerBelowThreshold, utilBelowThreshold, current control loop polling rate) 

19) When slow polling is enabled, temperature thresholds are set for the CPU participant and energy thresholds are set for the DGFX participant. If either of these thresholds gets crossed, the policy shall consider taking action 

20) Update the wiki page with information for this story




## QA  

1) how the pid budget calculated? what is the negetive number means.  
2) Is available TDP Headroom constant? observed 30000  
	- no its not constant. 
3) what is EWMA?  
	- Exponential Weighted Moving Average  
3) what is the difference between pid-target and pid budget.  
4) what is iterm?  
	- ki related parameter.
5) alpha / tau based on the sampling what will change? 
6) why callback time delta in low graphics mode is always around 3 sec. ???
7) PSP_utilization is missing in log with debug level. 65397 /2266
8) 100% to cpu and 100% to graphics.  65383 / 2267
9) setp 476 D0 255 for SET_RAPL_ENERGY to zero - 65401 / 2269
	- i can set once. 

10) change the TC as per new UI. 65388 / 2278
	check with spencer 
11) update the export description for 65373 / 2243
	- update test desc  
12) Temp Control and Threshold knobs appear on DGFC 65402 / 2328 
13) rewrite the test case 65375 / 2364
14) How frequently ewma calculations are done. 

## note:
- restart required after resetting the pid target value
- RAPL is pid target. 
- ESIF shell command is on MCPP
- available TDP headroom is fixed when pid target is less than
- utilization of CPU and graphics from the primitives. 
- 𝑡𝑎𝑢 (1𝑠 𝑑𝑒𝑓𝑎𝑢𝑙𝑡)  :𝑡𝑖𝑚𝑒 𝑐𝑜𝑛𝑠𝑡𝑎𝑛𝑡 𝑓𝑜𝑟 𝑡ℎ𝑒 𝑃𝐼𝐷 𝑎𝑙𝑔𝑜𝑟𝑖𝑡ℎ𝑚
- 𝑠𝑎𝑚𝑝𝑙𝑖𝑛𝑔_𝑖𝑛𝑡𝑒𝑟𝑣𝑎𝑙:100 𝑚𝑠 𝑑𝑒𝑓𝑎𝑢𝑙𝑡
- 𝛼=(1−𝑠𝑎𝑚𝑝𝑙𝑖𝑛𝑔_𝑖𝑛𝑡𝑒𝑟𝑣𝑎𝑙/𝑡𝑎𝑢)
- 𝑝𝑖𝑑𝐵𝑢𝑑𝑔𝑒𝑡_𝑡  :𝐴𝑐𝑐𝑢𝑚𝑢𝑙𝑎𝑡𝑒𝑑 𝑏𝑢𝑑𝑔𝑒𝑡 𝑎𝑡 𝑡𝑖𝑚𝑒 𝑡  
- 𝑝𝑖𝑑𝐵𝑢𝑑𝑔𝑒𝑡_(𝑡−1)=0 𝑓𝑜𝑟 𝑖𝑛𝑖𝑡𝑖𝑎𝑙 𝑒𝑣𝑎𝑙𝑢𝑎𝑙𝑡𝑖𝑜𝑛 𝑖𝑛𝑡𝑒𝑟𝑣𝑎𝑙  
- 𝑜𝑣𝑒𝑟𝑎𝑙𝑙𝐶𝑢𝑟𝑟𝑒𝑛𝑡𝑇𝐷𝑃 :𝑁𝑒𝑤 𝑀𝐶𝑃 𝑃𝐿1 𝑡𝑜 𝑏𝑒 𝑝𝑟𝑜𝑔𝑟𝑎𝑚𝑚𝑒𝑑 𝑖𝑛 𝑡ℎ𝑖𝑠 𝑖𝑛𝑡𝑒𝑟𝑣𝑎𝑙
- 𝑝𝑖𝑑𝐵𝑢𝑑𝑔𝑒𝑡_𝑡=𝛼∗〖𝑝𝑖𝑑𝐵𝑢𝑑𝑔𝑒𝑡〗_(𝑡−1)+(1−𝛼)(𝑝𝑖𝑑𝑇𝑎𝑟𝑔𝑒𝑡−𝑡𝑜𝑡𝑎𝑙𝑀𝑐𝑝𝑃𝑜𝑤𝑒𝑟)
- 𝑝𝑇𝑒𝑟𝑚_𝑡=𝐾𝑝∗〖𝑝𝑖𝑑𝐵𝑢𝑑𝑔𝑒𝑡〗_𝑡
- 𝑖𝑇𝑒𝑟𝑚_𝑡=〖𝑖𝑇𝑒𝑟𝑚〗_(𝑡−1)+𝐾𝑖∗〖𝑝𝑖𝑑𝐵𝑢𝑑𝑔𝑒𝑡〗_𝑡∗𝑠𝑎𝑚𝑝𝑙𝑒𝑃𝑒𝑟𝑖𝑜𝑑𝐼𝑛𝑆𝑒𝑐𝑠
- 𝑜𝑣𝑒𝑟𝑎𝑙𝑙𝐶𝑢𝑟𝑟𝑒𝑛𝑡𝑇𝐷𝑃=𝑝𝑖𝑑𝑇𝑎𝑟𝑔𝑒𝑡+〖𝑝𝑇𝑒𝑟𝑚〗_𝑡+〖𝑖𝑇𝑒𝑟𝑚〗_𝑡  
- If〖 𝑝𝑖𝑑𝐵𝑢𝑑𝑔𝑒𝑡〗_𝑡 is negative then we are in a limiting state. Will need to save this state (limiting/un-limiting) and use it in the decision to go into slow polling.  
- 𝒍𝒊𝒎𝒊𝒕𝒊𝒏𝒈=(〖𝒑𝒊𝒅𝑩𝒖𝒅𝒈𝒆𝒕〗_𝒕<𝟎)  
- Tau for GPU available for PS2  
- PL2 knob available for graphics.  
- kpe - kernel participants extension for talking to other driver. 
- PID budget is error equivalent of PID
- TDP headroom is total power that will be split. 


# algorithm Power share 
## Algorithm_without_slow_poll_optimization_v7.txt

DPTF implements a PID controller to track overall power head room available to the entire MCP.  

### Components of the PID 
1. PID_Budget[t] – This is a unitless quantity that tracks available power headroom.  This is the EWMA accumulator  
2. PID coefficients  
	o Kp – This is the proportional gain of the PID controller
3. PID Target – This is the target in Watts that the PID controller is expected to maintain the MCP to.  
4. Tau 
	– This is the time constant of the PID algorithm  
	– it defines the averaging interval for the PID controller.  
	- This is typically matched to the thermal capacitance of the form factor.  
	- Customers may request configurability of this parameter.  
	- If we are targeting the control loop to run every 100ms, Tau should be no smaller than 5x this number.  I would say we should target 1s Tau at the minimum.  
	- Alpha – is a derived factor that defines how much history we carry forward from one evaluation interval to another.  
	- Alpha = 1 – (sample_interval_period)/Tau.  
	- So for Tau = 1 Second, and a sample interval of 100ms,  
	- Alpha = 1 – (0.1/1) = 0.9  

### Loop   
Every 100ms (or every periodic interval)  
· Calculate utilization of the CPU die  
	- Option 1  
		1.  Read current value of PCU_CR_PKG_IA_C0_ANY_0_0_0_MCHBAR_PCU_ADDRESS  
		2. Calculate delta from previous sampled value   
		3. This register counts the number of clocks any IA core is active at a 100MHz heart beat.  
		4. Calculate time elapsed since last interval   
			• Delta_Time = current_time – prev_time  
		5. Delta_IA_C0_residency_pct = (current_IA_C0_ANY – last_IA_C0_ANY)*10ns / delta_time  
		6. Store the current C0 residency counter away for future computation. Last_IA_C0_ANY = current_IA_C0_Any  
	- Option 2  
		1. Use existing residency counter primitives that was used for HDC ('GPCU') or create a new one similar to that but which gets just the PKG utilization counters  
· Calculate utilization of the DGFX die  
	7. Plan is to use  (action: DGFX, method: 'GGAC')  
	8. The goal is to come up with effective C0 residency (or utilization of the GPU die) over the last evaluation interval  
· Calculate KBL H energy consumed over the last evaluation interval  
	9. Read PKG_ENERGY_STATUS MSR (MSR 0x611)  
	10. Calculate energy consumed over the evaluation interval  
	11. delta_energy_IA = (current_PKG_ENERGY_STATUS – las_PKG_ENERGY_STATUS)  
	12. This is a 64 bit counter that tracks energy consumed in fractions of Joules.  The fraction (or unit of measurement) is enumerated in PKG_POWER_SKU_UNIT.ENERGY_UNIT field. (MSR 0x606, bits[12:8])  
	13. A value of 3 for eg => unit is in 2(-3) joules = 1/8th of a joule.  
· Calculate energy consumed  by DGFX die over the evaluation interval  
	14. Plan is to use  (action: DGFX, method: 'GGAC' and 'GEU0' if needed)  
	15. Result is getting a delta_GPU_nergy  
· Calculate total power consumed by the MCP  
	16. Total_mcp_energy = delta_IA_energy + delta_GPU_energy  
	17. Delta_Time = current_time – prev_time  
	18. Total_mcp_power = total_mcp_energy/(delta_Time)  
· Calculate the available headroom  
	19. PID_budget[t] = PID_budget[t-1]*alpha + (1-alpha)*(PID_Target – total_mcp_power)  
	20. Where t-1 stands for the accumulated budget at the previous evaluation interval.  
· Translate accumulated budget to available TDP head room  
	21.  
		a.  
		iTerm[t] = iTerm[t-1] + PID_Budget[t] * timeinSecs * Ki  
		m_availableHeadroom = PID_Target + PID_budget[t] * Kp + iTerm[t]  
			• Where PID_Target is the power limit DPTF is configured to control the MCP to.  
			• Kp is the gain of the PID controller.  
			• Ki is the integral const.  
			• If PID_budget[t] starts becoming negative, current_TDP will be lower than PID_Target and we’ll start throttling both the dies.  
		b.  
		//We need to keep the iTerm windup separate from the Max_PL1_MCP check.  this allows the proper sharing of power and allow the package power  
		//to "Turbo" and exceed the PL1 limit for short duration.  
		if (m_availableHeadroom > (Max_PL1_CPU + Max_PL1_GPU)) {  
			iTerm[t] -= m_availableHeadroom - (Max_PL1_CPU + max_PL1_GPU)  
		}    
		else if (m_availableHeadroom < PL1Min for MCP) {    
		iTerm[t] += PL1Min - m_availableHeadroom    
		}    
		//Below we add a a separate check to limt the overall_current_TDP to keep at or below the Max and Min budget allowed.  This must  
		//be kept separate from the iterm windup check since.  This value is visible to UI and we should not show allowance of a total  
		//package power higher than the programmed Max_PL1_MCP  
		if (Overall_Current_TDP > PL1Max for MCP) {		  
			Overall_Current_TDP = MCP PL1Max  
		   }  
  		   else if (Overall_Current_TDP < PL1Min for MCP) {  
			Overall_Current_TDP = PL1Min   
		   }  
· Calculate BIAS for each of the dies and calculate effective budgets based on the BIAS  
	22. This step is needed to figure out how to split the overall TDP between the two MCP components (DGFX , and KBL H die)  
		 Implementation #1 – assuming run time tracking of utilization to infer BIAS works  
			i. Instantaneous_IA_BIAS = Default_Palo_BIAS * Delta_IA_C0_residency_pct  
			ii. Instantaneous_GPU_BIAS = Default_GPU_BIAS * Delta_GPU_C0_residency_pct  
			iii. Effective_IA_BIAS = 0.5 + (Instantaneous_IA_BIAS – Instantaneous_GPU_BIAS)/2  
			iv. Effective_GPU_BIAS = 0.5 + (Instantaneous_GPU_BIAS – Instantaneous_IA_BIAS)/2  
			v. if (graphicsUtil <= 5%)	{  
				Effective_IA_BIAS = 0.95;  
				Effective_GPU_BIAS = 0.05;  
		           }  
	23. effectiveProcessorTdpBudget = Overall_Current_TDP * m_effectiveProcessorBias;  
	    effectiveGraphicsTdpBudget = Overall_Current_TDP * m_effectiveGraphicsBias;  
· Rebalance unused budget  
	24.  
	if (rebalance_unused_budget) {  
	 	if (effectiveProcessorTdpBudget > processorPl1Max) {  
			remainingProcessorTdpBudget = effectiveProcessorTdpBudget - processorPl1Max;  
			effectiveGraphicsTdpBudget = effectiveGraphicsTdpBudget + remainingProcessorTdpBudget;  
		 }  
		 else if (effectiveGraphicsTdpBudget > graphicsPl1Max) {  
			remainingGraphicsTdpBudget = effectiveGraphicsTdpBudget - graphicsPl1Max;  
			effectiveProcessorTdpBudget = effectiveProcessorTdpBudget + remainingGraphicsTdpBudget;  
		}  
	}  
· Split the available TDP budget between the two dies  
	25. Palo_TDP_Budget = min(max(effectiveProcessorTdpBudget, Min_palo_power), Max_palo_power)  
	26. Alto_TDP_Budget = min(max(effectiveGraphicsTdpBudget, Min_alto_power), Max_alto_power)  
· Program the individual power budgets as the control points for each of the dies   
	27. For CPU – program this in PACKGAGE_RAPL_LIMIT MSR 0x610  
	28. For DGFX – action: DGFX, method: 'SPL0'.  





config set @dptf /features/DG1 1
restart needed. can try esif reload

## mail from Enriquez Montanez, Daniel
http://ubit-gfx.intel.com/build/7045258


HKLM\SYSTEM\CurrentControlSet\Control\Video\<GUID>\0000\

The GUID will vary, however, only our driver will have a lot of reg keys starting with “@” in that path, so that way you know is the good one. The regkey should be a DWORD called:

DptfForceEnable
DptfUseSpoofValues

In the same path. This what it does is, to return hardcoded values for registers not yet ready, like setting PL4, Energy Threshold and some more. However for PL1 and PL2 and I think even for Tau should work. The names are case sensitive.

After setting the reg keys, please restart and it should be connecting via Kpe as usual.



testcase related to the PS2 story: 
AC 1,3 - 2266 - for activity status.  DPTF-PSPVTC-3357
AC 4-7 - 2313 utilization and energy. DPTF-PSPVTC-3360
AC 9 - 2269  - DPTF-PSPVTC-3361


no spoofing until we get new hardware. 


Raedon vega M GL graphics - PCI slot1 - bus1 - device 0 
Intel - PCI bus 0 - device 2



creating participant MCPP shows PL234567 if you click next and prev repeatedly. 
MCPP dynamically created but require restart appstop/start doesnt work. 
MCPP added but still not showing in the table PSH2. 
Processor PL1 tau = 32 s
Graphics = 5.0S
appstop / start needed for any change on MCPP to be impacted like PL1 . 
tried two edp and one HDMI and only one works. 
graphics PL1 tau shows X after connecting display and reboot. 


graphics repo
https://gfx-assets.fm.intel.com/artifactory/webapp/#/artifacts/browse/tree/General/gfx-core-assets/Production/KMDR/CI/TOP_Test_Suite/DPTF/DPTF-core-val-ci-master-1794 
Alvarado Legaria, Selene 1:46 PM: 
https://gfx-assets.fm.intel.com/artifactory/webapp/#/artifacts/browse/tree/General/gfx-core-assets/Production/CrossComponent/DIVA/CI/DIVA/DIVA-core-val-ci-master-1794 



ET:
delete IDG1 and check the policy status. 
PID target is always negative. 
CPU utilization is higher than expected. 



Slow poll.

1) Pid Budget -ve OR ewma pid budget slope -ve
2) ewma utlization <CPU util threshold   AND   emw DGXutil < GFX util threshold. 
3) ema power< slow poll power theshold. 

1 AND 2 AND 3 will put the system into slow poll. 





logman create trace dptfonly -p EsifLfEtwProvider 0x00000102 5 -o c:\dptf25.etl
logman start dptfonly
set /p DUMMY=Hit ENTER to continue...
logman stop dptfonly
tracerpt **.etl -o energythresholdcount.csv -of CSV