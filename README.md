# Alwebiee.PostgreSQL.DBInteraction
## PostgreSQL Database Access Library using ADO.NET

### Library version
.NET Standard 2.1

### Targeted Frameworks
ASP.Net Core 5 And ASP.NET Frameworks 4.8

#### Click the below link for more details
https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/

# How to implement in the code?

#### Install 'Alwebiee.PostgreSQL.DBInteraction' package from nuget.org
https://www.nuget.org/packages/Alwebiee.PostgreSQL.DBInteraction
#### OR
```
Install-Package Alwebiee.PostgreSQL.DBInteraction -Version 1.0.3
```

#### 1.Inherit abstract class 'PostgreSQLDBInteraction' from Alwebiee.PostgreSQL.DBInteraction package as shown below code.
```
using Alwebiee.PostgreSQL.DBInteraction;

namespace DemoFrameworks
{
    public class Test : PostgreSQLDBInteraction
    {        
    }
}
```
