# Customizing your powershell

Sooner or later the default powershell grows stale and you want to start customizing is. For that you'll need:
* a good terminal (see (https://www.hanselman.com/blog/how-to-make-a-pretty-prompt-in-windows-terminal-with-powerline-nerd-fonts-cascadia-code-wsl-and-ohmyposh))
* prompt replacement (same link, see ohmyposh)
* PSReadLine (see (https://www.hanselman.com/blog/you-should-be-customizing-your-powershell-prompt-with-psreadline))

On a mac the steps are pretty straighforward:
```powershell
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
Install-Module PSReadLine -AllowPrerelease -Force
```

And the you need to edit your profile with `code -n %PROFILE`. Mine is currently set to:
```powershell
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme Paradox
if ($host.Name -eq 'ConsoleHost')
{
    Import-Module PSReadLine
}
Set-PSReadLineOption -EditMode Vi
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward

function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange

Get-PSReadLineKeyHandler
```