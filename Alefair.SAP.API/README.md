# Alefair.SAP.API

> SAP API based by *Interop.SAPFEWSELib.dll*and *Interop.SapROTWr.dll*

## Methods:

*class* **SAPAPI**
- [GetConnections](#GetConnections)
- [GetSessions](#GetSessions)
- [Connect](#Connect)
- [CloseConnection](#CloseConnection)
- [CloseSession](#CloseSession)
- [CreateSession](#CreateSession)
- [GetConnection](#GetConnection)
- [GetSession](#GetSession)
- [CheckSAP](#CheckSAP)


*class* **SAPTABLE**
- ExtractTable
- ExtractFirstVisibleRows
- OnlyColumns
- GetShellTable


*class* **EXTENSION**
- SelectorType
- OpenTransaction


## Examples

```csharp
/// Init SAPAPI object, The sap should open if exist
///
SAPAPI gui = new SAPIPI();
```


#### GetConnections

```csharp
/// Method get a Dictionary of open connections
/// Key is an Id of connection
/// Value is an instance of GuiConnection
///
Dictionary<string, object> connections = gui.GetConnections();

-> connections["/app/con[0]"] = <COMObject <unknown>>
```


#### GetSessions

```csharp
/// Method get a Dictionary of open sessions
/// Key is an Id of session
/// Value is an instance of GuiSession
///
Dictionary<string, object> sessions = gui.GetSessions();

-> sessions["/app/con[0]/ses[0]"] = <COMObject <unknown>>
```


#### Connect

```csharp
/// Method create new Connection of GuiConnection object with username, password and base name
///
GuiConnection connection = gui.Create(string login, SecureString pswd, string basename);

-> connection <COMObject <unknown>>
```



#### CloseConnection

```csharp
/// Method closes an open connection
/// by connection           - conn:connection(-s)
/// by id                   - id:"/app/con[0]"
/// by number of connection - child:0
/// close all connections   - all:true

gui.CloseConnection(GuiConnection conn = null, string id = "", int child = -1, bool all = false);

///gui.CloseConnection(connection);
///gui.CloseConnection(id:id_conn);
///gui.CloseConnection(child:child_conn);
///gui.CloseConnection(all:true);

-> 
```



#### CreateSession

```csharp
/// Method creates a new session from the connection
/// 
GuiSession session = gui.CreateSession(GuiConnection conn = null);

-> session <COMObject <unknown>>
```



#### GetConnection

```csharp
/// Method gives the instance of the GuiConnection object by ID
/// 
GuiConnection connection = gui.GetConnection(int connNumber = 0);

-> connection <COMObject <unknown>>
```



#### GetSession

```csharp
/// Method gives the instance of the GuiSession object by ID and connection
/// 
GuiSession session = gui.GetSession(GuiConnection conn, int sessNumber = 0);

-> session <COMObject <unknown>>
```



#### CheckSAP

```csharp
/// Method checks whether the Saplogon is running or not
/// 
gui.CheckSAP();

-> true
```
