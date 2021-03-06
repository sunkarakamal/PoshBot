---
external help file: Builtin-help.xml
online version: 
schema: 2.0.0
---

# Disable-Plugin

## SYNOPSIS
Disable a currently loaded plugin.

## SYNTAX

```
Disable-Plugin -Bot <Object> [-Name] <String> [[-Version] <String>]
```

## DESCRIPTION
{{Fill in the Description}}

## EXAMPLES

### -------------------------- EXAMPLE 1 --------------------------
```
!disable-plugin nameit
```

Disable the \[NameIt\] plugin.

### -------------------------- EXAMPLE 2 --------------------------
```
!disable-plugin --name PoshBot.XKCD --version 1.0.0
```

Disable version \[1.0.0\] of the \[PoshBot.XKCD\] module.

## PARAMETERS

### -Bot
{{Fill Bot Description}}

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
The name of the plugin to disable.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version
The specific version of the plugin to disable.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS

