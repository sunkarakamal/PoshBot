
# PoshBot

[![Build status](https://ci.appveyor.com/api/projects/status/9em7etgtlmeax7gl?svg=true)](https://ci.appveyor.com/project/devblackops/poshbot)
[![Documentation Status](https://readthedocs.org/projects/poshbot/badge/?version=latest)](http://poshbot.readthedocs.io/en/latest/)
[![Gratipay](https://img.shields.io/gratipay/PoshBot.svg)](https://gratipay.com/PoshBot/)

PoshBot is a chat bot written in [PowerShell](https://msdn.microsoft.com/powershell).
It makes extensive use of classes introduced in PowerShell 5.0.
PowerShell modules are loaded into PoshBot and instantly become available as bot commands.
PoshBot currently supports connecting to Slack to provide you with awesome ChatOps goodness.

<p align="center">
  <img src="https://raw.githubusercontent.com/poshbotio/PoshBot/master/Media/poshbot_logo_300_432.png" alt="PoshBot logo"/>
</p>

## What Can PoshBot Do?

Pretty much anything you want :) No seriously.
PoshBot executes functions/cmdlets from PowerShell modules.
Use PoshBot to connect to servers and report status, deploy code, execute runbooks, query APIs, etc.
If you can write it in PowerShell, PoshBot can execute it.

> Detailed documentation can be found at [ReadTheDocs](http://poshbot.readthedocs.io/en/latest/)

> See [Building PoshBot](./building.md) for documentation on how to build PoshBot from source.

## [YouTube] PoshBot Demo at the Portland User Group on 2017-05-31

[![Alt text](https://img.youtube.com/vi/36fkyKYq43c/0.jpg)](https://www.youtube.com/watch?v=36fkyKYq43cV)

## Quickstart

To get started now, get a SLACK-API-TOKEN for your bot:

[https://api.slack.com/bot-users](https://api.slack.com/bot-users)

```powershell
# Install the module from PSGallery
Install-Module -Name PoshBot -Repository PSGallery

# Import the module
Import-Module -Name PoshBot

# Create a bot configuration
$botParams = @{
    Name = 'name'
    BotAdmins = @('<SLACK-CHAT-HANDLE>')
    CommandPrefix = '!'
    LogLevel = 'Info'
    BackendConfiguration = @{
        Name = 'SlackBackend'
        Token = '<SLACK-API-TOKEN>'
    }
    AlternateCommandPrefixes = 'bender', 'hal'
}

$myBotConfig = New-PoshBotConfiguration @botParams

# Start a new instance of PoshBot interactively or in a job.
Start-PoshBot -Configuration $myBotConfig #-AsJob
```

Basic usage:

```powershell
# Create a Slack backend
$backendConfig = @{Name = 'SlackBackend'; Token = '<SLACK-API-TOKEN>'}
$backend = New-PoshBotSlackBackend -Configuration $backendConfig

# Create a PoshBot configuration
$pbc = New-PoshBotConfiguration -BotAdmins @('<MY-SLACK-HANDLE>') -BackendConfiguration $backendConfig

# Save configuration
Save-PoshBotConfiguration -InputObject $pbc -Path .\PoshBotConfig.psd1

# Load configuration
$pbc = Get-PoshBotConfiguration -Path .\PoshBotConfig.psd1

# Create an instance of the bot
$bot = New-PoshBotInstance -Configuration $pbc -Backend $backend

# Start the bot
$bot.Start()

# Available commands
Get-Command -Module PoshBot

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-PoshBot                                        0.8.0      poshbot
Function        Get-PoshBotConfiguration                           0.8.0      poshbot
Function        Get-PoshBotStatefulData                            0.8.0      poshbot
Function        New-PoshBotCardResponse                            0.8.0      poshbot
Function        New-PoshBotConfiguration                           0.8.0      poshbot
Function        New-PoshBotFileUpload                              0.8.0      poshbot
Function        New-PoshBotInstance                                0.8.0      poshbot
Function        New-PoshBotScheduledTask                           0.8.0      poshbot
Function        New-PoshBotSlackBackend                            0.8.0      poshbot
Function        New-PoshBotTextResponse                            0.8.0      poshbot
Function        Remove-PoshBotStatefulData                         0.8.0      poshbot
Function        Save-PoshBotConfiguration                          0.8.0      poshbot
Function        Set-PoshBotStatefulData                            0.8.0      poshbot
Function        Start-PoshBot                                      0.8.0      poshbot
Function        Stop-Poshbot                                       0.8.0      poshbot
```
