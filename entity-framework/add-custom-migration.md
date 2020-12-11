# How to add a migration when everything is tailored...

When you have multiple contexts and they're in specific spots you need to give specific instructions to the EF Core migrations tooling. The commands run here are run from the src directory, the same where the AuthServer.csproj is located.

```powershell
dotnet ef migrations add 'AuthenticatorKey' -p .\AuthServer.csproj -c AuthServer.Data.OmgevingContext -o 'Data\Migrations\Omgeving'
```

## Listing the existing migrations
By default this will fail without any explanation; it was caused by not being able to find the migrations and/or contexts. So this works:
```powershell
dotnet ef migrations list -p .\AuthServer.csproj -c AuthServer.Data.OmgevingContext
```

## Locale test
```powershell
dotnet ef migrations add 'localization' -p .\src\Infrastructure\Infrastructure.csproj -s .\src\Web\Web.csproj -c Infrastructure.Data.Contexts.LocaleDbContext -o .\src\Infrastructure\Data\Migrations\Locale
```