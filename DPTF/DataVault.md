# DV?

- Data Vaults are a service provided by the Upper Framework
- Collection of persisted K/V pair. 
- Filename is namespace. foo.dv -> foo namespace.  
- datavault maximum size is 2GB. 
- version1 header: 1) Signature 2) header size) Version 4) flags. 
- version2 Header:  5) segment ID 6) comment 7) payload hash 8) Payload Size 9) Payload Class
- 


# Data Model

|object|description|
|---|---|
|Repository|It only includes global databank|
|DataBank|It partitions data into Namespace. Each namespace stores data in DataCache|
|DataCache|K V pair in Memroy. Some or all may be persisted in DataVault|
|DataVault|It contains all the K/V pair persisted to disk|

# Example DV
- dsp.dv
- override.dv
- dptf.dv
- startup.dv
- platform.dv


# config command



|Function|Description |
|---|---|
|EsifConfigExit|Close a DataVault (Namespace) |
|EsifConfigFindFirst|Iterate First Key/Value pair in a DataVault (Namespace), sorted alphabetically. |
|EsifConfigFindNext|Iterate Next Key/Value pair in a DataVault (Namespace), sorted alphabetically. |
|EsifConfigGet|Get a Value from a DataVault (Namespace) for a given Key. |
|EsifConfigInit|Open or Create a DataVault (Namespace) [Do not specify ".dv" extension] |
|EsifConfigSet|Set a Value in a DataVault (Namespace) for a given Key/Value pair and options |


|example|Description |
|---|---|
|config / config list|display all open dv, default with *|
|config get @override "/participants/DPTF.D0/idsp"|get the value from override|
|config get @dsp sb_wwan.edp|get key from dsp|
|config get version|get ver|
|config get @override *|get all from override|
|config set @override "/participants/TCPU.D0/trippoint_ac0" 42 temperature| set temp datatype|
|config open @override|open if it is not open already|
|config close @override|close|
|config drop @override |delete if not open|
|config save @override /participants/IETM.D0/idsp idsp.bin||
|config set debug "trace route all log && trace log open debug.log && trace level debug"| Set the "debug" Key to the specified commands (multiple commands separated by " && " and replaced with newlines).|