# Alefair.Extended.Methods


```
Extended Methods powered by Alefair
```

>Current version **[1.0.6](https://github.com/Alefair/C-Nugets/blob/main/Alefair.Extended.Methods/Packages/Alefair.Extended.Methods.1.0.6.nupkg)**
>

>[nuget](https://www.nuget.org/packages/Alefair.Extended.Methods/1.0.6) on https://www.nuget.org

***

*class* **StringExtended**
-[x] Like
-[x] ContainsInList
-[x] ToDouble
-[x] ToDoubleStr
-[x] ToDecimal
-[x] ToDecimalStr
-[x] GetSimilarity
-[x] DictToString
-[x] DictToJson
-[x] DateParse
-[x] Capitalize

*class* **DataExtended** (added 1.0.5)
-[x] ReadCSV
-[x] WriteCSV
-[x] AppendCSV

*class* **ProcessExtended** (added 1.0.6)
-[x] GetPid
-[x] Kill
-[x] GetWinHandle
-[x] GetMainWinHandle
-[x] GetWinTitle
-[x] GetProcess

***

## [*class* **StringExtended**](#StringExtended)

***

#### **Like**
```csharp
/// <summary>
/// "String".Like("*ring*") -> true
/// </summary>
/// <param name="toSearch"></param>
/// <param name="toFind"></param>
/// <param name="RegOptions"></param>
/// <returns></returns>
public static bool Like(this string toSearch, string toFind, RegexOptions RegOptions = RegexOptions.IgnoreCase)

"123 456 789".Like("456") - > true
"123 456 789".Like("^456") -> false

```

***

#### **ContainsInList**
```csharp
/// <summary>
/// "Hello, world!".ContainsInList(new List(){"world", "peace", "men"}) -> true
/// </summary>
/// <param name="toSearch"></param>
/// <param name="currentList"></param>
/// <returns></returns>
public static bool ContainsInList(this string toSearch, List<string> currentList = default(List<string>))

"123 456 789".ContainsInList({"asd", "456", "ghj"})  - > true
"123 456 789".ContainsInList({"asd", "^456", "ghj"}) - > false

```

***

#### **ToDouble**
```csharp
/// <summary>
/// "0,13".ToDouble() -> 0.13
/// "0,13".ToDouble(3) -> 0.130
/// </summary>
/// <param name="cdblString"></param>
/// <param name="Count"></param>
/// <returns></returns>
public static double ToDouble(this string cdblString, int Count = -1)

"123 456 789".ToDouble()         -> 123456789
"123 456 789.123456".ToDouble(2) -> 12346789.12

```

***

#### **ToDoubleStr**
```csharp
/// <summary>
/// "0,13".ToDoubleStr() -> "0.13"
/// "0,13".ToDoubleStr("#.###") -> "0.130"
/// </summary>
/// <param name="cdblString"></param>
/// <param name="StringFormat"></param>
/// <returns></returns>
public static string ToDoubleStr(this string cdblString, string StringFormat = "*")

"123 456 789".ToDoubleStr()               -> "123456789"
"123 456 789.123456".ToDoubleStr("#.###") -> "123456789.123"

```

***

#### **ToDecimal**
```csharp
/// <summary>
/// "0,13".ToDecimal() -> 0.13
/// "0,13".ToDecimal(3) -> 0.130
/// </summary>
/// <param name="decString"></param>
/// <param name="Count"></param>
/// <returns></returns>
public static decimal ToDecimal(this string decString, int Count = -1)

"123 456 789".ToDecimal()         -> 123456789
"123 456 789.123456".ToDecimal(2) -> 12346789.12

```


***

#### **ToDecimalStr**
```csharp
/// <summary>
/// "0,13".ToDecimalStr() -> "0.13"
/// "0,13".ToDecimalStr("#.###") -> "0.130"
/// </summary>
/// <param name="decString"></param>
/// <param name="StringFormat"></param>
/// <returns></returns>
public static string ToDecimalStr(this string decString, string StringFormat = "*")

"123 456 789".ToDecimalStr()               -> "123456789"
"123 456 789.123456".ToDecimalStr("#.###") -> "123456789.123"

```


***

#### **GetSimilarity**
```csharp
/// <summary>
/// "hello, world".GetSimilarity("hello,men") -> 0.58 is percent accuracy
/// </summary>
/// <param name="toSearch"></param>
/// <param name="toFind"></param>
/// <returns></returns>
public static Single GetSimilarity(this string toSearch, string toFind)

"123 456 789".GetSimilarity("123456 789") -> 0.9090909 - 91% accuracy
"123 456 789".GetSimilarity("123456789")  -> 0.8181818 - 82% accuracy

```

***

#### **DictToString**
```csharp
/// <summary>
/// dict.DictToString() -> {"4"="a","5"="b"}
/// </summary>
/// <typeparam name="TKey"></typeparam>
/// <typeparam name="TValue"></typeparam>
/// <param name="dictionary"></param>
/// <returns></returns>
/// <exception cref="ArgumentNullException"></exception>
public static string DictToString<TKey, TValue>(this IDictionary<TKey, TValue> dictionary)

(new Dictionary<string, object>() {{"a","1"}, {"b", 1}}).DictToString ->  "{\"a\"=\"1\",\"b\"=\"1\"}"

```


***

#### **DictToJson**
```csharp
/// <summary>
/// dict.DictToJson() -> {4:"a", 5:"b"}
/// </summary>
/// <typeparam name="TKey"></typeparam>
/// <typeparam name="TValue"></typeparam>
/// <param name="dictionary"></param>
/// <returns></returns>
/// <exception cref="ArgumentNullException"></exception>
public static JObject DictToJson<TKey, TValue>(this IDictionary<TKey, TValue> dictionary)

(new Dictionary<string, object>() {{"a","1"}, {"b", 1}}).DictToJson ->  {"a":"1","b"=1}

```


***

#### **DateParse**
```csharp
/// <summary>
/// "10.07.2022".DateParse() -> 07/10/2022 00:00:00
/// </summary>
/// <param name="date"></param>
/// <param name="listFormat"></param>
/// <returns></returns>
public static DateTime DateParse(this string date, string[] listFormat = null)

"10.07.2022".DateParse()                                     -> 07/10/2022 00:00:00
"7/10/22".DateParse({"M/dd/yy", "dd.MM.yyyy", "MM/dd/yyyy"}) -> 07/10/2022 00:00:00
```

***

#### **Capitalize**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="s"></param>
/// <returns></returns>
public static string Capitalize(this string s)

"this text".Capitalize() -> "This text"
```

***


## [*class* **DataExtended**](#DataExtended)

***

#### **ReadCSV**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="FilePath"></param>
/// <param name="DelimiterType"></param>
/// <param name="Encoding"></param>
/// <param name="HasHeaders"></param>
/// <param name="IgnoreQuotes"></param>
/// <returns></returns>
/// <exception cref="ArgumentException"></exception>
public static DataTable ReadCSV(string FilePath, Delimiter Delimiter = Delimiter.Semicolon, string Encoding = "", bool HasHeaders = false, bool IgnoreQuotes = false)
   
sFileName = "C:\Temp\test.csv";

dt = ReadCSV(sFileName);

-> dt as DataTable

```

***

#### **WriteCSV**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="FilePath"></param>
/// <param name="data"></param>
/// <param name="DelimiterType"></param>
/// <param name="Encoding"></param>
/// <param name="HasHeaders"></param>
/// <returns></returns>
public static bool WriteCSV(string FilePath, DataTable data, Delimiter DelimiterType = Delimiter.Semicolon, string Encoding = "", bool HasHeaders = false)

sFileName = "C:\Temp\test.csv";

WriteCSV(sFileName);

-> file csv

```


***

#### **AppendCSV**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="FilePath"></param>
/// <param name="data"></param>
/// <param name="DelimiterType"></param>
/// <param name="Encoding"></param>
/// <returns></returns>
public static bool AppendCSV(string FilePath, DataTable data, Delimiter DelimiterType = Delimiter.Semicolon, string Encoding = "")

sFileName = "C:\Temp\test.csv";

AppendCSV(sFileName);

-> file csv

```

-----------------

## [*class* **ProcessExtended**](#ProcessExtended)

***

#### **GetPid**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="processname"></param>
/// <param name="title"></param>
/// <param name="handle"></param>
/// <returns></returns>
public static int GetPid(this string processname, string title = "", IntPtr? handle = null)
   
iPID = "notepad".GetPid()
-> 12456

iPID = "notepad".GetPid("unti*")
-> 12456

iPID = "notepad".GetPid("", 78451689)
-> 12456

```

***

#### **Kill**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="processname"></param>
/// <param name="title"></param>
/// <param name="pid"></param>
/// <returns></returns>
/// <exception cref="ApplicationException"></exception>
public static bool Kill(this string processname, string title = "", int pid = -1)
   
"notepad".Kill()
-> true

"notepad".Kill("untit*")
-> true

"notepad".Kill("", 12456)
-> true

```

***


#### **GetWinHandle**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="processname"></param>
/// <param name="title"></param>
/// <returns></returns>
public static IntPtr GetWinHandle(this string processname, string title = "")
   
hwnd = "notepad".GetWinHandle()
-> 78451689

hwnd = "notepad".GetWinHandle("untit*")
-> 78451689

```

***

#### **GetMainWinHandle**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="processname"></param>
/// <param name="title"></param>
/// <returns></returns>
public static IntPtr GetMainWinHandle(this string processname, string title = "")
   
hwnd = "notepad".GetMainWinHandle()
-> 78451689

hwnd = "notepad".GetMainWinHandle("untit*")
-> 78451689

```

***


#### **GetWinTitle**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="processname"></param>
/// <param name="pid"></param>
/// <returns></returns>
public static string GetWinTitle(this string processname, int pid = -1)
   
sTitle = "notepad".GetWinTitle()
-> "Untitled - Notepad"

sTitle = "notepad".GetWinTitle(12456)
-> "Untitled - Notepad"

```

***

#### **GetProcess**
```csharp
/// <summary>
/// 
/// </summary>
/// <param name="processname"></param>
/// <param name="title"></param>
/// <param name="pid"></param>
/// <returns></returns>
public static Process GetProcess(this string processname, string title = "", int pid = -1)
   
sTitle = "notepad".GetProcess()
-> Process <Notepad.exe, "Untitled - Notepad">

sTitle = "notepad".GetProcess("untitl*")
-> Process <Notepad.exe, "Untitled - Notepad">

sTitle = "notepad".GetProcess("", 12456)
-> Process <Notepad.exe, "Untitled - Notepad">

```

***
