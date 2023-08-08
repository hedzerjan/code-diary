# Accessing private nuget feeds
There are multiple ways to do this but the safest and easiest way is with the use of a nuget credentials provider.

Install the provider with:

```
sh -c "$(curl -fsSL https://aka.ms/install-artifacts-credprovider.sh)"
```
And then restore the packages with:
```
dotnet restore --interactive
```