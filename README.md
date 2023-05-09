# KYH-BLAZOR

Demo projekt för att visa en del av vad man kan utveckla med blazor utan att använda javascript

## Teknik

Detta projekt använder följande tekniker

- Entity Framework with MS SQLSERVER
- .net7

## Krav för att köra projektet

- SQL Server
- .net 7 runtime
- Visual Studio 2022

## Struktur

En Solution som innehåller 1 projekt enligt följande.

### BlazorDemo.Backend

En class bibliotek projekt som sköter backend delen som databas anslutningen och services som ansvarar för att prata med databasen åt klienten.

Detta innehåller även några DTO modeller och en AutoMapper config.

Justera appsettings för att inkludera connection string


```json
"ConnectionStrings": {
    "DefaultConnection": "Server=localhost;database=KYHBlazorDemo;Trusted_Connection=True;Integrated Security=true;TrustServerCertificate=True;"
  }
```

Lägg till migration coden i program.cs

```csharp
using (var scope = app.Services.CreateScope())
{
    var service = scope.ServiceProvider.GetService<DataInitializer>();
    if (service is not null)
        await service.MigrateDataAsync();
}
```