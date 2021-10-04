# Alwebiee.PostgreSQL.DBInteraction (Under Preview)
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

#### Inherit abstract class 'PostgreSQLDBInteraction' from Alwebiee.PostgreSQL.DBInteraction package as shown below code.
```
using Alwebiee.PostgreSQL.DBInteraction;

namespace DemoFrameworks
{
    public class Test : PostgreSQLDBInteraction
    {        
    }
}
```
# List of Methods in the 'PostgreSQLDBInteraction' class and Its purposes

#### 1. How to get connection string from webconfig?
```
    string connstring = GetConnectionStringFromWebConfig("Keynamefromwebconfig");
```

#### 2. How to save data to the database tabe?
```
using Alwebiee.PostgreSQL.DBInteraction;
using System.Collections.Generic;
using System.Data;

namespace DemoFrameworks
{
    public class Test : PostgreSQLDBInteraction
    {
        public void Save(string Name, string Emailid, string PhoneNumber)
        {
            string connstring = GetConnectionStringFromWebConfig("MasterConnection"); //getting connection string from webconfig

            string postgreSQLFunctionName = "save_contact"; // function name of a postgresql
            List<string> paramNames = new List<string> { "@_name", "@_emailid", "@_phonenumber" }; //parameters of a function
            object[] objDat = { Name, Emailid, PhoneNumber }; //pass data to function

            using (IDbCommand Command = GetDBCommand(connstring, postgreSQLFunctionName, paramNames, objDat))
            {
                bool result = Save(Command);
                //int result = Save<int>(Command);
            }
        }
    }
}
```
#### 3. How to update data to the database tabe?
```
using Alwebiee.PostgreSQL.DBInteraction;
using System.Collections.Generic;
using System.Data;

namespace DemoFrameworks
{
    public class Test : PostgreSQLDBInteraction
    {
        public void Update(string Name, string Emailid, string PhoneNumber)
        {
            string connstring = GetConnectionStringFromWebConfig("MasterConnection"); //getting connection string from webconfig

            string postgreSQLFunctionName = "save_contact"; // function name of a postgresql
            List<string> paramNames = new List<string> { "@_name", "@_emailid", "@_phonenumber" }; //parameters of a function
            object[] objDat = { Name, Emailid, PhoneNumber }; //pass data to function

            using (IDbCommand Command = GetDBCommand(connstring, postgreSQLFunctionName, paramNames, objDat))
            {
                int result = Update(Command);
            }
        }
    }
}
```


#### 4. How to delete data from the database tabe?
```
using Alwebiee.PostgreSQL.DBInteraction;
using System.Collections.Generic;
using System.Data;

namespace DemoFrameworks
{
    public class Test : PostgreSQLDBInteraction
    {
        public void Delete(string Name, string Emailid, string PhoneNumber)
        {
            string connstring = GetConnectionStringFromWebConfig("MasterConnection"); //getting connection string from webconfig

            string postgreSQLFunctionName = "save_contact"; // function name of a postgresql
            List<string> paramNames = new List<string> { "@_name", "@_emailid", "@_phonenumber" }; //parameters of a function
            object[] objDat = { Name, Emailid, PhoneNumber }; //pass data to function

            using (IDbCommand Command = GetDBCommand(connstring, postgreSQLFunctionName, paramNames, objDat))
            {
                int result = Delete(Command);
            }
        }
    }
}
```

#### 5. How to delete data from the database tabe?
```
using Alwebiee.PostgreSQL.DBInteraction;
using System.Collections.Generic;
using System.Data;

namespace DemoFrameworks
{
    public class Test : PostgreSQLDBInteraction
    {
        public void BulkInsert(string Name, string Emailid, string PhoneNumber)
        {
            DataTable dt = new DataTable();
            dt.Columns.Add("Id", typeof(long)); // Map as mentioned in the postgre table data type 'Bigint'
            dt.Columns.Add("Name", typeof(string)); // Map as mentioned in the postgre table data type 'Text'
            dt.Columns.Add("Emailid", typeof(string)); // Map as mentioned in the postgre table data type 'Text'
            dt.Rows.Add(1,"test","test@gmail.com");

            string connstring = GetConnectionStringFromWebConfig("MasterConnection"); //getting connection string from webconfig
            
            BulkInsert(connstring, dt, "contact"); //connectionstring, datatable and table name of a postgreSQL
        }
    }
}

```

