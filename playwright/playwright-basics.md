# Playwright basics
## Installation 
And run on mac:
```bash
dotnet new nunit -n PlaywrightTests
dotnet add package Microsoft.Playwright.NUnit
```
Edit the csproj files and add:
```xml
    <PlaywrightPlatform>all</PlaywrightPlatform>
```
```bash
dotnet build
pwsh bin/Debug/net8.0/playwright.ps1 install
dotnet test -- NUnit.NumberOfTestWorkers=5
```

## Codegen
```bash
pwsh bin/Debug/net8.0/playwright.ps1 codegen triasweb.nl/bregressie
```