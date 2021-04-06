# PowerShell-Template

This is probably super specific to my daily routine, but to summarize.. On any given day my team is sorting files from a client into different directories. My solution to this at first was to make a template for people to copy. A few headaches later, I find myself looking into scripting out the entire folder structure.

```PowerShell
$Str1 = 'Placeholder text lol '
$Str2 = Read-Host -Prompt 'User Input Goes Here'

$TemplatePath = 'C:\Users\<User>\desktop\template\*' # Grab template files from here
$DestinationPath = 'C:\Users\<User>\desktop\destination' # Copy template to here

# Create a new directory named some placeholder text and user input, at the destination path
New-Item -Name ($Str1 + $Str2) -ItemType Directory -Path $DestinationPath

# Copy the contents of my template folder, including all of its contents to the newly made directory
Copy-Item -Path $TemplatePath -Destination ($DestinationPath + ($Str1 + $Str2)) -Recurse

# Open the destination path
ii ($DestinationPath)
```

There are a lot more moving parts that I've trimmed from this but it boils down to the same idea. You could also -join $Str1 and $Str2 inside of one variable but the way it works out I have some cases where I only want the user input for renaming certain things.
