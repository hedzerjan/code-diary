## paging in datagrid
### index moet goed geconfigureerd zijn
```csharp
            .DataSourceOptions(o => o.
                Paginate(true)
                .PageSize(10))
            .RemoteOperations(true)
```
## controller moet 'm voeden
Dit werkt nog maar beperkt, alleen skip en take doen het maar filter wordt genegeerd.
```csharp
                count = users.Count;
                //users = users.Skip(loadOptions.Skip).Take(loadOptions.Take).ToList();
            }
            LoadResult result = DataSourceLoader.Load(users, loadOptions);
            result.totalCount = count;
            return result;
```