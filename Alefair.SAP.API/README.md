# Alefair.SAP.API

> SAP API based by *Interop.SAPFEWSELib.dll*and *Interop.SapROTWr.dll*

## Methods:

[*class* **SAPAPI**](#class-sapapi)
- [GetConnections](#GetConnections)
- [GetSessions](#GetSessions)
- [Connect](#Connect)
- [CloseConnection](#CloseConnection)
- [CloseSession](#CloseSession)
- [CreateSession](#CreateSession)
- [GetConnection](#GetConnection)
- [GetSession](#GetSession)
- [CheckSAP](#CheckSAP)


[*class* **SAPTABLE**](#class-saptable)
- [ExtractTable](#ExtractTable)
- [ExtractFirstVisibleRows](#ExtractFirstVisibleRows)
- [OnlyColumns](#OnlyColumns)


[*class* **EXTENSION**](#class-extension)
- [SelectorType](#SelectorType)


## Examples


### *class* **SAPAPI**

```csharp
/// Init SAPAPI object, The sap should open if exist
///
SAPAPI gui = new SAPIPI();
```
[back |](#Methods)



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
GuiConnection connection = gui.Create(string login, SecureString pswd, string basename);

-> connection <COMObject <unknown>>
```
[back |](#Methods)



#### CloseConnection

```csharp
/// Method closes an open connection
/// by connection           - conn:connection(-s)
/// by id                   - id:"/app/con[0]"
/// by number of connection - child:0
/// close all connections   - all:true
///
gui.CloseConnection(GuiConnection conn = null, string id = "", int child = -1, bool all = false);

///gui.CloseConnection(connection);
///gui.CloseConnection(id:id_conn);
///gui.CloseConnection(child:child_conn);
///gui.CloseConnection(all:true);

-> 
```
[back |](#Methods)



#### CreateSession

```csharp
/// Method creates a new session from the connection
/// 
GuiSession session = gui.CreateSession(GuiConnection conn = null);

-> session <COMObject <unknown>>
```
[back |](#Methods)



#### GetConnection

```csharp
/// Method gives the instance of the GuiConnection object by ID
/// 
GuiConnection connection = gui.GetConnection(int connNumber = 0);

-> connection <COMObject <unknown>>
```
[back |](#Methods)



#### GetSession

```csharp
/// Method gives the instance of the GuiSession object by ID and connection
/// 
GuiSession session = gui.GetSession(GuiConnection conn, int sessNumber = 0);

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
string selectortype = session.SelectorType("wnd[0]/usr/cntlGRID1/shellcont/shell");

-> selectortype = "GuiGridView"
```
[back |](#Methods)
