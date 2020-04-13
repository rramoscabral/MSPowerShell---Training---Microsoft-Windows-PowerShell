#HSLIDE
# PowerShell Scripting and Toolmaking

#HSLIDE
# Introductions & HouseKeeping

#VSLIDE
## Class Hours
## Breaks & Lunch
## Lab Computers
## Facility Information

#VSLIDE
## Meet Your Instructor

#VSLIDE
## Introduce Yourselves







#HSLIDE
## CHAPTER 1:
## TOOL DESIGN
Tool design is an important step, and should focus on conforming to PowerShell's existing patterns.

#VSLIDE
### Tools Do One Thing

#VSLIDE
### Tools are Testable

#VSLIDE
### Tools are Flexible
```PowerShell
Get-Content names.txt | Set-MachineStatus
Get-ADComputer -filter * | Select -Expand Name | Set-MachineStatus
Get-ADComputer -filter * | Set-MachineStatus
Set-MachineStatus -ComputerName (Get-Content names.txt)
```

#VSLIDE
### Tools Look Native

#VSLIDE
### For Example
Let's run through a problem statement that will lead to a tool design.

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions









#HSLIDE
## CHAPTER 2:
## START WITH A COMMAND
Prototyping code/commands in the console saves time and helps prevent bugs.

#VSLIDE
Experiment with Get-CimInstance, Win32_OperatingSystem, Win32_ComputerSystem, and Win32_LogicalDisk.

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## CHAPTER 3:
## BUILD A BASIC FUNCTION AND MODULE
Turn your console commands into a simple function. This creates the skeleton of the tool you're building.

#VSLIDE
### Start with a Basic Function

#VSLIDE
### Design the Input Parameters
```PowerShell
function Get-MachineInfo {
 Param(
  [string[]]$ComputerName,
  [string]$LogFailuresToPath,
  [string]$Protocol,
  [switch]$ProtocolFallback
 )}
```

#VSLIDE
### Pro Tip
Don't get lazy about code formatting - ever.

#VSLIDE
### Code the Function

#VSLIDE
### The If Construct: Making Decisions
```PowerShell
If (<expression>) {
	# code
} ElseIf (<expression>) {
	# coded
} ElseIf (<expression>) {
	# code
} Else {
	# code
}
```

#VSLIDE
### The ForEach Construct: Enumerating Things
```PowerShell
ForEach ($item in $collection) {
    # code
}
```
Remember: you make up the variable names, they don't have any intrinsic meaning to the shell.

#VSLIDE
### Design the Output
Always output objects - for now, we'll use Select-Object to create that.

#VSLIDE
### Create a Script Module
Save the file with the right name, in the right spot.

#VSLIDE
### Pre-Req Check

* Run as Administrator
* Check Execution Policy
* Verify CIM functionality

#VSLIDE
### Running the Command
If it's "not found," check the file naming and location!

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions




#HSLIDE
## CHAPTER 4:
## ADDING CMDLETBINDING AND PARAMETERIZING
Start adding complexity and sophistication to your tools.

#VSLIDE
### About CmdletBinding and Common Parameters

#VSLIDE
* -Verbose
* -Debug
* -ErrorAction
* -ErrorVariable
* -InformationAction
* -InformationVariable
* -OutVariable
* -PipelineVariable

#VSLIDE
### Accepting Pipeline Input
* ValueFromPipeline
* * ValueFromPipelineByPropertyName

#VSLIDE
### Running Commands in Non-Pipeline Mode
BEGIN/PROCESS/END labels are ignored, command runs top-to-bottom

#VSLIDE
### Running Commands in Pipeline Mode
BEGIN runs first, PROCESS runs (with one object placed into the pipeline-accepting variable) once for each input object, END runs last

#VSLIDE
### Mandatory-ness
Shell will prompt for missing value(s).

#VSLIDE
### Parameter Validation
Numerous Validation attributes available.

#VSLIDE
### Parameter Aliases
Provide alternate names for parameters.

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions




#HSLIDE
## CHAPTER 5:
## EMITTING OBJECTS AS OUTPUT
Object-based output is the key to how PowerShell works. We've used Select-Object up until now, but we'll switch to a custom output object.

#VSLIDE
### Assembling the Information
Creating what will become the output object's properties.

#VSLIDE
### Constructing and Emitting Output
Creating and outputting the object.

#VSLIDE
### A Quick Test
Let's see how it works.

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## CHAPTER 6:
## INTERLUDE... CHANGING YOUR APPROACH
Let's look at one way in which PowerShell sometimes requires a re-thinking of how you approach scripting.

#VSLIDE
### The Example

#VSLIDE
### The Critique

#VSLIDE
### The Revision

#VSLIDE
### Let's Discuss





#HSLIDE
## CHAPTER 7:
## USING VERBOSE, WARNING, AND INFORMATIONAL OUTPUT
Using the proper output channels helps your tools better confirm to native shell practices.

#VSLIDE
### The Channels
1. Success (object output)
2. Errors
3. Warnings
4. Verbose
5. Debug
6. Informational

#VSLIDE
### Understanding Channel Preference Variables

#VSLIDE
### Adding Verbose and Warning Output

#VSLIDE
### Doing More with Verbose

#VSLIDE
### Informational Output

#VSLIDE
### A Detailed Informational Example

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions




#HSLIDE
## CHAPTER 8:
## COMMENT-BASED HELP
An easy way to provide native-looking help for your tools.

#VSLIDE
### Where to Put Your Help

#VSLIDE
### Getting Started

#VSLIDE
### Common Keywords
* .SYNOPSIS
* .DESCRIPTION
* .PARAMETER (parametername)
* .EXAMPLE

#VSLIDE
### Less-Common Keywords
* .INPUTS
* .NOTES
* .LINK

#VSLIDE
### Broken Help?

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## CHAPTER 9:
## HANDLING ERRORS
Dealing with errors adds sophistication and functionality to your tools.

#VSLIDE
### Understanding Errors and Exceptions

#VSLIDE
### -ErrorAction is the Key
```PowerShell
Get-Service -Name BITS,Nobody,WinRM -EA Continue
Get-Service -Name BITS,Nobody,WinRM -EA SilentlyContinue
Get-Service -Name BITS,Nobody,WinRM -EA Inquire
Get-Service -Name BITS,Nobody,WinRM -EA Stop
```

#VSLIDE
### Bad Handling

#VSLIDE
### Two Reasons for Exception Handling

#VSLIDE
### Handling Exceptions in Our Tool

#VSLIDE
### Capturing the Actual Exception

#VSLIDE
### Handling Errors for Non-Commands

#VSLIDE
### Going Further with Exception Handling

#VSLIDE
### Deprecated Exception Handling
Avoid using the old v1 `Trap` construct.

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## CHAPTER 10:
## BASIC DEBUGGING
Debugging can be less painful once you understand the technique, the goal, and the tools available.

#VSLIDE
### Two Kinds of Bugs

#VSLIDE
### The Ultimate Goal of Debugging

#VSLIDE
### Developing Assumptions
Let's walk through this example and write down our assumptions about what it's doing.

#VSLIDE
### Debugging Tool 1: Write-Debug

#VSLIDE
### Debugging Tool 2: Set-PSBreakpoint

#VSLIDE
### Debugging Tool 3: The PowerShell ISE

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## GOING DEEPER WITH PARAMETERS
Your parameter blocks can do a lot more than you may realize.

#VSLIDE
### Parameter Position

#VSLIDE
### Validation

#VSLIDE
### Multiple Parameter Sets

#VSLIDE
### ValueFromRemainingArguments

#VSLIDE
### Help Message

#VSLIDE
### Aliases (Again)

#VSLIDE
### More CmdletBinding

#VSLIDE
### Demo

#VSLIDE
### Review Questions





#HSLIDE
## WRITING FULL HELP
Update-able, localizable, native-style help for your tools.

#VSLIDE
### Downsides of Comment-Based Help
* Can't localize
* "Attached" to code
* Can't update (without updating code)
* Picky comment syntax

#VSLIDE
### External Help
Made from Microsoft Assistance Markup Language (MAML) XML

#VSLIDE
### Using Platyps
Turns Markdown into MAML and assists in creating initial Markdown

#VSLIDE
### Generate Markdown

#VSLIDE
### The Module Page

#VSLIDE
### Create External Help from Markdown

#VSLIDE 
### Supporting Online Help

#VSLIDE
### "About" Topics

#VSLIDE
### Making Your Help Update-able

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions



#HSLIDE
## UNIT TESTING YOUR CODE
Automated unit testing is one sign of a polished, professional toolmaker.

#VSLIDE
### Starting Point

#VSLIDE
### Sketching Out the Test

#VSLIDE
### Making Something to Test

#VSLIDE
### Expanding the Test

#VSLIDE 
### But Wait... There's More
Recommended: "The Pester Book" (http://LeanPub.com/the-pester-book)

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## EXTENDING OUTPUT TYPES
PowerShell's Extensible Type System offers useful "hidden" functionality for your tools.

#VSLIDE
### Understanding Types

#VSLIDE
### The Extensible Type System

#VSLIDE
### Type Extensions
* ScriptMethod
* ScriptProperty
* AliasProperty
* PropertySet
* NoteProperty

#VSLIDE
### Extending an Object

#VSLIDE
### Using Update-TypeData





#HSLIDE
## ANALYZING YOUR SCRIPT
Script Analyzer can help you develop and maintain best practices in your code.

#VSLIDE
### Performing a Basic Analysis

#VSLIDE
### Analyzing the Analysis

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## PUBLISHING YOUR TOOLS
Ready to share your masterpiece with your colleagues - or the world?

#VSLIDE
### Begin with a Manifest

#VSLIDE
### Publishing to PowerShell Gallery

#VSLIDE
### Publishing to Private Repositories or Galleries

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## BASIC CONTROLLERS: SCRIPTS AND MENUS

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## PROXY FUNCTIONS
A cool way to customize the functionality of PowerShell commands.

#VSLIDE
### What are Proxy Functions?

#VSLIDE
### Creating the Proxy Base

#VSLIDE
### Modifying the Proxy

#VSLIDE
### Adding Parameters

#VSLIDE
### Removing Parameters

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## WORKING WITH XML
A useful and flexible way to store data.

#VSLIDE
### Simple: CliXMI

#VSLIDE
### Importing Native XML

#VSLIDE
### Modify XML Data

#VSLIDE
### Add XML Data

#VSLIDE
### Saving XML

#VSLIDE
### ConvertTo-XML

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## WORKING WITH JSON
A web-centric way of persisting objects as text.

#VSLIDE
### What is JSON?

#VSLIDE
### Converting to JSON

#VSLIDE
### Converting from JSON

#VSLIDE
### Your Turn

#VSLIDE
### Reviewing a Solution

#VSLIDE
### Review Questions





#HSLIDE
## WORKING WITH SQL SERVER

#VSLIDE
### TERMINOLOGY

* SQL Server: The software
* Instance: A copy of the software
* Database: Like an Excel workbook
* Table: Like an Excel sheet
* Rows & Columns: As in Excel
* Data type: What a column can hold

#VSLIDE
### CONNECTING
```PowerShell
$conn = New-Object -Type System.Data.SqlClient.SqlConnection
$conn.ConnectionString = 'Server=SQL1;Database=MyDB;Trusted_Connection=True;'
$conn.Open()
```

Use ConnectionStrings.com for connection strings.

#VSLIDE
### QUERIES

* INSERT
* DELETE
* UPDATE
* SELECT

#VSLIDE
### INSERT
```SQL
INSERT INTO <tablename>
			(Column1, Column2, Column3)
	   		VALUES (Value1, Value2, Value3)
```

#VSLIDE
### DELETE
```SQL
DELETE FROM <tablename>
			WHERE <criteria>
```

#VSLIDE
### UPDATE
```SQL
UPDATE <tablename>
	   SET <column> = <value>, <column> = <value>
	   WHERE <criteria>
```

#VSLIDE
### SELECT
```SQL
SELECT <column>,<column>
	   FROM <tablename>
	   WHERE <criteria>
	   ORDER BY <column>
```

#VSLIDE
### CREATE TABLE
```SQL
CREATE TABLE <tablename> (
	<column> <type>,
	<column> <type>
)
```

#VSLIDE
### RUNNING QUERIES
```PowerShell
$command = New-Object -Type System.Data.SqlClient.SqlCommand
$command.Connection = $conn
$command.CommandText = $query
```

#VSLIDE
### UPDATE/INSERT/DELETE/CREATE TABLE
```PowerShell
$command.ExecuteNonQuery()
```

#VSLIDE
### SELECT
```PowerShell
$reader = $command.ExecuteReader()
```

#VSLIDE
```PowerShell
$conn = New-Object -Type System.Data.SqlClient.SqlConnection
$conn.ConnectionString = 'Server=SQL1;Database=MyDB;Trusted_Connection=True;'
$conn.Open()

$query = "SELECT ComputerName,DiskSpace,DateTaken FROM DiskTracking"

$command = New-Object -Type System.Data.SqlClient.SqlCommand
$command.Connection = $conn
$command.CommandText = $query
$reader = $command.ExecuteReader()

while ($reader.read()) {
	[psobject]$props = @{'ComputerName' = $reader.GetData(0)
	                     'DiskSpace' = $reader.GetData(1)
	                     'DateTaken' = $reader.GetData(2)}
}

$conn.Close()
```

#VSLIDE
### DON'T FORGET ABOUT TOOL DESIGN PATTERNS






#HSLIDE
## FINAL EXAM

#VSLIDE
This multi-hour lab experience will walk you through the major steps in creating a new tool. You'll be practicing all of the key elements that you've learned previously in this course.
