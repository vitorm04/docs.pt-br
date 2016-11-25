---
title: "Formatação de composição"
description: "Formatação de composição"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a01efc8f-c242-4535-bd32-acd0032d9590
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 15c549f5df0b6de8164e05f50855006996a47fac

---

# <a name="composite-formatting"></a>Formatação de composição

O recurso de formatação de composição do .NET utiliza uma lista de objetos e uma cadeia de caracteres de formato de composição como entrada. Uma cadeia de formato de composição consiste em um texto fixo intercalado com espaços reservados indexados, chamados de itens de formato, que correspondem aos objetos na lista. A operação de formatação produz uma cadeia de caracteres de resultado que consiste no texto fixo original intercalado com a representação de cadeia de caracteres dos objetos na lista. 

O recurso de formatação de composição tem suporte de métodos como: 

* [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)), que retorna uma cadeia de caracteres de resultado formatada. 

* [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider, System.String, System.Object), que acrescenta uma cadeia de caracteres de resultado formatada a um objeto [StringBuilder](xref:System.Text.StringBuilder).

* Algumas sobrecargas do método `WriteLine` do [Console](xref:System.Console),que exibem uma cadeia de caracteres de resultado formatada para o console.  

* Algumas sobrecargas do método `WriteLine` de [TextWriter](xref:System.IO.TextWriter), que gravam a cadeia de caracteres de resultado formatada em um fluxo ou arquivo. As classes derivadas de [TextWriter](xref:System.IO.TextWriter), como [StreamWriter](xref:System.IO.StreamWriter), também têm essa funcionalidade.

* [Debug.WriteLine(String, Object[])](xref:System.Diagnostics.Debug.WriteLine(System.String,System.Object[])), que gera uma mensagem formatada para ouvintes de rastreamento. 

* Os métodos [Trace.TraceError(String, Object[])](xref:System.Diagnostics.Trace.TraceError(System.String,System.Object[])), [Trace.TraceInformation(String, Object[])](xref:System.Diagnostics.Trace.TraceInformation(System.String,System.Object[])) e [Trace.TraceWarning(String, Object[])](xref:System.Diagnostics.Trace.TraceWarning(System.String,System.Object[])), que geram mensagens formatadas para ouvintes de rastreamento. 

* O método [TraceSource.TraceInformation(String, Object[])](xref:System.Diagnostics.TraceSource.TraceInformation(System.String,System.Object[])), que grava um método informativo para ouvintes de rastreamento. 

## <a name="composite-format-string"></a>Cadeia de formato de composição

Uma cadeia de formato de composição e uma lista de objetos são usadas como argumentos dos métodos que dão suporte ao recurso de formatação de composição. Uma cadeia de formato de composição consiste em zero ou mais sequências de texto fixo intercaladas com um ou mais itens de formato. O texto fixo é qualquer cadeia de caracteres que você escolher e cada item de formato corresponde a um objeto ou a uma estrutura demarcada na lista. O recurso de formatação de composição retorna uma nova cadeia de caracteres de resultado em que cada item de formato é substituído pela representação de cadeia de caracteres do objeto correspondente na lista.

Considere o seguinte fragmento de código [Format](xref:System.String.Format(System.String.Format(System.IFormatProvider,System.String,System.Object)).

```csharp
string name = "Fred";
String.Format("Name = {0}, hours = {1:hh}", name, DateTime.Now);
```

```vb
Dim name As String = "Fred"
String.Format("Name = {0}, hours = {1:hh}", name, DateTime.Now)
```

O texto fixo é `"Name = "` e `", hours = "`. Os itens de formato são `"{0}"`, cujo índice é 0, que corresponde ao objeto `name`, e `"{1:hh}"`, cujo índice é 1, que corresponde ao objeto `DateTime.Now`.

## <a name="format-item-syntax"></a>Sintaxe do item de formato

Cada item de formato assume a forma a seguir e consiste nos seguintes componentes:

__{__*index*[,*alignment*][:*formatString*]__}__

As chaves correspondentes ("{" e "}") são necessárias. 
 
### <a name="index-component"></a>Componente de índice

O componente obrigatório *index*, também chamado de especificador de parâmetro, é um número iniciado por 0 que identifica um item correspondente na lista de objetos. Ou seja, o item de formato cujo especificador de parâmetro é 0 formata o primeiro objeto na lista, o item de formato cujo especificador de parâmetro é 1 formata o segundo objeto na lista e assim por diante. O exemplo a seguir inclui quatro especificadores de parâmetros, numerados de zero a três, para representar números primos menores que dez: 

```csharp
string primes;
primes = String.Format("Prime numbers less than 10: {0}, {1}, {2}, {3}",
                       2, 3, 5, 7 );
Console.WriteLine(primes);
// The example displays the following output:
//      Prime numbers less than 10: 2, 3, 5, 7
```

```vb
Dim primes As String
primes = String.Format("Prime numbers less than 10: {0}, {1}, {2}, {3}",
                       2, 3, 5, 7 )
Console.WriteLine(primes)
' The example displays the following output:
'      Prime numbers less than 10: 2, 3, 5, 7
```

Vários itens de formato podem fazer referência ao mesmo elemento na lista de objetos ao especificar o mesmo especificador de parâmetro. Por exemplo, você pode formatar o mesmo valor numérico em formato hexadecimal, científico e numérico especificando uma cadeia de formato de composição como "0x{0:X} {0:E} {0:N}", conforme demonstrado no exemplo a seguir. 

```csharp
string multiple = String.Format("0x{0:X} {0:E} {0:N}",
                                Int64.MaxValue);
Console.WriteLine(multiple);
// The example displays the following output:
//      0x7FFFFFFFFFFFFFFF 9.223372E+018 9,223,372,036,854,775,807.00
```

```vb
Dim multiple As String = String.Format("0x{0:X} {0:E} {0:N}",
                                       Int64.MaxValue)
Console.WriteLine(multiple)
' The example displays the following output:
'      0x7FFFFFFFFFFFFFFF 9.223372E+018 9,223,372,036,854,775,807.00
```

Cada item de formato pode fazer referência a qualquer objeto na lista. Por exemplo, se houver três objetos, você poderá formatar o segundo, o primeiro e o terceiro objetos especificando uma cadeia de formato de composição como esta: "{1} {0} {2}". Um objeto que não é referenciado por um item de formato é ignorado. Uma [FormatException](xref:System.FormatException) será lançada no tempo de execução se um especificador de parâmetro designar um item fora dos limites da lista de objetos.

### <a name="alignment-component"></a>Componente de alinhamento

O componente opcional *alignment* é um inteiro com sinal que indica a largura preferencial do campo formatado. Se o valor de *alignment* for menor que o comprimento da cadeia de caracteres formatada, *alignment* será ignorado e o comprimento da cadeia de caracteres formatada será usado como a largura do campo. Os dados formatados no campo serão alinhados à direita se *alignment* for positivo e serão alinhados à esquerda se *alignment* for negativo. Se for necessário preenchimento, espaços em branco serão usados. A vírgula é necessária se *alignment* for especificado.

O exemplo a seguir define duas matrizes, uma contendo os nomes dos funcionários e outra contendo as horas trabalhadas por eles em um período de duas semanas. A cadeia de caracteres de formato de composição alinha à esquerda os nomes em um campo de 20 caracteres e alinha à direita as horas em um campo de 5 caracteres. Observe que a cadeia de caracteres de formato padrão "N1" também é usada para formatar horas com um dígito fracionário. 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string[] names = { "Adam", "Bridgette", "Carla", "Daniel",
                         "Ebenezer", "Francine", "George" };
      decimal[] hours = { 40, 6.667m, 40.39m, 82, 40.333m, 80,
                                 16.75m };

      Console.WriteLine("{0,-20} {1,5}\n", "Name", "Hours");
      for (int ctr = 0; ctr < names.Length; ctr++)
         Console.WriteLine("{0,-20} {1,5:N1}", names[ctr], hours[ctr]);

   }
}
// The example displays the following output:
//       Name                 Hours
//
//       Adam                  40.0
//       Bridgette              6.7
//       Carla                 40.4
//       Daniel                82.0
//       Ebenezer              40.3
//       Francine              80.0
//       George                16.8
```

```vb
Module Example
   Public Sub Main()
      Dim names() As String = { "Adam", "Bridgette", "Carla", "Daniel",
                                "Ebenezer", "Francine", "George" }
      Dim hours() As Decimal = { 40, 6.667d, 40.39d, 82, 40.333d, 80,
                                 16.75d }

      Console.WriteLine("{0,-20} {1,5}", "Name", "Hours")
      Console.WriteLine()
      For ctr As Integer = 0 To names.Length - 1
         Console.WriteLine("{0,-20} {1,5:N1}", names(ctr), hours(ctr))
      Next
   End Sub
End Module
' The example displays the following output:
'       Name                 Hours
'
'       Adam                  40.0
'       Bridgette              6.7
'       Carla                 40.4
'       Daniel                82.0
'       Ebenezer              40.3
'       Francine              80.0
'       George                16.8
```

### <a name="format-string-component"></a>Componente da cadeia de caracteres de formato

O componente opcional *formatString* é uma cadeia de caracteres de formato que é apropriada para o tipo de objeto que está sendo formatado. Especifique uma cadeia de caracteres de formato numérico padrão ou personalizado se o objeto correspondente for um valor numérico, uma cadeia de caracteres de formato de data e hora padrão ou personalizado se o objeto correspondente for um objeto [DateTime](xref:System.DateTime) ou uma [cadeia de caracteres de formato de enumeração](enumeration-format.md) se o objeto correspondente for um valor de enumeração. Se *formatString* não for especificado, o especificador de formato geral ("G") para um tipo numérico, de data e hora ou enumeração será usado. Os dois-pontos são necessários quando *formatString* é especificado.

A tabela a seguir lista tipos ou categorias de tipos na biblioteca de classes do .NET Framework que dão suporte a um conjunto predefinido de cadeias de caracteres de formato e fornece links para tópicos que relacionam as cadeias de caracteres de formato com suporte. Observe que a formatação de cadeias de caracteres é um mecanismo extensível que possibilita definir novas cadeias de caracteres de formato para todos os tipos existentes, bem como definir um conjunto de cadeias de caracteres de formato com suporte por um tipo definido por aplicativo. Para obter mais informações, consulte os tópicos de interface [IFormattable](xref:System.IFormattable) e [ICustomFormatter](xref:System.ICustomFormatter). 

Tipo ou categoria de tipo | Consulte
--------------------- | ---
Tipos de data e hora ([DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset)) | [Cadeias de Caracteres de Formato de Data e Hora Padrão](standard-datetime.md), [Cadeias de caracteres de formato de data e hora personalizados](custom-datetime.md)
Tipos de enumeração (todos os tipos derivados de [System.Enum](xref:System.Enum)) | [Cadeias de Caracteres de Formato de Enumeração](enumeration-format.md)
Tipos numéricos ([BigInteger](xref:System.Numerics.BigInteger), [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Duplo](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Simples](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64)) | [Cadeias de caracteres de formato numérico padrão](standard-numeric.md), [Cadeias de caracteres de formato numérico personalizado](custom-numeric.md)
[Guid](xref:System.Guid) | [Guid.ToString(String)](xref:System.Guid.ToString(System.String))
[TimeSpan](xref:System.TimeSpan) | [Cadeias de formato TimeSpan padrão](standard-timespan.md), [Cadeias de formato TimeSpan personalizadas](custom-timespan.md)

### <a name="escaping-braces"></a>Chaves de escape

As chaves de abertura e fechamento são interpretadas como o início e o fim de um item de formato. Consequentemente, você deve usar uma sequência de escape para exibir uma chave de abertura ou fechamento literal. Especifique duas chaves de abertura ("{{") no texto fixo para exibir uma chave de abertura ("{"), ou duas chaves de fechamento ("}}") para exibir uma chave de fechamento ("}"). As chaves em um item de formato são interpretadas sequencialmente na ordem em que são encontradas. Não há suporte para interpretação de chaves aninhadas. 

A forma como as chaves de escape são interpretadas pode levar a resultados inesperados. Por exemplo, considere o item de formato "{{{0:D}}}", que deve exibir uma chave de abertura, um valor numérico formatado como número decimal e uma chave de fechamento. No entanto, o item de formato na verdade é interpretado da seguinte forma: 

1. As duas primeiras chaves de abertura ("{{") são escapadas e produzem uma chave de abertura. 

2. Os três caracteres seguintes ("{0:") são interpretados como o início de um item de formato.

3. O caractere seguinte ("D") seria interpretado como o especificador de formato numérico Decimal padrão, mas as duas chaves de escape seguintes ("}} ") produzem uma única chave. Como a cadeia de caracteres resultante ("D}") não é um especificador de formato numérico padrão, ela é interpretada como uma cadeia de formato personalizado que visa exibir a cadeia de caracteres literal "D}". 

4. A última chave ("}") é interpretada como o final do item de formato. 

5. O resultado final que é exibido é a cadeia de caracteres literal, "{D}". O valor numérico que deveria ser formatado não é exibido.

Uma maneira de escrever seu código para evitar a interpretação incorreta de chaves de escape e itens de formato é formatar as chaves e os itens de formato separadamente. Ou seja, na primeira operação de formato exibir uma chave de abertura literal, na operação seguinte exibir o resultado do item de formato e, na operação final, exibir uma chave de fechamento literal. O exemplo a seguir ilustra esta abordagem.

```csharp
int value = 6324;
string output = string.Format("{0}{1:D}{2}", 
                             "{", value, "}");
Console.WriteLine(output);
// The example displays the following output:
//       {6324} 
```

```vb
Dim value As Integer = 6324
Dim output As String = String.Format("{0}{1:D}{2}", _
                                     "{", value, "}")
Console.WriteLine(output)   
' The example displays the following output:
'       {6324}
```

### <a name="processing-order"></a>Ordem de processamento

Se a chamada ao método de formatação de composição incluir um argumento [IFormatProvider](xref:System.IFormatProvider) cujo valor não é nulo, o tempo de execução chamará seu método [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) para solicitar uma implementação de [ICustomFormatter](xref:System.ICustomFormatter). Se o método puder retornar uma implementação de [ICustomFormatter](xref:System.ICustomFormatter), ele será armazenado em cache para uso posterior. 

Cada valor na lista de parâmetros que corresponder a um item de formato será convertido em uma cadeia de caracteres por meio da execução das etapas a seguir. Se qualquer condição nas três primeiras etapas for verdadeira, a representação de cadeia de caracteres do valor será retornada nessa etapa e as etapas subsequentes não serão executadas.

1. Se o valor a ser formatado for `null`, uma cadeia de caracteres vazia ("") será retornada. 

2. Se uma implementação de [ICustomFormatter](xref:System.ICustomFormatter) estiver disponível, o tempo de execução chamará seu método [Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)). Ele passa ao método o valor *formatString* do item de formato, se houver um presente ou `null`, se não houver, em conjunto com a implementação de [IFormatProvider](xref:System.IFormatProvider). 

3. Se o valor implementar a interface [IFormattable](xref:System.IFormattable), o método [ToString(String,IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) da interface será chamado. O método recebe o valor *formatString*, se houver um presente no item de formato ou `null`, se não houver. O argumento [IFormatProvider](xref:System.IFormatProvider) é determinado da seguinte forma:

    *   Para um valor numérico, se um método de formatação de composição com um argumento [IFormatProvider](xref:System.IFormatProvider) não nulo for chamado, o tempo de execução solicitará um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) de seu método [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)). Se ele não for capaz de fornecer um, se o valor do argumento for `null` ou se o método de formatação de composição não tiver um parâmetro [IFormatProvider](xref:System.IFormatProvider), o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo para a cultura do thread atual será usado. 
    
    * Para um valor de data e hora, se um método de formatação de composição com um argumento [IFormatProvider](xref:System.IFormatProvider) não nulo for chamado, o tempo de execução solicitará um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) de seu método [IFormatProvider.GetFormat](xref:System.IFormatProvider._GetFormat(System.Type). Se ele não for capaz de fornecer um, se o valor do argumento for `null` ou se o método de formatação de composição não tiver um parâmetro [IFormatProvider](xref:System.IFormatProvider), o objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) para a cultura do thread atual será usado. 
    
    * Para objetos de outros tipos, se uma formatação de composição for chamada com um argumento [IFormatProvider](xref:System.IFormatProvider), seu valor (incluindo `null`, se nenhum objeto [IFormatProvider](xref:System.IFormatProvider) for fornecido) será passado diretamente para a implementação de [IFormattable.ToString](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)). Caso contrário, um objeto [CultureInfo](xref:System.Globalization.CultureInfo) que representa a cultura atual do thread será passado para a implementação de [IFormattable.ToString](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)). 
    
4. O método sem parâmetros `ToString` do tipo, que substitui [Object.ToString()](xref:System.Object.ToString) ou herda o comportamento da sua classe base, é chamado. Nesse caso, a cadeia de caracteres de formato especificada pelo componente *formatString* no item de formato, se houver, será ignorada.

O alinhamento é aplicado após as etapas anteriores terem sido executadas. 

## <a name="code-examples"></a>Exemplos de código

O exemplo a seguir mostra uma cadeia de caracteres criada usando formatação de composição e outra criada usando o método `ToString` de um objeto. Os dois tipos de formatação produzem resultados equivalentes. 

```csharp
string FormatString1 = String.Format("{0:dddd MMMM}", DateTime.Now);
string FormatString2 = DateTime.Now.ToString("dddd MMMM");
```

```vb
Dim FormatString1 As String = String.Format("{0:dddd MMMM}", DateTime.Now)
Dim FormatString2 As String = DateTime.Now.ToString("dddd MMMM")
```

Supondo que o dia atual seja uma quinta-feira de maio, o valor de ambas as cadeias de caracteres no exemplo anterior será `Thursday May` na cultura do inglês nos EUA.

[Console.WriteLine](xref:System.Console.WriteLine) expõe a mesma funcionalidade que [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). A única diferença entre os dois métodos é que [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) retorna o resultado como uma cadeia de caracteres, enquanto [Console.WriteLine](xref:System.Console.WriteLine) grava o resultado no fluxo de saída associado ao objeto [Console](xref:System.Console). O exemplo a seguir usa o método [Console.WriteLine](xref:System.Console.WriteLine) para formatar o valor de `MyInt` como um valor de moeda.

```csharp
int MyInt = 100;
Console.WriteLine("{0:C}", MyInt);
// The example displays the following output 
// if en-US is the current culture:
//        $100.00
```

```vb
Dim MyInt As Integer = 100
Console.WriteLine("{0:C}", MyInt)
' The example displays the following output
' if en-US is the current culture:
'        $100.00
```

O exemplo a seguir demonstra a formatação de vários objetos, incluindo a formatação de um objeto de duas maneiras diferentes.

```csharp
string myName = "Fred";
Console.WriteLine(String.Format("Name = {0}, hours = {1:hh}, minutes = {1:mm}",
      myName, DateTime.Now));
// Depending on the current time, the example displays output like the following:
//    Name = Fred, hours = 11, minutes = 30                 
```

```vb
Dim myName As String = "Fred"
Console.WriteLine(String.Format("Name = {0}, hours = {1:hh}, minutes = {1:mm}", _
                  myName, DateTime.Now))
' Depending on the current time, the example displays output like the following:
'    Name = Fred, hours = 11, minutes = 30
```

O exemplo a seguir demonstra o uso de alinhamento na formatação. Os argumentos que são formatados são colocados entre caracteres de barra vertical (|) para realçar o alinhamento resultante.

```csharp
string myFName = "Fred";
string myLName = "Opals";
int myInt = 100;
string FormatFName = String.Format("First Name = |{0,10}|", myFName);
string FormatLName = String.Format("Last Name = |{0,10}|", myLName);
string FormatPrice = String.Format("Price = |{0,10:C}|", myInt); 
Console.WriteLine(FormatFName);
Console.WriteLine(FormatLName);
Console.WriteLine(FormatPrice);
Console.WriteLine();

FormatFName = String.Format("First Name = |{0,-10}|", myFName);
FormatLName = String.Format("Last Name = |{0,-10}|", myLName);
FormatPrice = String.Format("Price = |{0,-10:C}|", myInt);
Console.WriteLine(FormatFName);
Console.WriteLine(FormatLName);
Console.WriteLine(FormatPrice);
// The example displays the following output on a system whose current
// culture is en-US:
//          First Name = |      Fred|
//          Last Name = |     Opals|
//          Price = |   $100.00|
//
//          First Name = |Fred      |
//          Last Name = |Opals     |
//          Price = |$100.00   |
```

```vb
Dim myFName As String = "Fred"
Dim myLName As String = "Opals"

Dim myInt As Integer = 100
Dim FormatFName As String = String.Format("First Name = |{0,10}|", myFName)
Dim FormatLName As String = String.Format("Last Name = |{0,10}|", myLName)
Dim FormatPrice As String = String.Format("Price = |{0,10:C}|", myInt)
Console.WriteLine(FormatFName)
Console.WriteLine(FormatLName)
Console.WriteLine(FormatPrice)
Console.WriteLine()

FormatFName = String.Format("First Name = |{0,-10}|", myFName)
FormatLName = String.Format("Last Name = |{0,-10}|", myLName)
FormatPrice = String.Format("Price = |{0,-10:C}|", myInt)
Console.WriteLine(FormatFName)
Console.WriteLine(FormatLName)
Console.WriteLine(FormatPrice)
' The example displays the following output on a system whose current
' culture is en-US:
'          First Name = |      Fred|
'          Last Name = |     Opals|
'          Price = |   $100.00|
'
'          First Name = |Fred      |
'          Last Name = |Opals     |
'          Price = |$100.00   |
```

## <a name="see-also"></a>Consulte também

[Console.WriteLine](xref:System.Console.WriteLine)

[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))

[Formatando tipos](formatting-types.md)

[Cadeias de caracteres de formato de data e hora padrão](standard-datetime.md)

[Cadeias de caracteres de formato de data e hora personalizado](custom-datetime.md)

[Cadeias de caracteres de formato de enumeração](enumeration-format.md)

[Cadeias de caracteres de formato numérico padrão](standard-numeric.md)

[Cadeias de caracteres de formato numérico personalizado](custom-numeric.md)

[Cadeias de caracteres de formato TimeSpan padrão](standard-timespan.md)

[Cadeias de caracteres de formato TimeSpan personalizado](custom-timespan.md)



<!--HONumber=Nov16_HO3-->


