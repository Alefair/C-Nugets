# Alefair.Extended.Methods


```
Extended Methods powered by Alefair
```

>Current version **[1.0.4](https://github.com/Alefair/C-Nugets/blob/main/Alefair.Extended.Methods/Packages/Alefair.Extended.Methods.1.0.4.nupkg)**
>

>[nuget](https://www.nuget.org/packages/Alefair.Extended.Methods/1.0.4) on https://www.nuget.org


## [*class* **StringExtended**](#StringExtended)

### Methods:

- [Like](#Like)
- [ContainsInList](#ContainsInList)


- [ToDouble](#ToDouble)
- [ToDoubleStr](#ToDoubleStr)


- [ToDecimal](#ToDecimal)
- [ToDecimalStr](#ToDecimalStr)


- [GetSimilarity](#GetSimilarity)


- [DictToString](#DictToString)
- [DictToJson](#DictToJson)


- [DateParse](#DateParse)

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

<br><br>

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

<br><br>

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

<br><br>

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

<br><br>

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


<br><br>

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


<br><br>

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

<br><br>

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


<br><br>

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


<br><br>

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

<br><br>

-----------------

## [*class* **DataExtended**](#DataExtended)

### Methods:

- [ReadCSV](#ReadCSV)
- [WriteCSV](#WriteCSV)
- [AppendCSV](#AppendCSV)


<br><br>

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
public static DataTable ReadCSV(string FilePath, Delimeter DelimiterType = Delimeter.Semicolon, string Encoding = "", bool HasHeaders = false, bool IgnoreQuotes = false)
   
sFileName = "C:\Temp\test.csv";

dt = ReadCSV(sFileName);

-> dt as DataTable

```

<br><br>

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
public static bool WriteCSV(string FilePath, DataTable data, Delimeter DelimiterType = Delimeter.Semicolon, string Encoding = "", bool HasHeaders = false)

sFileName = "C:\Temp\test.csv";

WriteCSV(sFileName);

-> file csv

```


<br><br>

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
public static bool AppendCSV(string FilePath, DataTable data, Delimeter DelimiterType = Delimeter.Semicolon, string Encoding = "")

sFileName = "C:\Temp\test.csv";

AppendCSV(sFileName);

-> file csv

```
