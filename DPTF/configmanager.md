## config command

enable feature config set @dptf /features/configuration_manager 1


|action|command|
|---|---|
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

DPTFDPTF-3482	[Part 1] Add ESIF Shell Support for Configuration Manager UI commands

DPTF-PSPVTC-3097
DPTF-PSPVTC-3098
DPTF-PSPVTC-3099
DPTF-PSPVTC-3100
DPTF-PSPVTC-3101
DPTF-PSPVTC-3102
DPTF-PSPVTC-3103
DPTF-PSPVTC-3104

DPTF-3482	[Part 2] Show list of configuration files 
DPTF-PSPVTC-3229 
DPTF-PSPVTC-3231 
DPTF-PSPVTC-3234 
DPTF-PSPVTC-3235
DPTF-PSPVTC-3239

DPTF-3483	[Part 3] Activate a configuration
DPTF-PSPVTC-3233
DPTF-PSPVTC-3236
DPTF-PSPVTC-3237
DPTF-PSPVTC-3238

DPTF-3485	[Part 4] Delete a configuration
DPTF-3555	[Part 5] Edit a configuration
DPTF-3484	[Part 6] Factory reset
DPTF-3556	[Part 7] Import a configuration
DPTF-3557	[Part 8] Export a configuration
DPTF-3559	[Part 9] Import a configuration with .asl extension
DPTF-3606	[Part 10] Download configuration file
