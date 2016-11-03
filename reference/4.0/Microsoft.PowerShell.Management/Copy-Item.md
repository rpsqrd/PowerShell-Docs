﻿---
author: jpjofre
description: 
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell, cmdlet
manager: carolz
ms.date: 2016-09-27
ms.prod: powershell
ms.technology: powershell
ms.topic: reference
online version: http://go.microsoft.com/fwlink/p/?linkid=290483
schema: 2.0.0
title: Copy-Item
---

# Copy-Item

## SYNOPSIS
Copies an item from one location to another.

## SYNTAX

### Path (Default)
```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath
```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION
The Copy-Item cmdlet copies an item from one location to another location in the same namespace.
For example, it can copy a file to a folder, but it cannot copy a file to a certificate drive.

Copy-Item does not cut or delete the items being copied.
The particular items that the cmdlet can copy depend on the Windows PowerShell provider that exposes the item.
For example, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.

Copy-Item can copy and rename items in the same command.
To rename an item, enter the new name in the value of the Destination parameter.
To rename an item without copying it, use the Rename-Item cmdlet.

## EXAMPLES

### -------------------------- EXAMPLE 1 --------------------------
```
PS C:\>Copy-Item C:\Wabash\Logfiles\mar1604.log.txt -Destination C:\Presentation
```

This command copies the mar1604.log.txt file to the C:\Presentation directory.
The command does not delete the original file.

### -------------------------- EXAMPLE 2 --------------------------
```
PS C:\>Copy-Item C:\Logfiles -Destination C:\Drawings -Recurse
```

This command copies the entire contents of the Logfiles directory into the Drawings directory.
If the LogFiles directory contains files in subdirectories, those subdirectories will be copied with their file trees intact.
The Container parameter is set to true by default.
This preserves the directory structure.

### -------------------------- EXAMPLE 3 --------------------------
```
PS C:\>Copy-Item C:\Logfiles -Destination C:\Drawings\Logs -Recurse
```

This command copies the contents of the C:\Logfiles directory to the C:\Drawings\Logs directory.
It creates the \Logs subdirectory if it does not already exist.

### -------------------------- EXAMPLE 4 --------------------------
```
PS C:\>Copy-Item \\Server01\Share\Get-Widget.ps1 -Destination \\Server12\ScriptArchive\Get-Widget.ps1.txt
```

This command uses the **Copy-Item** cmdlet to copy the Get-Widget.ps1 script from the \\\\Server01\Share directory to the \\\\Server12\ScriptArchive directory.
As part of the copy operation, the command also changes the item name from Get-Widget.ps1 to Get-Widget.ps1.txt, so it can be attached to email messages.

## PARAMETERS

### -Container
Preserves container objects during the copy operation.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Specifies a user account that has permission to perform this action.
The default is the current user.

Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one generated by the Get-Credential cmdlet.
If you type a user name, you will be prompted for a password.

This parameter is not supported by any providers installed with Windows PowerShell.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Destination
Specifies the path to the new location.
To rename a copied item, include the new name in the value.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude
Omits the specified items.
Wildcards are permitted.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter
Specifies a filter in the provider's format or language.
The value of this parameter qualifies the Path parameter.
The syntax of the filter, including the use of wildcards, depends on the provider.
Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having Windows PowerShell filter the objects after they are retrieved.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force
Allows the cmdlet to copy items that cannot otherwise be changed, such as copying over a read-only file or alias.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: Force
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include
Specifies only those items upon which the cmdlet will act, excluding all others.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath
Specifies a path to the item.
The value of the LiteralPath parameter is used exactly as it is typed.
No characters are interpreted as wildcards.
If the path includes escape characters, enclose it in single quotation marks.
Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.

```yaml
Type: String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru
Returns an object representing each copied item.
By default, this cmdlet does not generate any output.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Specifies the path to the items to copy.

```yaml
Type: String[]
Parameter Sets: Path
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Recurse
Specifies a recursive copy.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction
Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see Includes the command in the active transaction.
This parameter is valid only when a transaction is in progress.
For more information, see

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String
You can pipe a string that contains a path to Copy-ItemProperty.

## OUTPUTS

### None or an object representing the copied item.
When you use the PassThru parameter, Copy-Item returns an object that represents the copied item.
Otherwise, this cmdlet does not generate any output.

## NOTES
* Copy-Item  is like the 'cp' or 'copy' commands in other shells.

  The Copy-Item cmdlet is designed to work with the data exposed by any provider.
To list the providers available in your session, type "Get-PsProvider".
For more information, see about_Providers.

*

## RELATED LINKS

[Clear-Item](Clear-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
