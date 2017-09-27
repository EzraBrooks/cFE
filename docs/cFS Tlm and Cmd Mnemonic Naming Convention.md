# CFS Telemetry and Command Mnemonic Naming Convention

### Purpose
To specify telemetry and commands naming convention that is to be used when writing generic CFS test products.  These include test scenarios, test procedures, telemetry and command RDLs, and display pages.  The use of this naming convention will allow these products to be used across different missions.  By preceding certain mnemonic fields with a dollar sign, automated procedures can be used to substitute specific names when instantiating the test products for a specific mission.
 
Since, at this point, the requirement is for CFS missions to use either ASIST or ITOS, these conventions shall be able to accommodate both of those ground systems.

### Telemetry Mnemonics

`$SC_$CPU_APP_TelemDescription[i]`

Where

| Field | Description |
|-------|-------------|
|$SC_   |Always specify this field as “$SC_”.  This field will be substituted with an actual spacecraft designator, up to 4 characters long.  The designator can be null if there is only one spacecraft in the mission.  The underscore is optional, although its use is encouraged to make the mnemonic more readable.  If included, it counts as one of the 4 characters.  |
|$CPU_  |Always specify this field as “$CPU_”.  This field will be substituted with an actual **CPU** designator, up to 4 characters long.  The designator can be null if the spacecraft has only one CPU.  If there are multiple CSCIs on the same CPU, the mission may decide to use the CSCI designator in this field. The underscore is optional, although its use is encouraged to make the mnemonic more readable.  If included, it counts as one of the 4 characters.  |
|APP_   |This is a mission-specified **Application** designator, up to 5 characters long.  The choices are as follows: <ul><li>CF_ CCSDS File Delivery Protocol</li><li>CS_ Checksum</li><li>DS_ Data Storage</li><li>FM _ File Manager</li><li>HK_ Housekeeping</li><li>HS_ Health and Safety</li><li>LC_ Limit Checker</li><li>MD_ Memory Dwell</li><li>MM_ Memory Manager</li><li>SCH_ Scheduler</li><li>SC_ Stored Commands</li></ul>For cFE the choices are:  <ul><li>ES_	Executive Services</li><li>TIME_	Time Services</li><li>EVS_	Event Service</li><li>SB_	Software Bus</li><li>FS_	File Service</li><li>TBL_	Table Service</li><li>CI_	Command Ingest</li><li>TO_	Telemetry Output</li><li>OS_	Operating System</li></ul>The underscore is **not** optional and counts as a fifth character.
|TelemDescription |**Description** of the telemetry point.  It can be up to 18 characters long.   Mixed case is encouraged to improve readability.  Note, the description shall contain no underscores.|
|[i]|**Index** designator.

### Command Mnemonics

```
$SC_$CPU_APP_CmdDescription  
    Parameter1|Parameter1=value,  
    Parameter2|Parameter2=value,…
```

Where

|Field|Description|
|-----|-----------|
|$SC_ |Spacecraft designator.  Same as for telemetry mnemonics.|
|$CPU_|CPU designator.  Same as for telemetry mnemonics.|
|APP_ |Application designator.  Same as for telemetry mnemonics.|
|CmdDescription|Description of the command.  It can be up to 18 characters long.<sup>[1](#footnote1)</sup>  Mixed case is encouraged to improve readability.  Note, the description shall contain no underscores.|
|Parameter1\| Parameter1=value |The Parameter can be a constant or an expression.  E.g.:<ul><li>/$SC_$CPU_EVS_EvtPortEna  ENA</li><li>/$SC_$CPU_TBL_LoadTbl  TABLE=32, FILE=Table32.txt</li></ul>

<a name="footnote1"><sup>1</sup> Note: ITOS allows for 256 character mnemonics, whereas ASIST only allows for 31 character mnemonics.  Since this convention must work for both systems, we must use the smaller of the two.</a>

### Test Application Telemetry and Command Mnemonics

When specifying telemetry and command mnemonics associated with test applications, use the following convention:

`$SC_$CPU_TST_APP_TelemDescription[i]`

`$SC_$CPU_TST_APP_CmmdDescription`

Note that the “TST” designator must always be specified and must always come before the Application designator.  Because of the presence of the test application designator, the descriptors can only be 14 characters long.  
