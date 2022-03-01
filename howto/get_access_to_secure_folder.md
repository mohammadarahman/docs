# Get Access to Secure Folder

	○ Right-click on the file/folder and select “Properties” from the drop-down menu.  
	○ Navigate to the “Security” tab and click on “Advanced” present at the near bottom of the screen. As you can see there are no proper permissions for your account in this case.  
	○ Click on the “Change” button present on the preceding screen. It will be right in front of the owner value. Here we will change the owner of this folder from TrustedInstaller to your computer account. Make sure that you are logged in as administrator.  
	○ Now enter your user account name in the empty space present and click on “Check Names”. Windows will automatically list all the accounts which are a hit with this name.  
	○ Now check the line “Replace owner on sub containers and objects”. This will ensure that all the folders/files within the folder also change their ownership. This way you won’t have to proceed with all the process again and again for any sub-directories present. You should also check “Replace all child object permission entries with inheritable permission entries from this object”.  
	○ Now close the Properties window after clicking “Apply” and open it again afterward. Navigate to the security tab and click “Advanced”.  
	○ On the permissions window, click on “Add” present at the near bottom of the screen  
	○ Click on “Select principle”. A similar window will pop up like it did in step 4. Repeat step 4 again when it does. Now check all the permission (giving full control) and press “OK”.  

	
From <https://appuals.com/fix-failed-enumerate-objects-container/> 