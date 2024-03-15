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
pwsh bin/Debug/net8.0/playwright.ps1 codegen triasweb.nl/triaspectdemo
```

## Tips&tricks
Getting the value of the `option` that's currently selected in a `select`:
```c#
var voorstart = await page.EvaluateAsync<string>(@"() => {
    const select = document.getElementById('ctl00_ContentPlaceHolder1_cntTabs_cboTRJVoorTraject');
    return select.options[select.selectedIndex].text;
    }");

```
Wait the page to refresh after selecting a different `option`:
```c#
await page.RunAndWaitForRequestFinishedAsync(async () => await page.Locator("#ctl00_ContentPlaceHolder1_cntTabs_lstTRJLijst").SelectOptionAsync(doorstart.Id.ToString()));
```