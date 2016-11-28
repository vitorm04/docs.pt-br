---
title: Formatando tipos
description: Formatando tipos
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: cf497639-9f91-45cb-836f-998d1cea2f43
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 2dc4d1deff8d1b72cbe433c45dda873e9caa26fb

---

# <a name="formatting-types"></a>Formatando tipos

Formatação é o processo de conversão de uma instância de classe, estrutura ou valor de enumeração em sua representação de cadeia de caracteres, de forma que a cadeia de caracteres resultante possa ser exibida aos usuários ou desserializada para restaurar o tipo de dados original. Essa conversão pode apresentar uma série de desafios:

* A maneira que os valores são armazenados internamente não necessariamente reflete a maneira que os usuários desejam exibi-los. Por exemplo, um número de telefone pode ser armazenado no formato **8009999999**, que não é amigável. Em vez disso, ele deve ser exibido como **800-999-9999**. Veja a seção [Cadeias de caracteres de formato personalizado](#custom-format-strings) para obter um exemplo que formata um número dessa maneira. 

* Às vezes, a conversão de um objeto para sua representação de cadeia de caracteres não é intuitiva. Por exemplo, não é claro o modo como a representação de cadeia de caracteres de um objeto de **Temperatura** ou um objeto de **Pessoa** deve aparecer. Para obter um exemplo que formata um objeto **Temperatura** de diversas maneiras, veja a seção [Cadeias de caracteres de formato padrão](#standard-format-strings).

* Muitas vezes, os valores exigem formatação que leva em conta a cultura. Por exemplo, em um aplicativo que usa números para refletir os valores monetários, cadeias de caracteres numéricas devem incluir o símbolo da moeda da cultura atual, o separador de grupo (que, na maioria das culturas, é o separador de milhar) e o símbolo decimal. Para ver um exemplo, consulte a seção [Formatação que leva em conta a cultura com provedores de formato e a interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface). 

* Um aplicativo pode ter que exibir o mesmo valor de maneiras diferentes. Por exemplo, um aplicativo pode representar um membro de enumeração ao exibindo uma representação de cadeia de caracteres de seu nome ou exibindo seu valor subjacente. Para obter um exemplo que formata um membro da enumeração [DayOfWeek](xref:System.DayOfWeek) de maneiras diferentes, veja a seção [Cadeias de caracteres de formato padrão](#standard-format-strings).

O .NET dá suporte à formatação avançada, que permite aos desenvolvedores atender a esses requisitos. 

> [!NOTE]
> A formatação converte o valor de um tipo em uma representação de cadeia de caracteres. A análise é o inverso da formatação. Uma operação de análise cria uma instância de um tipo de dados com base em na representação de sua cadeia de caracteres. Para obter informações sobre como converter cadeias de caracteres em outros tipos de dados, veja [Analisando cadeias de caracteres](parsing-strings.md).

Esta visão geral contém as seguintes seções:

* [Formatação em .NET](#formatting-in-net)

* [Formatação padrão usando o método ToString](#default-formatting-using-the-tostring-method)

* [Substituindo o método ToString](#overriding-the-tostring-method)

* [As cadeias de caractere de formato e do método ToString](#the-tostring-method-and-format-strings)

    * [Cadeias de caracteres de formato padrão](#standard-format-strings)
    
    * [Cadeias de caracteres de formato personalizado](#custom-format-strings)
    
    * [Cadeias de caracteres de formato e tipos do .NET](#format-strings-and-net-types)
    
* [Formatação que leva em conta a cultura com provedores de formato e a interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)

    * [Formatação de valores numéricos que leva em conta a cultura](#culture-sensitive-formatting-of-numeric-values)
    
    * [Formatação de valores de data e hora que leva em conta a cultura](#culture-sensitive-formatting-of-date-and-time-values)
    
* [A interface IFormattable](#the-iformattable-interface)

* [Formatação de composição](#composite-formatting)

* [Formatação personalizada com ICustomFormatter](#custom-formatting-with-icustomformatter)

* [Tópicos relacionados](#related-topics)

* [Referência](#reference)

## <a name="formatting-in-net"></a>Formatação em .NET

O mecanismo básico de formatação é a implementação padrão do método [Object.ToString](xref:System.Object.ToString), que é abordado na seção [Formatação padrão usando o método ToString](#default-formatting-using-the-tostring-method), mais adiante neste tópico. No entanto, o .NET oferece várias maneiras de modificar e estender o suporte à formatação padrão. Eles incluem o seguinte:

* A substituição do método [ToString](xref:System.Object.ToString) para definir uma representação de cadeia de caracteres personalizada do valor de um objeto. Para obter mais informações, veja a seção [Substituindo o método ToString](#overriding-the-tostring-method) mais adiante neste tópico.

* A definição dos especificadores de formato que permitem que a representação de cadeia de caracteres do valor de um objeto assuma várias formas. Por exemplo, o especificador de formato "X" na instrução a seguir converte um inteiro na representação de cadeia de caracteres de um valor hexadecimal.

  ```csharp
  int integerValue = 60312;
  Console.WriteLine(integerValue.ToString("X"));   // Displays EB98.
  ```

  ```vb
  Dim integerValue As Integer = 60312
  Console.WriteLine(integerValue.ToString("X"))   ' Displays EB98.
  ```
  
  Para obter mais informações sobre especificadores de formato, veja a seção [As cadeias de caractere de formato e do método ToString](#the-tostring-method-and-format-strings).
  
* O uso de provedores de formato para aproveitar as convenções de formatação de uma cultura específica. Por exemplo, a instrução a seguir exibe um valor de moeda usando as convenções de formatação da cultura en-US. 

  ```csharp
  double cost = 1632.54; 
  Console.WriteLine(cost.ToString("C", 
                  new System.Globalization.CultureInfo("en-US")));   
  // The example displays the following output:
  //       $1,632.54
  ```

  ```vb
  Dim cost As Double = 1632.54
  Console.WriteLine(cost.ToString("C", New System.Globalization.CultureInfo("en-US")))
  ' The example displays the following output:
  '       $1,632.54
  ```
  
  Para obter mais informações sobre a formatação com provedores de formato, veja a seção [Formatação que leva em conta a cultura com provedores de formato e a interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface).  
  
* A implementação da interface [IFormattable](xref:System.IFormattable) para dar suporte tanto à conversão de cadeia de caracteres com a classe [Convert](xref:System.Convert) quanto à formatação de composição. Para obter mais informações, veja a seção [A interface IFormattable](#the-iformattable-interface).

* O uso da formatação de composição para inserir a representação de cadeia de caracteres de um valor em uma cadeia de caracteres maior. Para obter mais informações, veja a seção [Formatação de composição](#composite-formatting).

* A implementação de [ICustomFormatter](xref:System.ICustomFormatter) e [IFormatProvider](xref:System.IFormatProvider) para fornecer uma solução completa de formatação personalizada. Para obter mais informações, veja a seção [Formatação personalizada com ICustomFormatter](#custom-formatting-with-icustomformatter).

As seções a seguir examinam esses métodos para converter um objeto em sua representação de cadeia de caracteres.

## <a name="default-formatting-using-the-tostring-method"></a>Formatação padrão usando o método ToString

Cada tipo é derivado de [System.Object](xref:System.Object) herda automaticamente um método [ToString](xref:System.Object.ToString) sem parâmetros, que retorna o nome do tipo por padrão. O exemplo a seguir ilustra o método [ToString](xref:System.Object.ToString) padrão. Ele define uma classe chamada `Automobile` que não tem nenhuma implementação. Quando a classe é instanciada e seu método [ToString](xref:System.Object.ToString) é chamado, ele exibe seu nome de tipo. Observe que o método [ToString](xref:System.Object.ToString) não é chamado explicitamente no exemplo. O método [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) chama implicitamente o método [ToString](xref:System.Object.ToString) do objeto é passado para ele como um argumento. 

```csharp
using System;

public class Automobile
{
   // No implementation. All members are inherited from Object.
}

public class Example
{
   public static void Main()
   {
      Automobile firstAuto = new Automobile();
      Console.WriteLine(firstAuto);
   }
}
// The example displays the following output:
//       Automobile
```

```vb 
Public Class Automobile
   ' No implementation. All members are inherited from Object.
End Class

Module Example
   Public Sub Main()
      Dim firstAuto As New Automobile()
      Console.WriteLine(firstAuto)
   End Sub
End Module
' The example displays the following output:
'       Automobile
```

Já que todos os tipos, com a exceção das interfaces, são derivados de [Object](xref:System.Object), essa funcionalidade é fornecida automaticamente para suas estruturas ou classes personalizadas. No entanto, a funcionalidade oferecida pelo método [ToString](xref:System.Object.ToString) padrão é limitada: embora ele identifique o tipo, não fornece nenhuma informação sobre uma instância do tipo. Para fornecer uma representação de cadeia de caracteres de um objeto que fornece informações sobre o objeto, você deve substituir o método [ToString](xref:System.Object.ToString).

> [!NOTE]
> Estruturas herdam de [ValueType](xref:System.ValueType), que por sua vez é derivado de [Object](xref:System.Object). Embora [ValueType](xref:System.ValueType) substitua [Object.ToString](xref:System.Object.ToString), sua implementação é idêntica.

## <a name="overriding-the-tostring-method"></a>Substituindo o método ToString

A exibição do nome de um tipo é geralmente de uso limitado e não permite que os consumidores dos seus tipos diferenciem uma instância da outra. No entanto, você pode substituir o método [ToString](xref:System.Object.ToString) para fornecer uma representação mais útil do valor de um objeto. O exemplo a seguir define um objeto `Temperature` e substitui seu método [ToString](xref:System.Object.ToString) para exibir a temperatura em graus Celsius.

```csharp
using System;

public class Temperature
{
   private decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;   
   }

   public override string ToString()
   {
      return this.temp.ToString("N1") + "°C";
   }
}

public class Example
{
   public static void Main()
   {
      Temperature currentTemperature = new Temperature(23.6m);
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString());
   }
}
// The example displays the following output:
//       The current temperature is 23.6°C.
```

```vb
Public Class Temperature
   Private temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Overrides Function ToString() As String
      Return Me.temp.ToString("N1") + "°C"   
   End Function
End Class

Module Example
   Public Sub Main()
      Dim currentTemperature As New Temperature(23.6d)
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString())
   End Sub
End Module
' The example displays the following output:
'       The current temperature is 23.6°C.
```

No .NET, o método [ToString](xref:System.Object.ToString) de cada tipo de valor primitivo foi substituído para exibir o valor do objeto, em vez de seu nome. A tabela a seguir mostra a substituição de cada tipo primitivo. Observe que a maioria dos métodos substituídos chama outra sobrecarga do método [ToString](xref:System.Object.ToString) e passa-a ao especificador de formato "G" que define o formato geral de seu tipo, além de um objeto [IFormatProvider](xref:System.IFormatProvider) que representa a cultura atual.

Tipo | Substituição de ToString
---- | -----------------
[Booliano](xref:System.Boolean) | Retorna um [Boolean.TrueString](xref:System.Boolean.TrueString) ou [Boolean.FalseString](xref:System.Boolean.FalseString).
[Byte](xref:System.Byte) | Chama `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Byte](xref:System.Byte) para a cultura atual.
[Char](xref:System.Char) | Retorna o caractere como uma cadeia de caracteres.
[DateTime](xref:System.DateTime) | Chama `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` para formatar o valor de data e hora para a cultura atual. 
[Decimal](xref:System.Decimal) | Chama `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Decimal](xref:System.Decimal) para a cultura atual.
[Duplo](xref:System.Double) | Chama `Double.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Double](xref:System.Double) para a cultura atual.
[Int16](xref:System.Int16) | Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Int16](xref:System.Int16) para a cultura atual.
[Int32](xref:System.Int32) | Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Int32](xref:System.Int32) para a cultura atual.
[Int64](xref:System.Int64) | Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Int64](xref:System.Int64) para a cultura atual.
[SByte](xref:System.SByte) | Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [SByte](xref:System.SByte) | para a cultura atual.
[Simples](xref:System.Single) | Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Single](xref:System.Single) para a cultura atual.
[UInt32](xref:System.UInt32) | Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [UInt32](xref:System.UInt32) para a cultura atual.
[UInt32](xref:System.UInt32) | Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [UInt32](xref:System.UInt32) para a cultura atual.
[UInt64](xref:System.UInt64) | Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [UInt64](xref:System.UInt64) para a cultura atual.

## <a name="the-tostring-method-and-format-strings"></a>As cadeias de caractere de formato e do método ToString

Contar com o método padrão [ToString](xref:System.Object.ToString) ou substituir [ToString](xref:System.Object.ToString) é apropriado quando um objeto tem uma única representação de cadeia de caracteres. No entanto, o valor de um objeto normalmente tem várias representações. Por exemplo, uma temperatura pode ser expressa em graus Fahrenheit, graus Celsius ou kelvins. De forma similar, o valor de inteiro 10 pode ser representado de várias maneiras, incluindo 10, 10,0, 1.0e01 ou US $10,00.

Para permitir que um único valor tenha várias representações de cadeia de caracteres, o .NET usa cadeias de caracteres de formato. Uma cadeia de caracteres de formato é uma cadeia de caracteres que contém um ou mais especificadores de formato predefinidos, que são caracteres únicos ou grupos de caracteres que definem como o método [ToString](xref:System.Object.ToString) deve formatar sua saída. A cadeia de caracteres de formato é passada como um parâmetro para o método [ToString](xref:System.Object.ToString) do objeto e determina como a representação de cadeia de caracteres do valor do objeto deve ser exibida.

Todos os tipos numéricos, de data e hora e tipos de enumeração no .NET dão suporte a um conjunto predefinido de especificadores de formato. Você também pode usar cadeias de caracteres de formato para definir várias representações de cadeia de caracteres de seus tipos de dados definidos pelo aplicativo.

### <a name="standard-format-strings"></a>Cadeias de caracteres de formato padrão

Uma cadeia de caracteres de formato padrão contém um único especificador de formato, que é um caractere alfabético que define a representação de cadeia de caracteres do objeto ao qual ela é aplicada, junto com um especificador de precisão opcional que afeta a quantos dígitos serão exibidos na cadeia de caracteres de resultado. Se o especificador de precisão for omitido ou não houver suporte a ele, um especificador de formato padrão será equivalente a uma cadeia de caracteres de formato padrão. 

O .NET define um conjunto de especificadores de formato padrão para todos os tipos numéricos, todos os tipos de data e hora e todos os tipos de enumeração. Por exemplo, cada uma dessas categorias dá suporte a um especificador de formato padrão "G", que define uma representação de cadeia de caracteres geral de um valor desse mesmo tipo.

Cadeias de caracteres de formato padrão para tipos de enumeração controlam diretamente a representação de cadeia de caracteres de um valor. As cadeias de caracteres de formato passadas para o método [ToString](xref:System.Object.ToString) de um valor de enumeração determinam se o valor é exibido usando seu nome de cadeia de caracteres (especificadores de formato "G" e "F"), seu valor integral subjacente (o especificador de formato "D") ou seu valor hexadecimal (o especificador de formato "X"). O exemplo a seguir ilustra o uso de cadeias de caracteres de formato padrão para formatar um valor de enumeração [DayOfWeek](xref:System.DayOfWeek). 

```csharp
DayOfWeek thisDay = DayOfWeek.Monday;
string[] formatStrings = {"G", "F", "D", "X"};

foreach (string formatString in formatStrings)
   Console.WriteLine(thisDay.ToString(formatString));
// The example displays the following output:
//       Monday
//       Monday
//       1
//       00000001
```

```vb
Dim thisDay As DayOfWeek = DayOfWeek.Monday
Dim formatStrings() As String = {"G", "F", "D", "X"}

For Each formatString As String In formatStrings
   Console.WriteLine(thisDay.ToString(formatString))
Next
' The example displays the following output:
'       Monday
'       Monday
'       1
'       00000001
```

Para obter informações sobre cadeias de caracteres de formato de enumeração, veja [Cadeias de caracteres de formato de enumeração](enumeration-format.md).

Cadeias de caracteres de formato padrão para tipos numéricos geralmente definem uma cadeia de caracteres de resultado cuja aparência exata é controlada por um ou mais valores de propriedade. Por exemplo, o especificador de formato "C" formata um número como um valor de moeda. Quando você chama o método [ToString](xref:System.Object.ToString) com o especificador de formato "C" como o único parâmetro, os seguintes valores de propriedade do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) da cultura atual são usados para definir a representação de cadeia de caracteres do valor numérico:

* A propriedade [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol), que especifica o símbolo da moeda da cultura atual.

* A propriedade [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) ou [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern), que retorna um inteiro que determina o seguinte: 

    * O posicionamento do símbolo da moeda.
    
    * Se valores negativos são indicados por um sinal de negativo à esquerda, um sinal de negativo à direita ou parênteses.
    
    * Se um espaço é ou não exibido entre o valor numérico e o símbolo da moeda.
    
* A propriedade [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits), que define o número de dígitos fracionários na cadeia de caracteres de resultado.

* A propriedade [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator), que define o símbolo do separador decimal na cadeia de caracteres de resultado.

* A propriedade [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator), que define o símbolo de separador de grupo.

* A propriedade [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes), que define o número de dígitos em cada grupo à esquerda da vírgula decimal.

* A propriedade [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign), que determinará o sinal de negativo usado na cadeia de caracteres de resultado se parênteses não forem usados para indicar valores negativos.

Além disso, cadeias de caracteres de formato numérico podem incluir um especificador de precisão. O significado desse especificador depende da cadeia de caracteres de formato com o qual ele é usado, mas ele normalmente indica o número total de dígitos ou o número de dígitos fracionários que devem aparecer na cadeia de caracteres de resultado. Por exemplo, o exemplo a seguir usa a cadeia de caracteres numérica padrão "X4" e um especificador de precisão para criar um valor de cadeia de caracteres com quatro dígitos hexadecimais.

```csharp
byte[] byteValues = { 12, 163, 255 };
foreach (byte byteValue in byteValues)
   Console.WriteLine(byteValue.ToString("X4"));
// The example displays the following output:
//       000C
//       00A3
//       00FF
```

```vb
Dim byteValues() As Byte = { 12, 163, 255 }
For Each byteValue As Byte In byteValues
   Console.WriteLine(byteValue.ToString("X4"))
Next
' The example displays the following output:
'       000C
'       00A3
'       00FF
```

Para obter mais informações sobre cadeias de caracteres de formatação numérica padrão, veja [Cadeias de caracteres de formato numérico padrão](standard-numeric.md). 

Cadeias de caracteres de formato padrão para valores de data e hora são aliases para cadeias de caracteres de formato personalizado armazenadas por uma determinada classe [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo). Por exemplo, chamar o método [ToString](xref:System.Object.ToString) de um valor de data e hora com o especificador de formato "D" exibe a data e hora por meio do uso da cadeia de caracteres de formato personalizado armazenada na propriedade [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) da cultura atual. (Para obter mais informações sobre cadeias de caracteres de formato personalizado, veja a seção [Cadeias de caracteres de formato personalizado](#custom-format-strings).) O exemplo a seguir ilustra essa relação.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      DateTime date1 = new DateTime(2017, 6, 30);
      Console.WriteLine("D Format Specifier:     {0:D}", date1);
      string longPattern = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern;
      Console.WriteLine("'{0}' custom format string:     {1}", 
                        longPattern, date1.ToString(longPattern));
   }
}
// The example displays the following output when run on a system whose
// current culture is en-US:
//    D Format Specifier:     Tuesday, June 30, 2017
//    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2017
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim date1 As Date = #6/30/2009#
      Console.WriteLine("D Format Specifier:     {0:D}", date1)
      Dim longPattern As String = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern
      Console.WriteLine("'{0}' custom format string:     {1}", _
                        longPattern, date1.ToString(longPattern))
   End Sub
End Module
' The example displays the following output when run on a system whose
' current culture is en-US:
'    D Format Specifier:     Tuesday, June 30, 2009
'    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2009
```

Para obter mais informações sobre o padrão de data e cadeias de caracteres de formato de hora, veja [Cadeias de caracteres de formato de data e hora padrão](standard-datetime.md).

Você também pode usar cadeias de caracteres de formato padrão para definir a representação de cadeia de caracteres de um objeto definido pelo aplicativo que é produzido pelo método `ToString(String)` do objeto. Você pode definir os especificadores de formato padrão específicos que dão suporte a seu objeto e você pode determinar se eles diferenciam ou não maiúsculas de minúsculas. A implementação do `ToString(String)` método deve dar suporte ao seguinte:

* Um especificador de formato "G" que representa um formato comum ou habitual do objeto. A sobrecarga sem parâmetros do método `ToString` de seu objeto deve chamar sua sobrecarga `ToString(String)` e passar cadeia de caracteres de formato padrão "G".

* Suporte para um especificador de formato que é igual a uma referência nula. Um especificador de formato igual a uma referência nula deve ser considerado equivalente ao especificador de formato "G".

Por exemplo, um `Temperature` classe interna pode armazenar a temperatura em graus Celsius e usar especificadores de formato para representar o valor do objeto `Temperature` em graus Fahrenheit, graus Celsius e kelvins. O exemplo a seguir fornece uma ilustração.

```csharp
using System;

public class Temperature
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round(((decimal) (this.m_Temp * 9 / 5 + 32)), 2); }
   }

   public override string ToString()
   {
      return this.ToString("C");
   }

   public string ToString(string format)
   {  
      // Handle null or empty string.
      if (String.IsNullOrEmpty(format)) format = "C";
      // Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant();      

      // Convert temperature to Fahrenheit and return string.
      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2") + " °F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2") + " K";
         // return temperature in Celsius.
         case "G":
         case "C":
            return this.Celsius.ToString("N2") + " °C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}

public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(0m);
      Console.WriteLine(temp1.ToString());
      Console.WriteLine(temp1.ToString("G"));
      Console.WriteLine(temp1.ToString("C"));
      Console.WriteLine(temp1.ToString("F"));
      Console.WriteLine(temp1.ToString("K"));

      Temperature temp2 = new Temperature(-40m);
      Console.WriteLine(temp2.ToString());
      Console.WriteLine(temp2.ToString("G"));
      Console.WriteLine(temp2.ToString("C"));
      Console.WriteLine(temp2.ToString("F"));
      Console.WriteLine(temp2.ToString("K"));

      Temperature temp3 = new Temperature(16m);
      Console.WriteLine(temp3.ToString());
      Console.WriteLine(temp3.ToString("G"));
      Console.WriteLine(temp3.ToString("C"));
      Console.WriteLine(temp3.ToString("F"));
      Console.WriteLine(temp3.ToString("K"));

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3));
   }
}
// The example displays the following output:
//       0.00 °C
//       0.00 °C
//       0.00 °C
//       32.00 °F
//       273.15 K
//       -40.00 °C
//       -40.00 °C
//       -40.00 °C
//       -40.00 °F
//       233.15 K
//       16.00 °C
//       16.00 °C
//       16.00 °C
//       60.80 °F
//       289.15 K
//       The temperature is now 16.00 °C.
```

```vb
Public Class Temperature
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("C")
   End Function

   Public Overloads Function ToString(format As String) As String  
      ' Handle null or empty string.
      If String.IsNullOrEmpty(format) Then format = "C"
      ' Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant()      

      Select Case format
         Case "F"
           ' Convert temperature to Fahrenheit and return string.
            Return Me.Fahrenheit.ToString("N2") & " °F"
         Case "K"
            ' Convert temperature to Kelvin and return string.
            Return Me.Kelvin.ToString("N2") & " K"
         Case "C", "G"
            ' Return temperature in Celsius.
            Return Me.Celsius.ToString("N2") & " °C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(0d)
      Console.WriteLine(temp1.ToString())
      Console.WriteLine(temp1.ToString("G"))
      Console.WriteLine(temp1.ToString("C"))
      Console.WriteLine(temp1.ToString("F"))
      Console.WriteLine(temp1.ToString("K"))

      Dim temp2 As New Temperature(-40d)
      Console.WriteLine(temp2.ToString())
      Console.WriteLine(temp2.ToString("G"))
      Console.WriteLine(temp2.ToString("C"))
      Console.WriteLine(temp2.ToString("F"))
      Console.WriteLine(temp2.ToString("K"))

      Dim temp3 As New Temperature(16d)
      Console.WriteLine(temp3.ToString())
      Console.WriteLine(temp3.ToString("G"))
      Console.WriteLine(temp3.ToString("C"))
      Console.WriteLine(temp3.ToString("F"))
      Console.WriteLine(temp3.ToString("K"))

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3))
   End Sub
End Module
' The example displays the following output:
'       0.00 °C
'       0.00 °C
'       0.00 °C
'       32.00 °F
'       273.15 K
'       -40.00 °C
'       -40.00 °C
'       -40.00 °C
'       -40.00 °F
'       233.15 K
'       16.00 °C
'       16.00 °C
'       16.00 °C
'       60.80 °F
'       289.15 K
'       The temperature is now 16.00 °C.
```

### <a name="custom-format-strings"></a>Cadeias de caracteres de formato personalizado

Além de cadeias de caracteres de formato padrão, o .NET define cadeias de caracteres de formato personalizado para valores numéricos e valores de data e hora. Uma cadeia de caracteres de formato personalizado consiste em um ou mais especificadores de formato personalizado que definem a representação de cadeia de caracteres de um valor. Por exemplo, a cadeia de caracteres de formato de data e hora personalizada "aaaa/mm/dd hh:mm:ss.ffff t zzz" converte uma data em sua representação de cadeia de caracteres no formato "2008/11/15 07:45:00.0000 P -08:00" para a cultura en-US. Da mesma forma, a cadeia de caracteres de formato personalizado "0000" converte o valor inteiro 12 em "0012". Para obter uma lista completa de cadeias de caracteres de formato personalizado, veja [Cadeias de caracteres de formato de data e hora personalizado](custom-datetime.md) e [Cadeias de caracteres de formato numérico personalizado](custom-numeric.md).

Se uma cadeia de caracteres de formato consiste em um único especificador de formato personalizado, o especificador de formato deve ser precedido pelo símbolo de porcentagem (%) para evitar confusão com um especificador de formato padrão. O exemplo a seguir usa o especificador de formato personalizado "M" para exibir um número de um ou dois dígitos do mês de uma data específica.

```csharp
DateTime date1 = new DateTime(2009, 9, 8);
Console.WriteLine(date1.ToString("%M"));       
// Displays 9
```

```vb
Dim date1 As Date = #09/08/2009#
Console.WriteLine(date1.ToString("%M"))      ' Displays 9
```

Muitas cadeias de caracteres de formato padrão para valores de data e hora são aliases para cadeias de caracteres de formato personalizado que são definidas pelas propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo). Cadeias de caracteres de formato personalizado também oferecem flexibilidade considerável no fornecimento de formação definida pelo aplicativo para valores numéricos ou valores de data e hora. Você pode definir suas próprias cadeias de caracteres de resultado personalizadas para valores numéricos e valores de data e hora combinando vários especificadores de formato personalizado em uma única cadeia de caracteres de formato personalizado. O exemplo a seguir define uma cadeia de caracteres de formato personalizado que exibe o dia da semana entre parênteses após o nome do mês, o dia e o ano.

```csharp
string customFormat = "MMMM dd, yyyy (dddd)";
DateTime date1 = new DateTime(2009, 8, 28);
Console.WriteLine(date1.ToString(customFormat));   
// The example displays the following output if run on a system
// whose language is English:
//       August 28, 2009 (Friday) 
```

```vb
Dim customFormat As String = "MMMM dd, yyyy (dddd)"
Dim date1 As Date = #8/28/2009#
Console.WriteLine(date1.ToString(customFormat))   
' The example displays the following output if run on a system
' whose language is English:
'       August 28, 2009 (Friday) 
```

O exemplo a seguir define uma cadeia de caracteres de formato personalizado que exibe um valor [Int64](xref:System.Int64) como um número de telefone de sete dígitos padrão dos EUA, junto com seu código de área. 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      long number = 8009999999;
      string fmt = "000-000-0000";
      Console.WriteLine(number.ToString(fmt));
   }
}
// The example displays the following output:
//        800-999-9999
```

```vb
Module Example
   Public Sub Main()
      Dim number As Long = 8009999999
      Dim fmt As String = "000-000-0000"
      Console.WriteLine(number.ToString(fmt))
   End Sub
End Module
' The example displays the following output:

' The example displays the following output:
'       800-999-9999
```

Embora as cadeias de caracteres de formato padrão geralmente tratem da maioria das necessidades de formatação para os tipos definidos pelo aplicativo, você também pode definir especificadores de formato personalizado para formatar seus tipos. 

### <a name="format-strings-and-net-types"></a>Cadeias de caracteres de formato e tipos do .NET

Todos os tipos numéricos (ou seja, os tipos [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64) e [BigInteger](xref:System.Numerics.BigInteger)), bem como [DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset), [TimeSpan](xref:System.TimeSpan), [Guid](xref:System.Guid) e todos os tipos de enumeração, dão suporte à formatação com cadeias de caracteres de formato. Para obter informações sobre as cadeias de caracteres de formato específicas às quais cada tipo dá suporte, veja os seguintes tópicos: 

Título | Definição
----- | ----------
[Cadeias de caracteres de formato numérico padrão](standard-numeric.md) | Descreve cadeias de caracteres de formato padrão que criam representações de cadeia de caracteres de valores numéricos frequentemente usadas. 
[Cadeias de caracteres de formato numérico personalizado](custom-numeric.md) | Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para valores numéricos.
[Cadeias de caracteres de formato de data e hora padrão](standard-datetime.md) | Descreve cadeias de caracteres de formato padrão que criam representações de cadeia de caracteres de valores [DateTime](xref:System.DateTime) frequentemente usadas.
[Cadeias de caracteres de formato de data e hora personalizado](custom-datetime.md) | Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para valores [DateTime](xref:System.DateTime).
[Cadeias de caracteres de formato TimeSpan padrão](standard-timespan.md) | Descreve cadeias de caracteres de formato padrão que criam representações de intervalos de tempo frequentemente usadas.
[Cadeias de caracteres de formato TimeSpan personalizado](custom-timespan.md) | Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para intervalos de tempo.
[Cadeias de caracteres de formato de enumeração](enumeration-format.md) | Descreve cadeias de caracteres de formato padrão que são usadas para criar representações de cadeia de caracteres de valores de enumeração.
[Guid.ToString(String)](xref:System.Guid.ToString(System.String)) | Descreve cadeias de caracteres de formato padrão para valores [Guid](xref:System.Guid).

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Formatação que leva em conta a cultura com provedores de formato e a interface IFormatProvider

Embora os especificadores de formato permitam personalizar a formatação de objetos, a produção de uma representação de cadeia de caracteres de objetos significativa geralmente requer informações de formatação adicionais. Por exemplo, formatar um número como um valor de moeda usando a cadeia de caracteres de formato padrão "C" ou então uma cadeia de caracteres de formato personalizado como "$ #,#.00" requer que, no mínimo, informações sobre o símbolo correto da moeda, o separador de grupo e o separador decimal estejam disponíveis para inclusão na cadeia de caracteres formatada. No .NET, essas informações de formatação adicionais são disponibilizadas por meio da interface [IFormatProvider](xref:System.IFormatProvider), que é fornecida como um parâmetro para um ou mais sobrecargas do método `ToString` de tipos numéricos e tipos de data e hora. Implementações [IFormatProvider](xref:System.IFormatProvider) são usadas em .NET para dar suporte à formatação de cultura específica. O exemplo a seguir ilustra como a representação de cadeia de caracteres de um objeto é alterado quando ele é formatado com três objetos [IFormatProvider](xref:System.IFormatProvider) que representam diferentes culturas.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      decimal value = 1603.42m;
      Console.WriteLine(value.ToString("C3", new CultureInfo("en-US")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("fr-FR")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("de-DE")));
   }
}
// The example displays the following output:
//       $1,603.420
//       1 603,420 €
//       1.603,420 €
```

```vb
Imports System.Globalization

Public Module Example
   Public Sub Main()
      Dim value As Decimal = 1603.42d
      Console.WriteLine(value.ToString("C3", New CultureInfo("en-US")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("fr-FR")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("de-DE")))
   End Sub
End Module
' The example displays the following output:
'       $1,603.420
'       1 603,420 €
'       1.603,420 €
```

A interface [IFormatProvider](xref:System.IFormatProvider) inclui um método, [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)), que tem um único parâmetro que especifica o tipo de objeto que fornece informações de formatação. Se o método puder fornecer um objeto desse tipo, ele retornará esse objeto. Caso contrário, ele retornará uma referência nula.

[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) é um método de retorno de chamada. Quando você chama uma sobrecarga de método `ToString` que inclui um parâmetro [IFormatProvider](xref:System.IFormatProvider), ele chama o método [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) desse objeto [IFormatProvider](xref:System.IFormatProvider). O método [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) é responsável por retornar um objeto que fornece as informações de formatação necessárias (conforme especificadas pelo seu parâmetro *formatType*) para o método `ToString`. 

Um número de métodos de conversão de cadeia de caracteres ou formatação inclui um parâmetro de tipo [IFormatProvider](xref:System.IFormatProvider), mas em muitos casos o valor do parâmetro é ignorado quando o método é chamado. A tabela a seguir lista alguns dos métodos de formatação que usam o parâmetro e o tipo do objeto [Type](xref:System.Type) que passam para o método [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)). 

Método | Tipo de parâmetro *formatType*
------ | ------------------------------
`ToString` método de tipos numéricos | [System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)
`ToString` método de tipos de data e hora | [System.Globalization.DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)
[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) | [System.ICustomFormatter](xref:System.ICustomFormatter)
[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) | [System.ICustomFormatter](xref:System.ICustomFormatter)

O .NET fornece três classes que implementam [IFormatProvider](xref:System.IFormatProvider): 

* [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), uma classe que fornece informações de formatação para valores de data e hora para uma cultura específica. Sua implementação [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retorna uma instância de si mesma.

* [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), uma classe que fornece informações de formatação numérica para uma cultura específica. Sua implementação [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retorna uma instância de si mesma.

* [CultureInfo](xref:System.Globalization.CultureInfo). Sua implementação [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) pode retornar um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) para fornecer informações de formatação numérica ou um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) para fornecer informações de formatação para valores de data e hora. 

Você também pode implementar seu próprio provedor de formato para substituir qualquer uma dessas classes. No entanto, se o seu método `GetFormat` de sua implementação precisar fornecer informações de formatação ao método `ToString`, ele deverá retornar um objeto do tipo listado na tabela anterior.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Formatação de valores numéricos que leva em conta a cultura

Por padrão, a formatação de valores numéricos leva em conta a cultura. Se você não especificar uma cultura quando chamar um método de formatação, as convenções de formatação da cultura do thread atual serão usadas. Isso é ilustrado no exemplo a seguir, que altera a cultura do thread atual quatro vezes e, em seguida, chama o método [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)). Em cada caso, a cadeia de caracteres de resultado reflete as convenções de formatação da cultura atual. Isso ocorre porque os métodos `ToString` e `ToString(String)` encapsulam chamadas para o método `ToString(String, IFormatProvider)` de cada tipo numérico. 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      Decimal value = 1043.17m;

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(value.ToString("C2"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       $1,043.17
//       
//       The current culture is fr-FR
//       1 043,17 €
//       
//       The current culture is es-MX
//       $1,043.17
//       
//       The current culture is de-DE
//       1.043,17 €
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim value As Decimal = 1043.17d 

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(value.ToString("C2"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       $1,043.17
'       
'       The current culture is fr-FR
'       1 043,17 €
'       
'       The current culture is es-MX
'       $1,043.17
'       
'       The current culture is de-DE
'       1.043,17 €
```

Você também pode formatar um valor numérico para uma cultura específica chamando uma sobrecarga `ToString` que tenha um parâmetro de *provedor* e passando-o a um dos dois elementos a seguir: 

* Um [CultureInfo](xref:System.Globalization.CultureInfo) objeto que representa a cultura cujas convenções de formatação devem ser usadas. Seu método [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retorna o valor da propriedade [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat), que é o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que fornece informações de formatação específicas da cultura para valores numéricos.

* Um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que define as convenções de formatação específicas da cultura a ser usada. Seu método [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) retorna uma instância de si mesmo.

O exemplo a seguir usa objetos [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que representam as culturas inglês (Estados Unidos) e inglês (Grã-Bretanha), além das culturas neutras francês e russo, para formatar um número de ponto flutuante.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      Double value = 1043.62957;
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         NumberFormatInfo nfi = CultureInfo.CreateSpecificCulture(name).NumberFormat;
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 1,043.630
//       en-GB: 1,043.630
//       ru:    1 043,630
//       fr:    1 043,630
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As Double = 1043.62957
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim nfi As NumberFormatInfo = CultureInfo.CreateSpecificCulture(name).NumberFormat
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 1,043.630
'       en-GB: 1,043.630
'       ru:    1 043,630
'       fr:    1 043,630
```

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Formatação de valores de data e hora que leva em conta a cultura

Por padrão, a formatação de valores de data e hora leva em conta a cultura. Se você não especificar uma cultura quando chamar um método de formatação, as convenções de formatação da cultura do thread atual serão usadas. Isso é ilustrado no exemplo a seguir, que altera a cultura do thread atual quatro vezes e, em seguida, chama o método [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)). Em cada caso, a cadeia de caracteres de resultado reflete as convenções de formatação da cultura atual. Isso ocorre porque os métodos [DateTime.ToString()](xref:System.DateTime.ToString), [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)), [DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)) e [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) encapsulam chamadas para os métodos [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) e [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)).

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      DateTime dateToFormat = new DateTime(2012, 5, 28, 11, 30, 0);

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(dateToFormat.ToString("F"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       Monday, May 28, 2012 11:30:00 AM
//       
//       The current culture is fr-FR
//       lundi 28 mai 2012 11:30:00
//       
//       The current culture is es-MX
//       lunes, 28 de mayo de 2012 11:30:00 a.m.
//       
//       The current culture is de-DE
//       Montag, 28. Mai 2012 11:30:00
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim dateToFormat As Date = #5/28/2012 11:30AM#

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(dateToFormat.ToString("F"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       Monday, May 28, 2012 11:30:00 AM
'       
'       The current culture is fr-FR
'       lundi 28 mai 2012 11:30:00
'       
'       The current culture is es-MX
'       lunes, 28 de mayo de 2012 11:30:00 a.m.
'       
'       The current culture is de-DE
'       Montag, 28. Mai 2012 11:30:00
```

Você também pode formatar um valor de data e hora para uma cultura específica chamando uma sobrecarga [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) ou [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) que tenha um parâmetro de provedor e passando-o a um dos dois elementos a seguir: 

* Um [CultureInfo](xref:System.Globalization.CultureInfo) objeto que representa a cultura cujas convenções de formatação devem ser usadas. Seu método [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retorna o valor da propriedade [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat), que é o objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que fornece informações de formatação específicas da cultura para valores numéricos.

* Um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que define as convenções de formatação específicas da cultura a ser usada. Seu método [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) retorna uma instância de si mesmo.

O exemplo a seguir usa objetos [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que representam as culturas inglês (Estados Unidos) e inglês (Grã-Bretanha), além das culturas neutras francês e russo, para formatar uma data. 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      DateTime dat1 = new DateTime(2012, 5, 28, 11, 30, 0);
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         DateTimeFormatInfo dtfi = CultureInfo.CreateSpecificCulture(name).DateTimeFormat;
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 5/28/2012 11:30:00 AM
//       en-GB: 28/05/2012 11:30:00
//       ru: 28.05.2012 11:30:00
//       fr: 28/05/2012 11:30:00
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dat1 As Date = #5/28/2012 11:30AM#
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim dtfi As DateTimeFormatInfo = CultureInfo.CreateSpecificCulture(name).DateTimeFormat
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 5/28/2012 11:30:00 AM
'       en-GB: 28/05/2012 11:30:00
'       ru: 28.05.2012 11:30:00
'       fr: 28/05/2012 11:30:00
```

## <a name="the-iformattable-interface"></a>A interface IFormattable

Normalmente, os tipos que sobrecarregam o método `ToString` com uma cadeia de caracteres de formato e um parâmetro [IFormatProvider](xref:System.IFormatProvider) também implementam a interface [IFormattable](xref:System.IFormattable). Essa interface tem um único membro, [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)), que inclui como parâmetros uma cadeia de caracteres de formato e um provedor de formato.

Implementar a interface [IFormattable](xref:System.IFormattable) para a classe definida pelo aplicativo oferece duas vantagens: 

* Suporte para conversão de cadeia de caracteres pela classe [Convert](xref:System.Convert). Chamadas para os métodos [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) e [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) chamam sua implementação [IFormattable](xref:System.IFormattable) automaticamente.

* Suporte à formatação composição. Se um item de formato que inclui uma cadeia de caracteres de formato for usado para formatar seu tipo personalizado, o Common Language Runtime chamará automaticamente a implementação [IFormattable](xref:System.IFormattable) e passará a ele a cadeia de caracteres de formato. Para obter mais informações sobre formatação de composição com métodos como `String.Format` ou `Console.WriteLine`, veja a seção [Formatação de composição](#composite-formatting).

O exemplo a seguir define uma classe `Temperature` que implementa a interface [IFormattable](xref:System.IFormattable). Ela dá suporte aos especificadores de formato "C" ou "G" para exibir a temperatura em graus Celsius, o especificador de formato "F" para exibir a temperatura em Fahrenheit e o especificador de formato "K" para exibir a temperatura em Kelvin.

```csharp
using System;
using System.Globalization;

public class Temperature : IFormattable
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round((decimal) this.m_Temp * 9 / 5 + 32, 2); }
   }

   public override string ToString()
   {
      return this.ToString("G", null);
   }

   public string ToString(string format)
   {
      return this.ToString(format, null);
   }

   public string ToString(string format, IFormatProvider provider)  
   {
      // Handle null or empty arguments.
      if (String.IsNullOrEmpty(format)) format = "G";
      // Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant();

      if (provider == null) provider = NumberFormatInfo.CurrentInfo;

      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2", provider) + "°F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2", provider) + "K";
         // Return temperature in Celsius.
         case "C":
         case "G":
            return this.Celsius.ToString("N2", provider) + "°C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}
```

```vb
Imports System.Globalization

Public Class Temperature : Implements IFormattable
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("G", Nothing)
   End Function

   Public Overloads Function ToString(format As String) As String
      Return Me.ToString(format, Nothing)
   End Function

   Public Overloads Function ToString(format As String, provider As IFormatProvider) As String _  
      Implements IFormattable.ToString

      ' Handle null or empty arguments.
      If String.IsNullOrEmpty(format) Then format = "G"
      ' Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant()

      If provider Is Nothing Then provider = NumberFormatInfo.CurrentInfo

      Select Case format
         ' Convert temperature to Fahrenheit and return string.
         Case "F"
            Return Me.Fahrenheit.ToString("N2", provider) & "°F"
         ' Convert temperature to Kelvin and return string.
         Case "K"
            Return Me.Kelvin.ToString("N2", provider) & "K"
         ' Return temperature in Celsius.
         Case "C", "G"
            Return Me.Celsius.ToString("N2", provider) & "°C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class
```

O exemplo a seguir instancia um objeto `Temperature`. Depois, ele chama o método [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) e usa várias cadeias de caracteres de formato de composição para obter diferentes representações de um objeto `Temperature`. Cada uma dessas chamadas de método, por sua vez, chama a implementação [IFormattable](xref:System.IFormattable) da classe `Temperature`.

```csharp
public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(22m);
      Console.WriteLine(Convert.ToString(temp1, new CultureInfo("ja-JP")));
      Console.WriteLine("Temperature: {0:K}", temp1);
      Console.WriteLine("Temperature: {0:F}", temp1);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), "Temperature: {0:F}", temp1));
   }
}
// The example displays the following output:
//       22.00°C
//       Temperature: 295.15°K
//       Temperature: 71.60°F
//       Temperature: 71,60°F
```

```vb
Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(22d)
      Console.WriteLine(Convert.ToString(temp1, New CultureInfo("ja-JP")))
      Console.WriteLine("Temperature: {0:K}", temp1)
      Console.WriteLine("Temperature: {0:F}", temp1)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), "Temperature: {0:F}", temp1)) 
   End Sub
End Module
' The example displays the following output:
'       22.00°C
'       Temperature: 295.15°K
'       Temperature: 71.60°F
'       Temperature: 71,60°F
```

## <a name="composite-formatting"></a>Formatação de composição

Alguns métodos, tais como `String.Format` e `StringBuilder.AppendFormat`, dão suporte à formatação de composição. Uma cadeia de caracteres de formato de composição é um tipo de modelo que retorna uma única cadeia de caracteres que incorpora a representação de cadeia de caracteres de zero, um ou mais objetos. Cada objeto é representado na cadeia de caracteres de formato de composição por um item de formato indexado. O índice do item de formato corresponde à posição do objeto que ele representa na lista de parâmetros do método. Os índices são baseados em zero. Por exemplo, na seguinte chamada para o método `String.Format`, o primeiro item de formato, `{0:D}`, é substituído pela representação de cadeia de caracteres de `thatDate`; o segundo item de formato, `{1}`, é substituído pela representação de cadeia de caracteres de `item1` e, por fim, o terceiro item de formato, `{2:C2}`, é substituído pela representação de cadeia de caracteres de `item1.Value`.

```csharp
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", 
                       thatDate, item1, item1.Value);
Console.WriteLine(result);                            
// The example displays output like the following if run on a system
// whose current culture is en-US:
//       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

```vb
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", _
                       thatDate, item1, item1.Value)
Console.WriteLine(result)                            
' The example displays output like the following if run on a system
' whose current culture is en-US:
'       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

Além de substituir um item de formato pela representação de cadeia de caracteres de seu objeto correspondente, os itens de formato também permitem que você controle o seguinte: 

* O modo específico em que um objeto é representado como uma cadeia de caracteres, se o objeto implementa a interface [IFormattable](xref:System.IFormattable) e se dá suporte a cadeias de caracteres de formato. Você pode fazer isso seguindo o índice do item de formato com um : (dois-pontos) seguido por uma cadeia de caracteres de formato válido. O exemplo anterior já fez isso ao formatar um valor de data com a cadeia de caracteres de formato (por exemplo, `{0:d}`) "d" (padrão de data abreviada) e formatando um valor numérico com a cadeia de caracteres de formato "C2" (por exemplo, `{2:C2}`) para representar o número como um valor de moeda com dois dígitos decimais fracionários. 

* A largura do campo que contém a representação de cadeia de caracteres do objeto e o alinhamento da representação de cadeia de caracteres nesse campo. Você pode fazer isso seguindo o índice do item de formato com uma , (vírgula) seguida da largura do campo. A cadeia de caracteres será alinhada à direita no campo se a largura do campo for um valor positivo ou à esquerda se esse valor for negativo. O exemplo a seguir alinha os valores de data à esquerda em um campo de 20 caracteres e alinha valores decimais com um dígito fracionário à direita em um campo de 11 caracteres. 

```csharp
DateTime startDate = new DateTime(2015, 8, 28, 6, 0, 0);
decimal[] temps = { 73.452m, 68.98m, 72.6m, 69.24563m,
                   74.1m, 72.156m, 72.228m };
Console.WriteLine("{0,-20} {1,11}\n", "Date", "Temperature");
for (int ctr = 0; ctr < temps.Length; ctr++)
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps[ctr]);

// The example displays the following output:
//       Date                 Temperature
//
//       8/28/2015 6:00 AM           73.5
//       8/29/2015 6:00 AM           69.0
//       8/30/2015 6:00 AM           72.6
//       8/31/2015 6:00 AM           69.2
//       9/1/2015 6:00 AM            74.1
//       9/2/2015 6:00 AM            72.2
//       9/3/2015 6:00 AM            72.2
```

```vb
Dim startDate As New Date(2015, 8, 28, 6, 0, 0)
Dim temps() As Decimal = { 73.452, 68.98, 72.6, 69.24563,
                           74.1, 72.156, 72.228 }
Console.WriteLine("{0,-20} {1,11}", "Date", "Temperature")
Console.WriteLine()
For ctr As Integer = 0 To temps.Length - 1
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps(ctr))
Next
' The example displays the following output:
'       Date                 Temperature
'
'       8/28/2015 6:00 AM           73.5
'       8/29/2015 6:00 AM           69.0
'       8/30/2015 6:00 AM           72.6
'       8/31/2015 6:00 AM           69.2
'       9/1/2015 6:00 AM            74.1
'       9/2/2015 6:00 AM            72.2
'       9/3/2015 6:00 AM            72.2
```

Observe que, se o componente de cadeia de caracteres de alinhamento e o componente de cadeia de caracteres de formato estiverem presentes, o primeiro precederá o último (por exemplo, `{0,-20:g}`. 

Para obter mais informações sobre formatação de composição, veja [Formatação de composição](composite-format.md).

## <a name="custom-formatting-with-icustomformatter"></a>Formatação personalizada com ICustomFormatter

Dois métodos de formatação de composição, [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) e [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), incluem um parâmetro de provedor de formato que dá suporte à formatação personalizada. Quando um desses métodos de formatação é chamado, ele passa um objeto [Type](xref:System.Type) que representa uma interface [ICustomFormatter](xref:System.ICustomFormatter) para o método `GetFormat` do provedor de formato. O `GetFormat` em seguida, o método é responsável por retornar a implementação [ICustomFormatter](xref:System.ICustomFormatter) que oferece formatação personalizada.

A interface [ICustomFormatter](xref:System.ICustomFormatter) tem um único método, [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), que é chamado automaticamente por um método de formatação de composição, uma vez para cada item de formato em uma cadeia de caracteres de formato de composição. O método [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) tem três parâmetros: uma cadeia de caracteres de formato, que representa o argumento *formatString* em um item de formato, um objeto a ser formatado e um objeto [IFormatProvider](xref:System.IFormatProvider) que oferece serviços de formatação. Normalmente, a classe que implementa [ICustomFormatter](xref:System.ICustomFormatter) também implementa [IFormatProvider](xref:System.IFormatProvider), portanto, este último parâmetro é uma referência para a própria classe de formatação personalizada. O método retorna uma representação de cadeia de caracteres formatada personalizada do objeto a ser formatado. Se o método não for capaz de formatar o objeto, ele deverá retornar uma referência nula.

O exemplo a seguir fornece uma implementação [ICustomFormatter](xref:System.ICustomFormatter) chamada `ByteByByteFormatter` que exibe valores inteiros como uma sequência de valores hexadecimais de dois dígitos seguidos por um espaço.

```csharp
public class ByteByByteFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   { 
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }

   public string Format(string format, object arg, 
                          IFormatProvider formatProvider)
   {   
      if (! formatProvider.Equals(this)) return null;

      // Handle only hexadecimal format string.
      if (! format.StartsWith("X")) return null;

      byte[] bytes;
      string output = null;

      // Handle only integral types.
      if (arg is Byte) 
         bytes = BitConverter.GetBytes((Byte) arg);
      else if (arg is Int16)
         bytes = BitConverter.GetBytes((Int16) arg);
      else if (arg is Int32)
         bytes = BitConverter.GetBytes((Int32) arg);
      else if (arg is Int64)   
         bytes = BitConverter.GetBytes((Int64) arg);
      else if (arg is SByte)
         bytes = BitConverter.GetBytes((SByte) arg);
      else if (arg is UInt16)
         bytes = BitConverter.GetBytes((UInt16) arg);
      else if (arg is UInt32)
         bytes = BitConverter.GetBytes((UInt32) arg);
      else if (arg is UInt64)
         bytes = BitConverter.GetBytes((UInt64) arg);
      else
         return null;

      for (int ctr = bytes.Length - 1; ctr >= 0; ctr--)
         output += String.Format("{0:X2} ", bytes[ctr]);   

      return output.Trim();
   }
}
```

```vb
Public Class ByteByByteFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If
   End Function

   Public Function Format(fmt As String, arg As Object, 
                          formatProvider As IFormatProvider) As String _
                          Implements ICustomFormatter.Format

      If Not formatProvider.Equals(Me) Then Return Nothing

      ' Handle only hexadecimal format string.
      If Not fmt.StartsWith("X") Then 
            Return Nothing
      End If

      ' Handle only integral types.
      If Not typeof arg Is Byte AndAlso
         Not typeof arg Is Int16 AndAlso
         Not typeof arg Is Int32 AndAlso
         Not typeof arg Is Int64 AndAlso
         Not typeof arg Is SByte AndAlso
         Not typeof arg Is UInt16 AndAlso
         Not typeof arg Is UInt32 AndAlso
         Not typeof arg Is UInt64 Then _
            Return Nothing

      Dim bytes() As Byte = BitConverter.GetBytes(arg)
      Dim output As String = Nothing

      For ctr As Integer = bytes.Length - 1 To 0 Step -1
         output += String.Format("{0:X2} ", bytes(ctr))   
      Next

      Return output.Trim()
   End Function
End Class
```

O exemplo a seguir usa a classe `ByteByByteFormatter` para formatar valores inteiros. Observe que o método [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) é chamado mais de uma vez na segunda chamada do método [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) e que o provedor padrão [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) é usado na terceira chamada de método porque o método `.ByteByByteFormatter.Format` não reconhece a cadeia de caracteres de formato "N0" e retorna uma referência nula.

```csharp
public class Example
{
   public static void Main()
   {
      long value = 3210662321; 
      byte value1 = 214;
      byte value2 = 19;

      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X}", value));
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 & value2));                                
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0,10:N0}", value));
   }
}
// The example displays the following output:
//       00 00 00 00 BF 5E D1 B1
//       00 D6 And 00 13 = 00 12 (018)
//       3,210,662,321
```

```vb
Public Module Example
   Public Sub Main()
      Dim value As Long = 3210662321 
      Dim value1 As Byte = 214
      Dim value2 As Byte = 19

      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X}", value)))
      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 And value2)))                                
      Console.WriteLine(String.Format(New ByteByByteFormatter(), "{0,10:N0}", value))
   End Sub
End Module
' The example displays the following output:
'       00 00 00 00 BF 5E D1 B1
'       00 D6 And 00 13 = 00 12 (018)
'       3,210,662,321
```

## <a name="related-topics"></a>Tópicos relacionados

Título | Definição
----- | ----------
[Cadeias de caracteres de formato numérico padrão](standard-numeric.md) | Descreve cadeias de caracteres de formato padrão que criam representações de cadeia de caracteres de valores numéricos frequentemente usadas. 
[Cadeias de caracteres de formato numérico personalizado](custom-numeric.md) | Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para valores numéricos.
[Cadeias de caracteres de formato de data e hora padrão](standard-datetime.md) |  Descreve cadeias de caracteres de formato padrão que criam representações de cadeia de caracteres de valores [DateTime](xref:System.DateTime) frequentemente usadas.
[Cadeias de caracteres de formato de data e hora personalizado](custom-datetime.md) | Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para valores [DateTime](xref:System.DateTime).
[Cadeias de caracteres de formato TimeSpan padrão](standard-timespan.md) | Descreve cadeias de caracteres de formato padrão que criam representações de intervalos de tempo frequentemente usadas.
[Cadeias de caracteres de formato TimeSpan personalizado](custom-timespan.md) | Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para intervalos de tempo.
[Cadeias de caracteres de formato de enumeração](enumeration-format.md) | Descreve cadeias de caracteres de formato padrão que são usadas para criar representações de cadeia de caracteres de valores de enumeração.
[Formatação de composição](composite-format.md) | Descreve como inserir um ou mais valores formatados em uma cadeia de caracteres. A cadeia de caracteres pode posteriormente ser exibida no console ou gravada em um fluxo.
[Executando operações de formatação](performing-formatting-operations.md) | Lista os tópicos que fornecem instruções passo a passo para executar operações de formatação específicas.
[Analisando cadeias de caracteres](parsing-strings.md) | Descreve como inicializar objetos para os valores descritos pelas representações de cadeia de caracteres desses objetos. A análise é a operação inversa da formatação.

## <a name="reference"></a>Referência

[System.IFormattable](xref:System.IFormattable)

[System.IFormatProvider](xref:System.IFormatProvider)

[System.ICustomFormatter](xref:System.ICustomFormatter)



<!--HONumber=Nov16_HO4-->


