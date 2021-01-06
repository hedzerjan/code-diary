# How to add the MS DI framework to a console application
When you create a new application based on one of the ASP.Net templates, you get DI for free, it's already setup from the get go. But when you create a console application, you have to add it yourself. There's actually not much to it to add it yourself, it's a three step operation:
1. Add the DI package.
2. Create a ServiceCollection.
3. Build a ServiceProvider from the ServiceCollection.

I compiled this mainly from [this MS document](https://docs.microsoft.com/en-us/archive/msdn-magazine/2016/june/essential-net-dependency-injection-with-net-core) which is a thorough article on it.

## Add the DI package
This is as simple as:
```
dotnet add package Microsoft.Extensions.DependencyInjection
```

And of course between `add` and `package` you can enter the reference to your project file.

## Create a ServiceCollection
This is as simple as `new`-ing it:
```csharp
            var serviceCollection = new ServiceCollection();
```

## Build a ServiceProvider
Again, just one command:
```csharp
            var serviceProvider = serviceCollection.BuildServiceProvider();
```
Of course, to have any use out of it, you need to add some services and kick it off by getting one of them:
```csharp
            serviceCollection.AddTransient<ISomethingDoer, SomethingDoer>();
            serviceCollection.AddTransient<IManager, Manager>();
            var serviceProvider = serviceCollection.BuildServiceProvider();
            var manager = serviceProvider.GetRequiredService<IManager>();
            manager.OrderSomething();
``