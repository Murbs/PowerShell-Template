# PowerShell-Template

Quick shell script to automate some directory templating.

```PowerShell
$Str1 = 'Placeholder text lol '
$Str2 = Read-Host -Prompt 'User Input Goes Here'

$TemplatePath = 'C:\Users\<User>\desktop\template\*' # Grab template files from here
$DestinationPath = 'C:\Users\<User>\desktop\destination' # Copy template to here

# Create a new directory named some placeholder text and user input, at the destination path
New-Item -Name ($Str1 + $Str2) -ItemType Directory -Path $DestinationPath

# Copy the contents of my template folder to the newly made directory
Copy-Item -Path $TemplatePath -Destination ($DestinationPath + ($Str1 + $Str2)) -Recurse

# Open the destination path
ii ($DestinationPath)
```
