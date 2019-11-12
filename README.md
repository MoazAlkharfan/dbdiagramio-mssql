# dbdiagram.io diagram generator for MS SQL

Draw a database diagram from your MS SQL database in dbdiagram.io.

## The repository

* DbDiagramIo.MsSql: Library to export an MS SQL database schema into script that dbdiagram.io understands.
* Example.DotNetCore: .NET Core example application that actually creates the dbdiagram.io script by using the library.
* Example.DotNet461: .NET 4.6.1 example application.

## Try it

* set the connection string in `Example.DotNetCore\Program.cs` to point to your database
* build solution with Visual Studio
* run the application by `dotnet Example.DotNetCore.dll`
* copy&paste the application's output to https://dbdiagram.io/d
* see your database's diagram

## Create your own application

Use the DbDiagramIo.MsSql library in your code and create a better MS SQL => dbdiagram.io export tool.

### Add nuget package

```
dotnet add package DbDiagramIo.MsSql
```

### Import the namespace

```
using DbDbiagramIo.MsSql;
```

### Generate dbdiagram.io script

```
(TableDto[] tables, ForeignKeyDto[] foreignKeys) = MsSqlSchemaReader.ReadTablesAndForeignKeysFromDb( "<YOUR-DB'S-CONNECTIONSTRING>" );

foreach (TableDto table in tables)
{
    Console.WriteLine( table.ToDbDbiagramCode() );
}

foreach (ForeignKeyDto fk in foreignKeys)
{
    Console.WriteLine( fk.ToDbDiagramDto() );
}
```

## License

Licensed under the [MIT license](LICENSE).