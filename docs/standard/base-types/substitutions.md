---
title: "Substituições em expressões regulares"
description: "Substituições em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0fded615-1021-4468-a644-b491814305c6
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 4b2b547b6edd67590ad75851b8b287e55dc7d70c

---

# <a name="substitutions-in-regular-expressions"></a>Substituições em expressões regulares

As substituições são elementos de linguagem que são reconhecidos apenas em padrões de substituição. Eles usam um padrão de expressão regular para definir o todo ou parte do texto que substitui o texto correspondente na cadeia de caracteres de entrada. O padrão de substituição pode consistir em uma ou mais substituições junto com caracteres literais. Os padrões de substituição são fornecidos para sobrecargas do método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) que têm um parâmetro *substituição* e para o método [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)). Os métodos substituem o padrão correspondente pelo padrão que é definido pelo parâmetro *substituição*.

O .NET define os elementos de substituição listados na tabela a seguir.

Substituição | Descrição
------------ | ----------- 
**$**_number_ | Inclui a última subcadeia de caracteres correspondida pelo grupo de captura que é identificado por *number*, no qual *number* é um valor decimal na cadeia de caracteres de substituição. Para obter mais informações, consulte [Substituindo um grupo numerado](#substituting-a-numbered-group).
**${**_name_**}** | Inclui a última subcadeia de caracteres correspondida pelo grupo nomeado que é designado por **(?<**_name_**>)** na cadeia de caracteres de substituição. Para obter mais informações, consulte [Substituindo um grupo nomeado](#substituting-a-named-group).
**$$** | Inclui um único literal “$” na cadeia de caracteres de substituição. Para obter mais informações, consulte [Substituindo um símbolo "$"](#substituting-a--character).
**$&** | Inclui uma cópia da correspondência inteira na cadeia de caracteres de substituição. Para obter mais informações, consulte [Substituindo a correspondência inteira](#substituting-the-entire-match).
**$`** | Inclui todo o texto da cadeia de caracteres de entrada antes da correspondência na cadeia de caracteres de substituição. Para obter mais informações, consulte [Substituindo o texto antes da correspondência](#substituting-the-text-before-the-match).
**$'** | Inclui todo o texto da cadeia de caracteres de entrada após a correspondência na cadeia de caracteres de substituição. Para obter mais informações, consulte [Substituindo o texto após a correspondência](#substituting-the-text-after-the-match). 
**$+** | O inclui o último grupo capturado na cadeia de caracteres de substituição. Para obter mais informações, consulte [Substituindo o último grupo capturado](#substituting-the-last-captured-group).
**$_** | Inclui a cadeia de entrada inteira na cadeia de caracteres de substituição. Para obter mais informações, consulte [Substituindo a cadeia de caracteres de entrada inteira](#substituting-the-entire-input-string).
 
## <a name="substitution-elements-and-replacement-patterns"></a>Elementos de substituição e padrões de substituição

As substituições são as únicas construções especiais reconhecidas em um padrão de substituição. Nenhum dos outros elementos de linguagem de expressões regulares, incluindo caracteres de escape e o ponto final (**.**), que corresponde a qualquer caractere, têm suporte. Da mesma forma, os elementos de linguagem de substituição são reconhecidos apenas nos padrões de substituição e nunca são válidos em padrões de expressões regulares. 

O único caractere que pode aparecer em um padrão de expressão regular ou em uma substituição é o caractere **$**, embora ele tenha um significado diferente em cada contexto. Em um padrão de expressão regular, **$** é uma âncora que corresponde ao final da cadeia de caracteres. Em um padrão de substituição, **$** indica o início de uma substituição. 

> [!NOTE]
> Para uma funcionalidade semelhante a um padrão de substituição dentro de uma expressão regular, use um backreference. Para obter mais informações sobre referências inversas, consulte [Constructos de referência inversa](backreference.md).
 
## <a name="substituting-a-numbered-group"></a>Substituindo um grupo numerado

O elemento de linguagem **$**_number_ inclui a última subcadeia de caracteres correspondida pelo grupo de captura na cadeia de caracteres de substituição, no qual *number* é o índice do grupo de captura. Por exemplo, o padrão de substituição `$1` indica que a subcadeia de caracteres correspondente deve ser substituída pelo primeiro grupo capturado. Para obter mais informações sobre os grupos de captura numerados, consulte [Agrupando constructos em expressões regulares](grouping.md).

Todos os dígitos que seguem **$** são interpretados como pertencentes ao grupo de número. Se essa não for sua intenção, você poderá substituir um grupo nomeado. Por exemplo, você pode usar a cadeia de caracteres de substituição **${1}1** em vez de **$11** para definir a cadeia de caracteres de substituição como o valor do primeiro grupo capturado junto com o número "1". Para obter mais informações, consulte [Substituindo um grupo nomeado](#substituting-a-named-group). 

Grupos de captura, aos quais não são atribuídos nomes explicitamente usando a sintaxe **(?<**_name-**>)**, são numerados da esquerda para a direita, começando em um. Os grupos nomeados também são numerados da esquerda para a direita, começando em um maior que o índice do último grupo não nomeado. Por exemplo, na expressão regular `(\w)(?<digit>\d)`, o índice do grupo nomeado `digit` é 2.

Se *number* não especificar um grupo de captura válido definido no padrão de expressão regular, **$**_number_ será interpretado como uma sequência de caracteres literal que será usada para substituir cada correspondência.

O exemplo a seguir usa a substituição **$**_número_ para remover o símbolo de moeda de um valor decimal. Ele remove os símbolos de moeda localizados no início ou término de um valor monetário e reconhece os dois separadores decimais mais comuns (“.” e “, "). 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*";
      string replacement = "$1";
      string input = "$16.32 12.19 £16.29 €18.29  €18,29";
      string result = Regex.Replace(input, pattern, replacement);
      Console.WriteLine(result);
   }
}
// The example displays the following output:
//       16.32 12.19 16.29 18.29  18,29
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*"
      Dim replacement As String = "$1"
      Dim input As String = "$16.32 12.19 £16.29 €18.29  €18,29"
      Dim result As String = Regex.Replace(input, pattern, replacement)
      Console.WriteLine(result)
   End Sub
End Module
' The example displays the following output:
'       16.32 12.19 16.29 18.29  18,29
```

O padrão de expressão regular `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\p{Sc}*` | Corresponde a zero ou mais caracteres de símbolos de moedas.
`\s?` | Corresponder a zero ou a um caractere de espaço em branco.
`\d+` | Corresponde a um ou mais dígitos decimais.
`[.,]?` | Corresponde a zero ou um ponto ou vírgula.
`\d*` | Corresponde a zero ou mais dígitos decimais.
`(\s?\d+[.,]?\d*)` | Corresponde a um espaço em branco seguido por um ou mais dígitos decimais, seguidos por zero ou um ponto ou uma vírgula, seguidos por zero ou mais dígitos decimais. Este é o primeiro grupo de captura. Como o padrão de substituição é `$1`, a chamada ao método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) substitui a subcadeia de caracteres inteira correspondente a esse grupo capturado. 
 
## <a name="substituting-a-named-group"></a>Substituindo um grupo nomeado

O elemento de linguagem **${**_name_**}** substitui a última subcadeia de caracteres correspondida pelo grupo de captura *name*, no qual *name* é o nome de um grupo de captura definido pelo elemento de linguagem **(?<**_name_**>)**. Para obter mais informações sobre os grupos de captura nomeados, consulte [Agrupando constructos em expressões regulares](grouping.md).

Se *name* não especificar um grupo de captura nomeado válido, definido no padrão da expressão regular, mas consistir em dígitos, **${**_name_**}** será interpretado como um grupo numerado. 

Se *name* não especificar um grupo de captura nomeado válido nem um grupo de captura numerado válido, definido no padrão da expressão regular, **${**_name_**}** será interpretado como uma sequência de caracteres literal que será usada para substituir cada correspondência.

O exemplo a seguir usa a substituição **${**_name_**}** para remover o símbolo de moeda de um valor decimal. Ele remove os símbolos de moeda localizados no início ou término de um valor monetário e reconhece os dois separadores decimais mais comuns (“.” e “, ").

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\p{Sc}*(?<amount>\s?\d+[.,]?\d*)\p{Sc}*";
      string replacement = "${amount}";
      string input = "$16.32 12.19 £16.29 €18.29  €18,29";
      string result = Regex.Replace(input, pattern, replacement);
      Console.WriteLine(result);
   }
}
// The example displays the following output:
//       16.32 12.19 16.29 18.29  18,29
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\p{Sc}*(?<amount>\s?\d+[.,]?\d*)\p{Sc}*"
      Dim replacement As String = "${amount}"
      Dim input As String = "$16.32 12.19 £16.29 €18.29  €18,29"
      Dim result As String = Regex.Replace(input, pattern, replacement)
      Console.WriteLine(result)
   End Sub
End Module
' The example displays the following output:
'       16.32 12.19 16.29 18.29  18,29
```

O padrão de expressão regular `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` é definido conforme mostrado na tabela a seguir. 

Padrão | Descrição
------- | -----------
`\p{Sc}*` | Corresponde a zero ou mais caracteres de símbolos de moedas.
`\s?` | Corresponder a zero ou a um caractere de espaço em branco.
`\d+` | Corresponde a um ou mais dígitos decimais.
`[.,]?` | Corresponde a zero ou um ponto ou vírgula.
`\d*` | Corresponde a zero ou mais dígitos decimais.
`(?<amount>\s?\d[.,]?\d*)` | Corresponde a um espaço em branco seguido por um ou mais dígitos decimais, seguidos por zero ou um ponto ou uma vírgula, seguidos por zero ou mais dígitos decimais. Este é o grupo de captura chamado quantidade. Como o padrão de substituição é `${amount}`, a chamada ao método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) substitui a subcadeia de caracteres inteira correspondente a esse grupo capturado. 
 
## <a name="substituting-a-character"></a>Substituindo um caractere $

A substituição de **$$** insere um caractere literal "$" na cadeia de caracteres substituída. 

O exemplo a seguir usa o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) para determinar o símbolo de moeda atual da cultura e seu posicionamento em uma cadeia de caracteres de moeda. Ele então cria um padrão de expressão regular e um padrão de substituição dinamicamente. Se o exemplo é executado em um computador cuja cultura atual é en-US, ele gera o padrão de expressão regular `\b(\d+)(\.(\d+))?` e o padrão de substituição `$$ $1$2`. O padrão de substituição substitui o texto correspondente por um símbolo de moeda e um espaço seguido pelo primeiro e segundo grupos capturados.

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define array of decimal values.
      string[] values= { "16.35", "19.72", "1234", "0.99"};
      // Determine whether currency precedes (True) or follows (False) number.
      bool precedes = NumberFormatInfo.CurrentInfo.CurrencyPositivePattern % 2 == 0;
      // Get decimal separator.
      string cSeparator = NumberFormatInfo.CurrentInfo.CurrencyDecimalSeparator;
      // Get currency symbol.
      string symbol = NumberFormatInfo.CurrentInfo.CurrencySymbol;
      // If symbol is a "$", add an extra "$".
      if (symbol == "$") symbol = "$$";

      // Define regular expression pattern and replacement string.
      string pattern = @"\b(\d+)(" + cSeparator + @"(\d+))?"; 
      string replacement = "$1$2";
      replacement = precedes ? symbol + " " + replacement : replacement + " " + symbol;
      foreach (string value in values)
         Console.WriteLine("{0} --> {1}", value, Regex.Replace(value, pattern, replacement));
   }
}
// The example displays the following output:
//       16.35 --> $ 16.35
//       19.72 --> $ 19.72
//       1234 --> $ 1234
//       0.99 --> $ 0.99
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      ' Define array of decimal values.
      Dim values() As String = { "16.35", "19.72", "1234", "0.99"}
      ' Determine whether currency precedes (True) or follows (False) number.
      Dim precedes As Boolean = (NumberFormatInfo.CurrentInfo.CurrencyPositivePattern Mod 2 = 0)
      ' Get decimal separator.
      Dim cSeparator As String = NumberFormatInfo.CurrentInfo.CurrencyDecimalSeparator
      ' Get currency symbol.
      Dim symbol As String = NumberFormatInfo.CurrentInfo.CurrencySymbol
      ' If symbol is a "$", add an extra "$".
      If symbol = "$" Then symbol = "$$"

      ' Define regular expression pattern and replacement string.
      Dim pattern As String = "\b(\d+)(" + cSeparator + "(\d+))?" 
      Dim replacement As String = "$1$2"
      replacement = If(precedes, symbol + " " + replacement, replacement + " " + symbol)
      For Each value In values
         Console.WriteLine("{0} --> {1}", value, Regex.Replace(value, pattern, replacement))
      Next
   End Sub
End Module
' The example displays the following output:
'       16.35 --> $ 16.35
'       19.72 --> $ 19.72
'       1234 --> $ 1234
'       0.99 --> $ 0.99
```

O padrão de expressão regular `\b(\d+)(\.(\d+))?` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Inicia a correspondência no começo de um limite de palavra.
`(\d+)` | Corresponde a um ou mais dígitos decimais. Este é o primeiro grupo de captura.
`\.` | Faz a correspondência a um período (o separador decimal).
`(\d+)` | Corresponde a um ou mais dígitos decimais. Este é o terceiro grupo de captura.
`(\.(\d+))?` | Faz a correspondência de zero ou uma ocorrência de um período seguido por um ou mais dígitos decimais. Este é o segundo grupo de captura.
 
## <a name="substituting-the-entire-match"></a>Substituindo a correspondência inteira

A substituição **$&** inclui a correspondência inteira na cadeia de caracteres de substituição. Muitas vezes, ela é usada para adicionar uma subcadeia de caracteres ao início ou fim da cadeia de caracteres correspondente. Por exemplo, o padrão de substituição `($&)` adiciona parênteses no início e no final de cada correspondência. Se não houver correspondência, a substituição **$&** não terá efeito.

O exemplo a seguir usa a substituição **$&** para adicionar aspas no início e no final de títulos de livros armazenados em uma matriz de cadeia de caracteres.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^(\w+\s?)+$";
      string[] titles = { "A Tale of Two Cities", 
                          "The Hound of the Baskervilles", 
                          "The Protestant Ethic and the Spirit of Capitalism", 
                          "The Origin of Species" };
      string replacement = "\"$&\"";
      foreach (string title in titles)
         Console.WriteLine(Regex.Replace(title, pattern, replacement));
   }
}
// The example displays the following output:
//       "A Tale of Two Cities"
//       "The Hound of the Baskervilles"
//       "The Protestant Ethic and the Spirit of Capitalism"
//       "The Origin of Species"
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^(\w+\s?)+$"
      Dim titles() As String = { "A Tale of Two Cities", _
                                 "The Hound of the Baskervilles", _
                                 "The Protestant Ethic and the Spirit of Capitalism", _
                                 "The Origin of Species" }
      Dim replacement As String = """$&"""
      For Each title As String In titles
         Console.WriteLine(Regex.Replace(title, pattern, replacement))
      Next  
   End Sub
End Module
' The example displays the following output:
'       "A Tale of Two Cities"
'       "The Hound of the Baskervilles"
'       "The Protestant Ethic and the Spirit of Capitalism"
'       "The Origin of Species"
```

O padrão de expressão regular `^(\w+\s?)+$` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`^` | Começa a correspondência no início da cadeia de caracteres de entrada.
`(\w+\s?)+` | Corresponde ao padrão de um ou mais caracteres de palavra seguidos por zero ou um espaço em branco uma ou mais vezes. 
`$` | Corresponder ao final da cadeia de caracteres de entrada.

O padrão de substituição `"$&"` adiciona aspas literais no início e no final de cada correspondência.

## <a name="substituting-the-text-before-the-match"></a>Substituindo o texto antes da correspondência

A substituição **$`** substitution replaces the matched string with the entire input string before the match. That is, it duplicates the input string up to the match while removing the matched text. Any text that follows the matched text is unchanged in the result string. If there are multiple matches in an input string, the replacement text is derived from the original input string, rather than from the string in which text has been replaced by earlier matches. (The example provides an illustration.) If there is no match, the **$`** não terá efeito.

O exemplo a seguir usa o padrão de expressão regular `\d+` para corresponder a uma sequência de um ou mais dígitos decimais na cadeia de caracteres de entrada. A cadeia de caracteres de substituição **$`** substitui esses dígitos pelo texto que precede a correspondência. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aa1bb2cc3dd4ee5";
      string pattern = @"\d+";
      string substitution = "$`";
      Console.WriteLine("Matches:");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);

      Console.WriteLine("Input string:  {0}", input);
      Console.WriteLine("Output string: " + 
                        Regex.Replace(input, pattern, substitution));
   }
}
// The example displays the following output:
//    Matches:
//       1 at position 2
//       2 at position 5
//       3 at position 8
//       4 at position 11
//       5 at position 14
//    Input string:  aa1bb2cc3dd4ee5
//    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aa1bb2cc3dd4ee5"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$`"
      Console.WriteLine("Matches:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
      Console.WriteLine("Input string:  {0}", input)
      Console.WriteLine("Output string: " + _
                        Regex.Replace(input, pattern, substitution))
   End Sub
End Module
' The example displays the following output:
'    Matches:
'       1 at position 2
'       2 at position 5
'       3 at position 8
'       4 at position 11
'       5 at position 14
'    Input string:  aa1bb2cc3dd4ee5
'    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

Neste exemplo, a cadeia de caracteres de entrada `"aa1bb2cc3dd4ee5"` contém cinco correspondências. A tabela a seguir ilustra como a substituição $` faz com que o mecanismo de expressão regular substitua cada correspondência na cadeia de caracteres de entrada. O texto inserido é mostrado em negrito na coluna da Cadeia de caracteres de resultado.

Corresponder a | Posição | Cadeia de caracteres antes da correspondência | Cadeia de caracteres de resultado
----- | -------- | ------------------- | -------------
1 | 2 | aa | aa**aa**bb2cc3dd4ee5
2 | 5 | aa1bb | aaaabb**aa1bb**cc3dd4ee5
3 | 8 | aa1bb2cc | aaaabbaa1bbcc**aa1bb2cc**dd4ee5
4 | 11 | aa1bb2cc3dd | aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5
5 | 14 | aa1bb2cc3dd4ee | aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee **aa1bb2cc3dd4ee**
 
## <a name="substituting-the-text-after-the-match"></a>Substituindo o texto após a correspondência

A substituição **$'** substitui a cadeia de caracteres correspondida pela cadeia de caracteres de entrada inteira após a correspondência. Ou seja, ela duplica a cadeia de caracteres de entrada após a correspondência e remove o texto correspondido. Qualquer texto antes do texto correspondido permanece inalterado na cadeia de caracteres de resultado. Se não houver correspondência, a substituição **$'** não terá efeito.

O exemplo a seguir usa o padrão de expressão regular `\d+` para corresponder a uma sequência de um ou mais dígitos decimais na cadeia de caracteres de entrada. A cadeia de caracteres de substituição **$'** substitui esses dígitos pelo texto após a correspondência. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aa1bb2cc3dd4ee5";
      string pattern = @"\d+";
      string substitution = "$'";
      Console.WriteLine("Matches:");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
      Console.WriteLine("Input string:  {0}", input);
      Console.WriteLine("Output string: " + 
                        Regex.Replace(input, pattern, substitution));
   }
}
// The example displays the following output:
//    Matches:
//       1 at position 2
//       2 at position 5
//       3 at position 8
//       4 at position 11
//       5 at position 14
//    Input string:  aa1bb2cc3dd4ee5
//    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aa1bb2cc3dd4ee5"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$'"
      Console.WriteLine("Matches:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
      Console.WriteLine("Input string:  {0}", input)
      Console.WriteLine("Output string: " + _
                        Regex.Replace(input, pattern, substitution))
   End Sub
End Module
' The example displays the following output:
'    Matches:
'       1 at position 2
'       2 at position 5
'       3 at position 8
'       4 at position 11
'       5 at position 14
'    Input string:  aa1bb2cc3dd4ee5
'    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

Neste exemplo, a cadeia de caracteres de entrada `"aa1bb2cc3dd4ee5"` contém cinco correspondências. A tabela a seguir ilustra como a substituição **$'** faz com que o mecanismo de expressão regular substitua cada correspondência na cadeia de caracteres de entrada. O texto inserido é mostrado em negrito na coluna da Cadeia de caracteres de resultado.

Corresponder a | Posição | Cadeia de caracteres antes da correspondência | Cadeia de caracteres de resultado
----- | -------- | ------------------- | -------------
1 | 2 | bb2cc3dd4ee5 | aa**bb2cc3dd4ee5**bb2cc3dd4ee5
2 | 5 | cc3dd4ee5 | aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5
3 | 8 | dd4ee5 | aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5
4 | 11 | ee5 | aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5
5 | 14 | [String.Empty](xref:System.String.Empty) | aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee
 
## <a name="substituting-the-last-captured-group"></a>Substituindo o último grupo capturado

A substituição **$+** substitui a cadeia de caracteres correspondida pelo último grupo capturado. Se não houver nenhum grupo capturado ou se o valor do grupo capturado por último for [String.Empty](xref:System.String.Empty), a substituição **$+** não terá efeito.

O exemplo a seguir identifica palavras duplicadas em uma cadeia de caracteres e usa a substituição **$+** para substituí-los por uma única ocorrência da palavra. A opção [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) é usada para garantir que as palavras que diferem apenas em termos de letras maiúsculas e minúsculas, mas que de outra forma são idênticas, sejam consideradas duplicadas.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)\s\1\b";
      string substitution = "$+";
      string input = "The the dog jumped over the fence fence.";
      Console.WriteLine(Regex.Replace(input, pattern, substitution, 
                        RegexOptions.IgnoreCase));
   }
}
// The example displays the following output:
//      The dog jumped over the fence.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)\s\1\b"
      Dim substitution As String = "$+"
      Dim input As String = "The the dog jumped over the fence fence."
      Console.WriteLine(Regex.Replace(input, pattern, substitution, _
                                      RegexOptions.IgnoreCase))
   End Sub
End Module
' The example displays the following output:
'      The dog jumped over the fence.
```

O padrão de expressão regular `\b(\w+)\s\1\b` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Começa a correspondência em um limite de palavra.
`(\w+)` | Corresponde a um ou mais caracteres de palavra. Este é o primeiro grupo de captura.
`\s` | Corresponde a um caractere de espaço em branco.
`\1` | Corresponde ao primeiro grupo capturado.
`\b` | Termina a correspondência em um limite de palavra.
 
## <a name="substituting-the-entire-input-string"></a>Substituindo a cadeia de caracteres de entrada inteira

A substituição **$_** substitui a cadeia de caracteres correspondida pela cadeia de caracteres de entrada inteira. Ou seja, ela remove o texto correspondido e o substitui pela cadeia de caracteres inteira, inclusive o texto correspondido.

O exemplo a seguir corresponde a um ou mais dígitos decimais na cadeia de caracteres de entrada. Ele usa a substituição **$_** para substituí-los pela cadeia de caracteres de entrada inteira.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "ABC123DEF456";
      string pattern = @"\d+";
      string substitution = "$_";
      Console.WriteLine("Original string:          {0}", input);
      Console.WriteLine("String with substitution: {0}", 
                        Regex.Replace(input, pattern, substitution));      
   }
}
// The example displays the following output:
//       Original string:          ABC123DEF456
//       String with substitution: ABCABC123DEF456DEFABC123DEF456
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "ABC123DEF456"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$_"
      Console.WriteLine("Original string:          {0}", input)
      Console.WriteLine("String with substitution: {0}", _
                        Regex.Replace(input, pattern, substitution))      
   End Sub
End Module
' The example displays the following output:
'       Original string:          ABC123DEF456
'       String with substitution: ABCABC123DEF456DEFABC123DEF456
```

Neste exemplo, a cadeia de caracteres de entrada `"ABC123DEF456"` contém duas correspondências. A tabela a seguir ilustra como a substituição **$_** faz com que o mecanismo de expressão regular substitua cada correspondência na cadeia de caracteres de entrada. O texto inserido é mostrado em negrito na coluna da Cadeia de caracteres de resultado.

Corresponder a | Posição | Cadeia de caracteres antes da correspondência | Cadeia de caracteres de resultado
----- | -------- | ------------------- | -------------
1 | 3 | 123 | ABC**ABC123DEF456**DEF456
2 | 5 | 456 | ABCABC123DEF456DEF**ABC123DEF456**
 
## <a name="see-also"></a>Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)




<!--HONumber=Nov16_HO4-->


