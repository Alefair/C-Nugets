![logo](https://raw.githubusercontent.com/Alefair/C-Nugets/main/Alefair.SAP.API/Images/saplogo_nuget.png)
# Alefair.SAP.API

```
SAP API based by Interop.SAPFEWSELib.dll  and  Interop.SapROTWr.dll
```

>Current version **[1.0.3](https://github.com/Alefair/C-Nugets/blob/main/Alefair.SAP.API/Packages/Alefair.SAP.API.1.0.3.nupkg)**

## [*class* **SAPAPI**](#SAPAPI)

### Properties
(added 1.0.3)
- [LogDateFormat](LogDateFormat)
- [Logging](Logging)
- [PID](PID)

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


<hr>


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
Console.WriteLine(gui.LogDateFormat) -> "MM/dd/yyyy HH:mm:ss.fff"
gui.LogDateFormat = "dd.MM.yyyy HH:mm:ss.fff"
```
[back |](#class-sapapi)


#### **Logging**
--property--

```csharp
/// Disable/Enable Logging for SAPAPI class
/// gui.Logging {get; set;}
Console.WriteLine(gui.Logging) -> false
gui.Logging = true
```
[back |](#class-sapapi)


#### **PID**
--property--

```csharp
/// Gets current instance of running Saplogon
/// gui.PID {get;}
Console.WriteLine(gui.PID) -> 84404
```
[back |](#class-sapapi)



#### GetConnections

```csharp
/// Method get a Dictionary of open connections
/// Key is an Id of connection
/// Value is an instance of GuiConnection
///
Dictionary<string, object> connections = gui.GetConnections();

-> connections["/app/con[0]"] = <COMObject <unknown>>
```
[back |](#Methods)



#### GetSessions

```csharp
/// Method get a Dictionary of open sessions
/// Key is an Id of session
/// Value is an instance of GuiSession
///
Dictionary<string, object> sessions = gui.GetSessions();

-> sessions["/app/con[0]/ses[0]"] = <COMObject <unknown>>
```
[back |](#Methods)



#### Connect

```csharp
/// Method create new Connection of GuiConnection object with username, password and base name
///
object connection = gui.Connect(string Login, SecureString Pswd, string Basename);

-> connection <COMObject <unknown>>
```
[back |](#Methods)



#### CloseConnection

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
[back |](#Methods)




#### CloseSession

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
[back |](#Methods)


#### CreateSession

```csharp
/// Method creates a new session from the connection
/// 
object session = gui.CreateSession(object Conn = null);

-> session <COMObject <unknown>>
```
[back |](#Methods)



#### GetConnection

```csharp
/// Method gives the instance of the GuiConnection object by ID
/// 
object connection = gui.GetConnection(int connNumber = 0);

-> connection <COMObject <unknown>>
```
[back |](#Methods)



#### GetSession

```csharp
/// Method gives the instance of the GuiSession object by ID and connection
/// 
object session = gui.GetSession(object Conn, int SessNumber = 0);

-> session <COMObject <unknown>>
```
[back |](#Methods)



#### CheckSAP

```csharp
/// Method checks whether the Saplogon is running or not
/// 
gui.CheckSAP();

-> true
```
[back |](#Methods)




### *class* **SAPTABLE**


```csharp
/// Init SAPTABLE object, read GuiGridView table to DataTable
/// selector is an id of GuiGridView table, for example: "wnd[0]/usr/cntlGRID1/shellcont/shell"
/// autodouble is an option, parse value to double, for example: 0,123- -> double -0.123
///
SAPTABLE tbl = new SAPTABLE(GuiSession session, string selector, bool autodouble = true);
```
[back |](#Methods)



#### ExtractTable

```csharp
/// Method gets a DataTable with columns type by default
/// ColumnsType.type_default -> Column_1, Column_2...
/// ColumnsType.type_1       -> column name as is
/// ColumnsType.type_2       -> column name as name in report of sap
/// ColumnsType.type_3       -> column name as name of tooltip
///
DataTable table = tbl.ExtractTable(ColumnsType clmntype = ColumnsType.type_default);

-> DataTable(){"Column_1", "Column_2"...}
```
[back |](#Methods)



#### ExtractFirstVisibleRows

```csharp
/// Method gets a List<int> of parameters .FirstVisibleRow
///
List<int> fvrc = tbl.ExtractFirstVisibleRows();

-> List<int> {0, 40, 81, 122}
```
[back |](#Methods)



#### GetTechNamesColumns

```csharp
/// Method gets a DataTable of only tech columns names
/// Option clmntype gets a real column name
///
/// ColumnsType.type_default -> Column_1, Column_2...
/// ColumnsType.type_1       -> column name as is
/// ColumnsType.type_2       -> column name as name in report of sap
/// ColumnsType.type_3       -> column name as name of tooltip
DataTable dtTech = tbl.GetTechNamesColumns(ColumnsType clmntype = ColumnsType.type_default);

-> DataTable() {"Column Number", "Name", "Value"}
```
[back |](#Methods)



#### OnlyColumns

```csharp
/// Method gets a DataTable of only columns names
/// ColumnsType.type_default -> Column_1, Column_2...
/// ColumnsType.type_1       -> column name as is
/// ColumnsType.type_2       -> column name as name in report of sap
/// ColumnsType.type_3       -> column name as name of tooltip
DataTable dtClone = tbl.OnlyColumns(ColumnsType clmntype = ColumnsType.type_default);

-> DataTable(){"Column_1", "Column_2"...}
```
[back |](#Methods)



### *class* **EXTENSION**



#### SelectorType

```csharp
/// Method gets a type name of GuiComponent
///
string selectortype = session.SelectorType("wnd[0]/usr/cntlGRID1/shellcont/shell");

-> selectortype = "GuiGridView"
```
[back |](#Methods)




#### GetTitle

```csharp
/// Method gets a title window
string title = session.GetTitle();

-> title = "Transaction Name"
```
[back |](#Methods)




#### GetStatus

```csharp
/// Method gets a text from Status Bar
string status = session.GetStatus();

-> status = "Current status"
```
[back |](#Methods)
