# Alefair.SAP.API

<div>SAP API based by <p style="color: darkblue;"><i>Interop.SAPFEWSELib.dll</i></p> and <i>Interop.SapROTWr.dll</i></div>

## Methods:

*class* **SAPAPI**
- [GetConnections](#GetConnections)
- GetSessions
- Connect
- CloseConnection
- CloseSession
- CreateSession
- GetConnection
- GetSession
- CheckSAP


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


<div id="GetConnections">GetConnections</div>

```csharp
/// Method gets a Dictionary of open connections
/// Key is an Id of connection
/// Value is an instance of GuiConnection
///
Dictionary<string, object> connections = gui.GetConnections

-> connections["/app/con[0]"] = <COMObject <unknown>>
```
