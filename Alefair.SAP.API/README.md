![logo](https://raw.githubusercontent.com/Alefair/C-Nugets/main/Alefair.SAP.API/Images/saplogo_nuget.png)
# Alefair.SAP.API

```
SAP API based by Interop.SAPFEWSELib.dll  and  Interop.SapROTWr.dll
```

>Current version **[1.0.4](https://github.com/Alefair/C-Nugets/blob/main/Alefair.SAP.API/Packages/Alefair.SAP.API.1.0.4.nupkg)**
>

>[nuget](https://www.nuget.org/packages/Alefair.SAP.API/1.0.4) on https://www.nuget.org

## [*class* **SAPAPI**](#SAPAPI)

### Properties

(added 1.0.3)
- [LogDateFormat](#LogDateFormat)
- [Logging](#Logging)
- [PID](#PID)

(added 1.0.4)
- [Application](#Application)
- [HWND](#HWND)
- [ProcessName](#ProcessName)

### Methods:
- [CheckSAP](#CheckSAP)
- [CloseConnection](#CloseConnection)
- [CloseSession](#CloseSession)
- [Connect](#Connect)
- [CreateSession](#CreateSession)
- [GetConnection](#GetConnection)
- [GetConnections](#GetConnections)
- [GetSession](#GetSession)
- [GetSessions](#GetSessions)
- [GetListConnections](#GetListConnections) - Experimental Method(added 1.0.4)



## [*class* **SAPTABLE**](#SAPTABLE)

### Properties
(added 1.0.3)
- [ColumnsCount](#ColumnsCount)
- [DefaultColumnName](#DefaultColumnName)
- [DefaultSuffixColumnName](#DefaultSuffixColumnName)
- [GuiTable](#GuiTable)
- [Id](#Id)
- [RowsCount](#RowsCount)


### Methods:
- [ExtractFirstVisibleRows](#ExtractFirstVisibleRows)
- [ExtractTable](#ExtractTable)
- [GetTechNamesColumns](#GetTechNamesColumns)
- [OnlyColumns](#OnlyColumns)


## [*class* **EXTENSION**](#EXTENSION)

### Methods:
- [SelectorType](#SelectorType)
- [GetTitle](#GetTitle)  (added 1.0.2)
- [GetStatus](#GetStatus)  (added 1.0.2)


***


### **SAPAPI**
--class--

```csharp
/// Init SAPAPI object, The sap should open if exist
///
SAPAPI gui = new SAPAPI(string path = @"C:\Program Files (x86)\SAP\FrontEnd\SAPgui\saplogon.exe", int timeout = 2000, bool logging = false)

-> SAPAPI gui  { LogDateFormat="MM/dd/yyyy HH:mm:ss.fff", Logging=true, PID=84404 }
```
[back |](#class-sapapi)


#### **LogDateFormat**
--property--

```csharp
/// DateTime format for logging
/// gui.LogDateFormat {get; set;}
Console.WriteLine(gui.LogDateFormat); -> "MM/dd/yyyy HH:mm:ss.fff"
gui.LogDateFormat = "dd.MM.yyyy HH:mm:ss.fff";
```
[back |](#class-sapapi)


#### **Logging**
--property--

```csharp
/// Disable/Enable Logging for SAPAPI class
/// gui.Logging {get; set;}
Console.WriteLine(gui.Logging); -> false
gui.Logging = true;
```
[back |](#class-sapapi)


#### **PID**
--property--

```csharp
/// Gets current process id of running Saplogon
/// gui.PID {get;}
Console.WriteLine(gui.PID); -> 84404
```
[back |](#class-sapapi)


#### **Application**
--property--

```csharp
/// Gets current instance application of running Saplogon
/// gui.Application {get;}
object app = gui.Application); 

-> app <COMObject <unknown>>
```
[back |](#class-sapapi)


#### **HWND**
--property--

```csharp
/// Gets current window handle
/// gui.HWND {get;}
Console.WriteLine(gui.HWND); -> 2178945
```
[back |](#class-sapapi)


#### **ProcessName**
--property--

```csharp
/// Gets current process window title
/// gui.ProcessName {get;}
Console.WriteLine(gui.ProcessName); -> "SAP Logon 760"
```
[back |](#class-sapapi)


#### **GetConnections**
--Method--

```csharp
/// Method get a Dictionary of open connections
/// Key is an Id of connection
/// Value is an instance of GuiConnection
///
Dictionary<string, object> connections = gui.GetConnections();

-> connections["/app/con[0]"] = <COMObject <unknown>>
```
[back |](#class-sapapi)



#### **GetSessions**
--Method--

```csharp
/// Method get a Dictionary of open sessions
/// Key is an Id of session
/// Value is an instance of GuiSession
///
Dictionary<string, object> sessions = gui.GetSessions();

-> sessions["/app/con[0]/ses[0]"] = <COMObject <unknown>>
```
[back |](#class-sapapi)



#### **Connect**
--Method--

```csharp
/// Method create new Connection of GuiConnection object with username, password and base name
///
object connection = gui.Connect(string Login, SecureString Pswd, string Basename);

-> connection <COMObject <unknown>>
```
[back |](#Methods)



#### **CloseConnection**
--Method--

```csharp
/// Method closes an open connection(-s)
/// by connection           - Conn:connection
/// by id                   - Id:"/app/con[0]"
/// by number of connection - Child:0
/// close all connections   - All:true
///
gui.CloseConnection(object Conn = null, string Id = "", int Child = -1, bool All = false);

///gui.CloseConnection(connection);
///gui.CloseConnection(Id:id_conn);
///gui.CloseConnection(Child:child_conn);
///gui.CloseConnection(All:true);

-> 
```
[back |](#class-sapapi)




#### **CloseSession**
--Method--

```csharp
/// Method closes an open session(-s)
/// by connection, session           - Conn:connection, Sess:session
/// by id                            - Id:"/app/con[0]"
/// by connection, number of session - Conn:connection, Child:0
/// close all session                - All:true
///
gui.CloseSession(object Conn = null, object Sess = null, string Id = "", int Child = -1, bool All = false);

///gui.CloseSession(connection, session);
///gui.CloseSession(Id:id_sess);
///gui.CloseSession(connection, Child:child_sess);
///gui.CloseSession(connection, All:true);
///gui.CloseSession(All:true);

-> 
```
[back |](#class-sapapi)


#### **CreateSession**
--Method--

```csharp
/// Method creates a new session from the connection
/// 
object session = gui.CreateSession(object Conn = null);

-> session <COMObject <unknown>>
```
[back |](#class-sapapi)



#### **GetConnection**
--Method--

```csharp
/// Method gives the instance of the GuiConnection object by ID
/// 
object connection = gui.GetConnection(int connNumber = 0);

-> connection <COMObject <unknown>>
```
[back |](#class-sapapi)



#### **GetSession**
--Method--

```csharp
/// Method gives the instance of the GuiSession object by ID and connection
/// 
object session = gui.GetSession(object Conn, int SessNumber = 0);

-> session <COMObject <unknown>>
```
[back |](#class-sapapi)



#### **CheckSAP**
--Method--

```csharp
/// Method checks whether the Saplogon is running or not
/// 
gui.CheckSAP();

-> true
```
[back |](#class-sapapi)



#### **GetListConnections**
--Experimental Method--

```csharp
/// Method gets list of connections on start page of Saplogon
/// 
/// By manual automationId of Table with connections - 1008, automationId of buttons with list - 59410
/// Support only SAP theme with buttons choice(see screenshot later)

List<string> basenames = GetListConnections(int id = 1008, int btn = 59410);

-> basenames<string> = {"Base Name 1", "Base Name 2"...}
```

![Choice](https://raw.githubusercontent.com/Alefair/C-Nugets/main/Alefair.SAP.API/Images/Choice.PNG)

[back |](#class-sapapi)


***

### **SAPTABLE**
--class--

```csharp
/// Init SAPTABLE object, read GuiGridView table to DataTable
/// selector is an id of GuiGridView table, for example: "wnd[0]/usr/cntlGRID1/shellcont/shell"
/// autodouble is an option, parse value to double, for example: 0,123- -> double -0.123
///
SAPTABLE tbl = new SAPTABLE(object Session, string Selector, bool Autodouble = true);
```
[back |](#class-saptable)


#### **ColumnsCount**
--property--

```csharp
/// Gets columns count
/// tbl.ColumnsCount {get;}
Console.WriteLine(tbl.ColumnsCount); -> 52
```
[back |](#class-saptable)


#### **DefaultColumnName**
--property--

```csharp
/// Gets/Sets Default Column Name
/// tbl.DefaultColumnName {get; set;}
Console.WriteLine(tbl.DefaultColumnName); -> "Column"
tbl.DefaultColumnName = "Clmn";

-> {"Clmn_0", "Clmn_1"....}
```
[back |](#class-saptable)


#### **DefaultSuffixColumnName**
--property--

```csharp
/// Gets/Sets suffix default column name
/// tbl.DefaultSuffixColumnName {get; set;}
Console.WriteLine(tbl.DefaultSuffixColumnName); -> "_"
tbl.DefaultColumnName = "-";

-> {"Clmn-0", "Clmn-1"....}
```
[back |](#class-saptable)



#### **GuiTable**
--property--

```csharp
/// Gets instance GuiComponent of table 
/// tbl.GuiTable {get;}
GuiGridView table = tbl.GuiTable;

-> table <COMObject <unknown>>
```
[back |](#class-saptable)



#### **Id**
--property--

```csharp
/// Gets Id of table
/// tbl.Id {get;}
Console.WriteLine(tbl.Id); -> wnd[0]/usr/cntlGRID1/shellcont/shell

```
[back |](#class-saptable)


#### **RowsCount**
--property--

```csharp
/// Gets rows count
/// tbl.RowsCount {get;}
Console.WriteLine(tbl.RowsCount; -> 320
```
[back |](#class-saptable)



#### **ExtractTable**
--Method--

```csharp
/// Method gets a DataTable with columns type by default
///
/// [unavailable after 1.0.3] ColumnsType.type_default -> Column_1, Column_2...
/// [unavailable after 1.0.3] ColumnsType.type_1       -> column name as is
/// [unavailable after 1.0.3] ColumnsType.type_2       -> column name as name in report of sap
/// [unavailable after 1.0.3] ColumnsType.type_3       -> column name as name of tooltip
///
/// [unavailable after 1.0.3] DataTable table = tbl.ExtractTable(ColumnsType clmntype = ColumnsType.type_default);
///
/// ColumnNameType.FULLNAME
/// ColumnNameType.DISPLAYNAME
/// ColumnNameType.TOOLTIP
/// ColumnNameType.TECHNAMES
/// ColumnNameType.DEFAULT


DataTable table = tbl.ExtractTable(ColumnsType clmntype = ColumnsType.type_default);

-> DataTable(){"Column_1", "Column_2"...}
```
[back |](#class-saptable)



#### **ExtractFirstVisibleRows**
--Method--

```csharp
/// Method gets a List<int> of parameters .FirstVisibleRow
///
List<int> fvrc = tbl.ExtractFirstVisibleRows();

-> List<int> {0, 40, 81, 122}
```
[back |](#class-saptable)



#### **GetTechNamesColumns**
--Method--

```csharp
/// Method gets a DataTable of only tech columns names
/// Option clmntype gets a real column name
///
/// [unavailable after 1.0.3] ColumnsType.type_default -> Column_1, Column_2...
/// [unavailable after 1.0.3] ColumnsType.type_1       -> column name as is
/// [unavailable after 1.0.3] ColumnsType.type_2       -> column name as name in report of sap
/// [unavailable after 1.0.3] ColumnsType.type_3       -> column name as name of tooltip
/// [unavailable after 1.0.3] DataTable dtTech = tbl.GetTechNamesColumns(ColumnsType clmntype = ColumnsType.type_default);
///
/// ColumnNameType.FULLNAME
/// ColumnNameType.DISPLAYNAME
/// ColumnNameType.TOOLTIP
/// ColumnNameType.TECHNAMES
/// ColumnNameType.DEFAULT

DataTable dtTech = tbl.GetTechNamesColumns(ColumnNameType clmntype = ColumnNameType.DEFAULT);

-> DataTable() {"Column Number", "Name", "Value"}
```
[back |](#class-saptable)



#### **OnlyColumns**
--Method--

```csharp
/// Method gets a DataTable of only columns names
/// [unavailable after 1.0.3] ColumnsType.type_default -> Column_1, Column_2...
/// [unavailable after 1.0.3] ColumnsType.type_1       -> column name as is
/// [unavailable after 1.0.3] ColumnsType.type_2       -> column name as name in report of sap
/// [unavailable after 1.0.3] ColumnsType.type_3       -> column name as name of tooltip
/// [unavailable after 1.0.3] DataTable dtClone = tbl.OnlyColumns(ColumnsType clmntype = ColumnsType.type_default);
///
/// ColumnNameType.FULLNAME
/// ColumnNameType.DISPLAYNAME
/// ColumnNameType.TOOLTIP
/// ColumnNameType.TECHNAMES
/// ColumnNameType.DEFAULT

DataTable dtClone = tbl.OnlyColumns(ColumnNameType clmntype = ColumnNameType.DEFAULT);

-> DataTable(){"Column_1", "Column_2"...}
```
[back |](#class-saptable)


***


### **EXTENSION**
--class--


#### **SelectorType**
--Method--

```csharp
/// Method gets a type name of GuiComponent
///
string selectortype = session.SelectorType("wnd[0]/usr/cntlGRID1/shellcont/shell");

-> selectortype = "GuiGridView"
```
[back |](#class-extension)




#### **GetTitle**
--Method--

```csharp
/// Method gets a title window
string title = session.GetTitle();

-> title = "Transaction Name"
```
[back |](#class-extension)




#### **GetStatus**
--Method--

```csharp
/// Method gets a text from Status Bar
string status = session.GetStatus();

-> status = "Current status"
```
[back |](#class-extension)
