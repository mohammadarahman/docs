# Basic Information

## info of files

- Solution name: DPTFLiveTest
- Folder - DptfTest
- Code - WebUiTest


## sample test

- DPTF-PSPVTC-2018 


## Code and explaination

- SpecflowHooks.cs
	- `[BeforeTestRun]`  
	- `[BeforeFeature]`  
	- `[BeforeScenario]`  
		- can have parameter.
	- `[AfterScenario]`  
	- `[AfterFeature]`  
	- `[AfterTestRun]`  



- `[When(@"I check the (System|Application) event log")]`


- `[Then(@"the (Application|System) event log contains no (.*) (critical|error|warning|information) entries")]`

- `[Given(@"I have Read the Participants and Policies parameters from file")]`

- EventLogsManager

- EsifCommandManager

- DWF

- DWFOptions

- FeatureContext 
	- Feature Title =>  FeatureContext.Current.FeatureInfo.Title  

- TestContext
	- testname => TestContext.CurrentContext.Test.Name

- `Echo.Info("")`  



## Code snippet
```c#

// This will check Fan participant
ParticipantInfoCollection.Instance.FindFirstMatchingParticipant("TFN");

// Ignore test
Assert.Ignore("Ignoring test. No fans detected.");


// check tab
bool SelectOpenTab() => DptfWrapper.WebModeless.SelectOpenTab(tabName);
bool SelectGroupTab() => DptfWrapper.WebModeless.SelectGroupTab(tabGroup);
bool SelectModuleTab() => DptfWrapper.WebModeless.SelectModuleTab(tabName);

// switch monitor and designer
DptfWrapper.WebModeless.SwitchModesFast(mode == "Monitor" ? WebPageInterface.UiMode.Monitor : WebPageInterface.UiMode.Designer);

DWF.WaitForResult(
				SelectModuleTab,
				isTabClosed,
				TimeSpan.FromSeconds(10),
				DWFOptions.Designer);


//LINQ Example
// Specify the data source.
        int[] scores = new int[] { 97, 92, 81, 60 };

        // Define the query expression.
        IEnumerable<int> scoreQuery =
            from score in scores
            where score > 80
            select score;

        // Execute the query.
        foreach (int i in scoreQuery)
        {
            Console.Write(i + " ");
        }            
// another LINQ
string[] words = { "bot", "apple", "apricot" };
int minimalLength = words
  .Where(w => w.StartsWith("a"))
  .Min(w => w.Length);
Console.WriteLine(minimalLength);   // output: 5



string op = EsifCommandManager.Instance.SendEsifCommand(cmd)
```





## lambda

The lambda operator => separates the input variables on the left side from the lambda body on the right side.

This example shows nameless lamda function which return a string "hello world"
``` c#
//no parameter
Func<string> greet = () => "Hello, World!";
//one parameter
Func<int, int> square = x => x * x;
Console.WriteLine(square(5)); //25
//two parameter
Func<int, int, int> square = (x,y) => x * y;
Console.WriteLine(square(5,6)); //30
// last one is return
Func<int, string, bool> isTooLong = (int x, string s) => s.Length > x;

```

[Reference about lamda delegate and events](https://docs.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10))  




# Muted test

## preparing sut
- Teams-> DPTF -> DPTF -> WindowsPipeline -> master  
- Full project name: dptf/WindowsPipeline/master
- [jenkin build location](https://owrpilot-cbjenkins.fm.corp.intel.com/teams-dptf/job/dptf/job/WindowsPipeline/job/master/)  
- From the artifact find file like DptfLiveTest-8.6.10499.10405.zip  
- need to get dptflivetest -> LiveTest-> scripts-> install64r.bat (ui) 
- livetest-> install -> dptf-installer-> setup.exe
- get latest working dptf version on SUT
- install dptf and UI
- need to clear cookies if old version not removed . 


## preparing for automated test. 
- Livetest-> scripts-> enable remotepowershell.ps1
- share c drive-> advance sharing-> permission -> allow full control (everyone)  
- datavault location -> C:\Windows\System32\drivers\DriverData\Intel\DPTF\dv  
- solution file -> yourWorkspace\dptf\Validation\Windows\Solution

## Testing
- Test explorer to run / find the test we want to run. 
- Utilities-> configurationManager.cs
	- developmentdefaultsettings line 170 
	- change ip address and change the pl
	- c:\validation\config\WebUiTestSetting.xml also keep ip address with high priority. 

## Muted Test
- These will be in backlog
- Muted Test category. 
- test number  and teamcity link should be in teh description. 
- assign to yourself. 
- change Sprint to Current / active sprint. and save. 
- 938 for story. 

### for triage debug

- windows builds
	- main  
		- automation runners (perbuild) (nightly) (weekly)  
			- automation integration runner  (validation development)  

- run the test on same target. 
- find the target under automation integration runner
- click run
- under dependencies select the version we want to test. 
- under parameters 
	- nunit categories include by config -> test number
	- clear nunit categoriesExclude
	- clear nunit categoriesExcludebyconfig 
- runBuild


# Story to verify

Defect = bug but not HSD
Issue = Might be expected. 

Coverage created -> test case created. 
if 1 scenerio is blocked but if failed is failed then it can be pass if 75% is passed. 

Coverage updated is needed -> when any similar test case found and update anything. 

ET -Exploratory Test. 



### Template of story verification. 
Test Plan
Item (n): 
Setup:
[IN PROGRESS]Outcome:


# push



	Cloning a Automation Story
	- for clone -> more -> clone ++ (everything)

step 1 is create a story if it is not there. 


	Get Automation Code
	- pull master to get all the last change. 
	- pull will only get unconflictedchanges. 
	- create a branch and pull as needed 
	- rightclick -> tortoise git -> create branch. 
	- switch to new branch. 



	Gherkin update
	- update @tc number 
	- update description 
	- scenario: jama testcase id: DPTF-PSPVTC: description 
	- make sure the binding is happening properly. 
	- **Given** will assert data and skip if not met. 
	- **assert.ignore** will ignore the test. 
	- **assert.success** -> pass
	- **assert.fail** -> faile


	Build the package
	- push the code with same remote branch. 
	- goto jenkin automation pipeline. 
	- build with parameter
		- dptf version 
		- branch 
	- jenkin will build the artifacts with some install. 
	- artifacts will be available in windows pipeline. 
	- [teamcity will get those artifacts.](https://ubit-teamcity-hf.intel.com/project.html?projectId=DptfEsif_WindowsBuilds_Main_AutomationIntegrationRunners&tab=projectOverview)  
	- Nightly -> specflow. 
	- click next to run -> tooltip = run custom builds 
		- Dependencies -> select build
		- Parameter -> define test case 
			- nunitcategories exclude -> delete all
			- nunitcategoriesinclude by config -> 2343 (test number ) use comma for multi test. 


	tips
	- my settings and tools
		- General 
		- check the check box add builds triggered by me to favourites. 

### Issue about remote Powershell. 
  - check C: is shared fully.   
  - check winrm is running.  
  - run winrm quickconfig in the host.  
  - run enableremotepowershell.ps  

### Merge request
 - gitlab
 - 2nd from left top 
 - repository -> branches -> find branch and send a merge request. 
 - prepend [VAL] in the merge request. edit the manual. 
 - in merge request provide the passing teamcity link of test. 
 - assigne put yourself name. 
 - select approver
 - checkbox - delete source branch 
 - squash commits. -

 - rebase if the branch is outdate. 
 - pull from master to master. local branch should be switched to master. 
 - then switch to dev branch and merge locally before pushing dev branch to remote. 
 - this will not change the local change. 


 tag push / push_review


# team city configuration. 

Registered on server with id 1582 and authorization token '54093d6633e07822b56a8c5e1244b195'
created a virtual machine for running using teamcity. 
config file is in c:\buildagent\conf\buildAgent.properties

### bring up platform to teamcity. 
- add trusted host winrm . 
- winrm quickconfig


# adding VM as teamCity agent to run test. 
- need to start with a working VM and rename the Virtual box system and also Team City agent name. 
- Team City agent name should be matched with the SUT host name. Otherwise need to change in the Team City configuration. 
- there are several configuration to be done from SUT side to do so need to use automation imaging system .
- for that need to update xml files in the workspace and check in the code. 

- Change for reimaging. 
	1) Go to <workspace>\Validation\Windows\Solution\ReImage\BiosSettings
	2)Make a copy of the BIOS settings XML file for a platform that's similar to the new platform.
	3) Rename the copy so it includes the new platform's abbreviation ("BiosSettings-<New Abbreviation>.xml").
	4) Modify the BIOS settings to reflect the POR features for the platform as listed in the Dynamic Tuning Feature Roadmap.
	5) Go to <workspace>\Validation\Windows\Solution\ReImage
	6)Add/Modify an Agent Parameters element in ReimageInfo.xml so that it reflects the new system's configuration.
	7) Add a Platform SubPaths element in ReimageInfo.xml that points to the new platform's base directory in \\dptf-imager\imaging\Image

- https://sx-cyclr-rem-vm:8000/index.html 


# Add participant for automation. 

The process is something like this:
1. Create a valid dynamic participant using the appropriate manual process (which is usually the DPW).
2. Run "participant <part_id>" in ESIF. The output should contain the participant's description, hid and ptype.
3. If the participant you created only appears in "parts", then its enum is "CONJURE".
If the participant you created also appears in "partsk", then its enum is "ACPI".