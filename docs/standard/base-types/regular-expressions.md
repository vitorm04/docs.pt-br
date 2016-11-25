---
title: "Expressões regulares no .NET"
description: "Expressões regulares no .NET"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d1a640cf-09ca-48f7-800c-a627a6d549c9
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 1fc1edd64c330fe579f389750432665ed982976e

---

# <a name="regular-expressions-in-net"></a>Expressões regulares no .NET

Expressões regulares oferecem um método poderoso, flexível e eficiente de processamento de texto. A extensiva notação de correspondência de padrões de expressões regulares permite que você analise rapidamente grandes quantidades de texto para encontrar padrões de caracteres específicos; para validar o texto e garantir que ele corresponda a um padrão predefinido (como um endereço de email); para extrair, editar, substituir ou excluir subcadeias de caracteres de texto; e para adicionar as cadeias de caracteres extraídas para uma coleção a fim de gerar um relatório. Para vários aplicativos que lidam com cadeias de caracteres ou que analisam grandes blocos de texto, as expressões regulares são uma ferramenta indispensável.

## <a name="how-regular-expressions-work"></a>Como funcionam as expressões regulares

A parte mais importante do processamento de texto com expressões regulares é o mecanismo de expressões regulares, que é representado pelo objeto [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) no .NET. No mínimo, o processamento de texto usando expressões regulares exige que o mecanismo de expressões regulares seja fornecido com os dois itens informativos a seguir:

* O padrão de expressão regular a ser identificado no texto. 
  
  No .NET, padrões de expressão regular são definidos por uma sintaxe ou linguagem especial, compatível com expressões regulares Perl 5 e inclui alguns recursos adicionais, como correspondência da direita para a esquerda. Para obter mais informações, consulte [Linguagem de expressões regulares – referência rápida](quick-ref.md).
  
* O texto a ser analisado para o padrão de expressão regular.

Os métodos da classe [Regex](xref:System.Text.RegularExpressions.Regex) permitem que você realize as seguintes operações:

* Determinar se o padrão de expressão regular ocorre no texto de entrada chamando o método [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)). Para obter um exemplo que usa o método [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) para validar texto, consulte [Como verificar se cadeias de caracteres estão em um formato de email válido](verify-format.md).

* Recuperar uma ou todas as ocorrências de texto que correspondem ao padrão de expressão regular chamando o método [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) ou [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)). O primeiro método retorna um objeto [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) que oferece informações sobre o texto correspondente. O último retorna um objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) que contém um objeto [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) para cada correspondência encontrada no texto analisado. 

* Substituir o texto que corresponde ao padrão da expressão regular chamando o método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)). Para ver exemplos que usam o método [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) para alterar formatos de data e remover caracteres inválidos de uma cadeia de caracteres, consulte [Como retirar caracteres inválidos de uma cadeia de caracteres](strip-characters.md) e [Exemplo de expressão regular: alterando formatos de data](changing-formats.md).

Para obter uma visão geral do modelo de objeto de expressão regular, consulte [O modelo de objeto de expressão regular](object-model.md).

Para obter mais informações sobre a linguagem de expressão regular, consulte [Linguagem de expressões regulares – referência rápida](quick-ref.md).

## <a name="regular-expression-examples"></a>Exemplos de expressões regulares

A classe [String](xref:System.String) inclui uma série de métodos de pesquisa de cadeia de caracteres e substituição que podem ser usados quando você quer localizar cadeias de caracteres literais em uma cadeia de caracteres maior. Expressões regulares são mais úteis quando você quer localizar uma dentre diversas subcadeias de caracteres em uma cadeia de caracteres maior ou quando quer identificar padrões em uma cadeia de caracteres, como mostrado nos exemplos a seguir. 

### <a name="example-1-replacing-substrings"></a>Exemplo 1: substituindo subcadeias de caracteres

Vamos presumir que uma lista de endereçamento contém nomes que, às vezes, incluem um pronome de tratamento (Sr., Srs., Srta. ou Sra.) junto com o nome e o sobrenome. Se não quiser incluir os pronomes de tratamento ao gerar etiquetas para envelopes na lista, é possível usar uma expressão regular para removê-los, como mostrado no exemplo a seguir.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(Mr\\.? |Mrs\\.? |Miss |Ms\\.? )";
      string[] names = { "Mr. Henry Hunt", "Ms. Sara Samuels", 
                         "Abraham Adams", "Ms. Nicole Norris" };
      foreach (string name in names)
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty));
   }
}
// The example displays the following output:
//    Henry Hunt
//    Sara Samuels
//    Abraham Adams
//    Nicole Norris
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(Mr\.? |Mrs\.? |Miss |Ms\.? )"
      Dim names() As String = { "Mr. Henry Hunt", "Ms. Sara Samuels", _
                                "Abraham Adams", "Ms. Nicole Norris" }
      For Each name As String In names
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty))
      Next                                
   End Sub
End Module
' The example displays the following output:
'    Henry Hunt
'    Sara Samuels
'    Abraham Adams
'    Nicole Norris
```

O padrão de expressão regular `(Mr\.? |Mrs\.? |Miss |Ms\.? )` corresponde a qualquer ocorrência de “Sr”, “Sr.”, “Sra”, “Sra.”, “Srta” ou “Srta.”. A chamada para o método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) substitui a cadeia de caracteres correspondente por [String.Empty](xref:System.String.Empty); em outras palavras, ela a remove da cadeia de caracteres original.

### <a name="example-2-identifying-duplicated-words"></a>Exemplo 2: identificando palavras duplicadas

Duplicar palavras acidentalmente é um erro comum que escritores cometem. Uma expressão regular pode ser usada para identificar palavras duplicadas, como mostrado no exemplo a seguir.

```csharp
using System;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string pattern = @"\b(\w+?)\s\1\b";
      string input = "This this is a nice day. What about this? This tastes good. I saw a a dog.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", 
                           match.Value, match.Groups[1].Value, match.Index);
   }
}
// The example displays the following output:
//       This this (duplicates 'This)' at position 0
//       a a (duplicates 'a)' at position 66
```

```vb
Imports System.Text.RegularExpressions

Module modMain
   Public Sub Main()
      Dim pattern As String = "\b(\w+?)\s\1\b"
      Dim input As String = "This this is a nice day. What about this? This tastes good. I saw a a dog."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", _
                           match.Value, match.Groups(1).Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       This this (duplicates 'This)' at position 0
'       a a (duplicates 'a)' at position 66
```

O padrão de expressão regular `\b(\w+?)\s\1\b` pode ser interpretado da seguinte maneira:

Sintaxe | Significado
------ | -------
`\b` | Iniciar em um limite de palavra.
`(\w+?)` | Corresponder a um ou mais caracteres de palavra, mas o menor número de caracteres possível. Juntos, formam um grupo que pode ser chamado de `\1`.
`\s` | Corresponde a um caractere de espaço em branco.
`\1` | Corresponder à subcadeia de caracteres que é igual ao grupo denominado `\1`.
`\b` | Corresponder a um limite de palavra.

O método [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) é chamado com opções de expressão regular definidas como [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase). Portanto, a operação de correspondência não faz distinção entre maiúsculas e minúsculas e o exemplo identifica a subcadeia de caracteres “This this” como uma duplicação.

Observe que a cadeia de caracteres de entrada inclui a subcadeia de caracteres “this? This”. No entanto, devido à pontuação no meio, ela não é identificada como uma duplicação.

### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Exemplo 3: compilando dinamicamente uma expressão regular sensível à cultura

O exemplo a seguir mostra a força das expressões regulares combinada à flexibilidade oferecida pelos recursos de globalização do .NET. Ele utiliza o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) para determinar o formato de valores de moeda na cultura atual do sistema. Então, essa informação é usada para construir dinamicamente uma expressão regular que extrai valores de moeda do texto. Para cada correspondência, ele extrai o subgrupo que contém somente a subcadeia de caracteres, converte-a para um valor [Decimal](xref:System.Decimal) e calcula uma soma acumulada. 

```csharp
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define text to be parsed.
      string input = "Office expenses on 2/13/2008:\n" + 
                     "Paper (500 sheets)                      $3.95\n" + 
                     "Pencils (box of 10)                     $1.00\n" + 
                     "Pens (box of 10)                        $4.49\n" + 
                     "Erasers                                 $2.19\n" + 
                     "Ink jet printer                        $69.95\n\n" + 
                     "Total Expenses                        $ 81.58\n"; 

      // Get current culture's NumberFormatInfo object.
      NumberFormatInfo nfi = CultureInfo.CurrentCulture.NumberFormat;
      // Assign needed property values to variables.
      string currencySymbol = nfi.CurrencySymbol;
      bool symbolPrecedesIfPositive = nfi.CurrencyPositivePattern % 2 == 0;
      string groupSeparator = nfi.CurrencyGroupSeparator;
      string decimalSeparator = nfi.CurrencyDecimalSeparator;

      // Form regular expression pattern.
      string pattern = Regex.Escape( symbolPrecedesIfPositive ? currencySymbol : "") + 
                       @"\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + 
                       Regex.Escape(decimalSeparator) + "[0-9]+)?)" + 
                       (! symbolPrecedesIfPositive ? currencySymbol : ""); 
      Console.WriteLine( "The regular expression pattern is:");
      Console.WriteLine("   " + pattern);      

      // Get text that matches regular expression pattern.
      MatchCollection matches = Regex.Matches(input, pattern, 
                                              RegexOptions.IgnorePatternWhitespace);               
      Console.WriteLine("Found {0} matches.", matches.Count); 

      // Get numeric string, convert it to a value, and add it to List object.
      List<decimal> expenses = new List<Decimal>();

      foreach (Match match in matches)
         expenses.Add(Decimal.Parse(match.Groups[1].Value));      

      // Determine whether total is present and if present, whether it is correct.
      decimal total = 0;
      foreach (decimal value in expenses)
         total += value;

      if (total / 2 == expenses[expenses.Count - 1]) 
         Console.WriteLine("The expenses total {0:C2}.", expenses[expenses.Count - 1]);
      else
         Console.WriteLine("The expenses total {0:C2}.", total);
   }  
}
// The example displays the following output:
//       The regular expression pattern is:
//          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
//       Found 6 matches.
//       The expenses total $81.58.
```

```vb
Imports System.Collections.Generic
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Module Example
   Public Sub Main()
      ' Define text to be parsed.
      Dim input As String = "Office expenses on 2/13/2008:" + vbCrLf + _
                            "Paper (500 sheets)                      $3.95" + vbCrLf + _
                            "Pencils (box of 10)                     $1.00" + vbCrLf + _
                            "Pens (box of 10)                        $4.49" + vbCrLf + _
                            "Erasers                                 $2.19" + vbCrLf + _
                            "Ink jet printer                        $69.95" + vbCrLf + vbCrLf + _
                            "Total Expenses                        $ 81.58" + vbCrLf
      ' Get current culture's NumberFormatInfo object.
      Dim nfi As NumberFormatInfo = CultureInfo.CurrentCulture.NumberFormat
      ' Assign needed property values to variables.
      Dim currencySymbol As String = nfi.CurrencySymbol
      Dim symbolPrecedesIfPositive As Boolean = CBool(nfi.CurrencyPositivePattern Mod 2 = 0)
      Dim groupSeparator As String = nfi.CurrencyGroupSeparator
      Dim decimalSeparator As String = nfi.CurrencyDecimalSeparator

      ' Form regular expression pattern.
      Dim pattern As String = Regex.Escape(CStr(IIf(symbolPrecedesIfPositive, currencySymbol, ""))) + _
                              "\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + _
                              Regex.Escape(decimalSeparator) + "[0-9]+)?)" + _
                              CStr(IIf(Not symbolPrecedesIfPositive, currencySymbol, "")) 
      Console.WriteLine("The regular expression pattern is: ")
      Console.WriteLine("   " + pattern)      

      ' Get text that matches regular expression pattern.
      Dim matches As MatchCollection = Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)               
      Console.WriteLine("Found {0} matches. ", matches.Count)

      ' Get numeric string, convert it to a value, and add it to List object.
      Dim expenses As New List(Of Decimal)

      For Each match As Match In matches
         expenses.Add(Decimal.Parse(match.Groups.Item(1).Value))      
      Next

      ' Determine whether total is present and if present, whether it is correct.
      Dim total As Decimal
      For Each value As Decimal In expenses
         total += value
      Next

      If total / 2 = expenses(expenses.Count - 1) Then
         Console.WriteLine("The expenses total {0:C2}.", expenses(expenses.Count - 1))
      Else
         Console.WriteLine("The expenses total {0:C2}.", total)
      End If   
   End Sub
End Module
' The example displays the following output:
'       The regular expression pattern is:
'          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
'       Found 6 matches.
'       The expenses total $81.58.
```

Em um computador cuja cultura atual seja Inglês – Estados Unidos (en-US), o exemplo compila dinamicamente a expressão regular `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Esse padrão de expressão regular pode ser interpretado da seguinte maneira:

Sintaxe | Significado
------ | -------
`\$` | Procure uma única ocorrência do símbolo de cifrão ($) na cadeia de caracteres de entrada. A cadeia de caracteres do padrão de expressão regular inclui uma barra invertida para indicar que o símbolo de cifrão deve ser interpretado literalmente ao invés de como uma âncora de expressão regular. (O símbolo $ sozinho indicaria que o mecanismo de expressões regulares deveria tentar iniciar a correspondência no final de uma cadeia de caracteres.) Para assegurar que o símbolo de moeda da cultura atual não seja interpretado inadequadamente como um símbolo de expressão regular, o exemplo chama o método [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) para escapar do caractere.
`\s*` | Procure zero ou mais ocorrências de um caractere de espaço em branco.
`[-+]?` | Procure zero ou uma ocorrência de um sinal de positivo ou negativo.
`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` | Os parênteses externos ao redor da expressão a definem como um grupo de captura ou uma subexpressão. Se uma correspondência for encontrada, informações sobre essa parte da cadeia de caracteres correspondente podem ser recuperadas do segundo objeto [Group](xref:System.Text.RegularExpressions.Group) no objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups). (O primeiro elemento na coleção representa a correspondência inteira.)
`[0-9]{0,3}` | Procure de zero a três ocorrências dos dígitos decimais de 0 a 9.
`(,[0-9]{3})*` | Procure zero ou mais ocorrências de um separador de grupo seguido por três dígitos decimais.
`\.` | Procure uma única ocorrência do separador decimal.
`[0-9]+` | Procure por um ou mais dígitos decimais.
`(\.[0-9]+)?` | Procure zero ou uma ocorrência de um separador decimal seguido por pelo menos um dígito decimal.

## <a name="related-topics"></a>Tópicos relacionados

Título | Descrição
----- | -----------
[Linguagem de expressão regular – referência rápida](quick-ref.md) | Oferece informações sobre o conjunto de caracteres, operadores e constructos que você pode usar para definir expressões regulares.
[O modelo de objeto de expressão regular](object-model.md) | Oferece informações e exemplos de código que ilustram como usar as classes de expressão regular.
[Detalhes do comportamento de expressões regulares](regex-behavior.md) | Oferece informações sobre os recursos e o comportamento das expressões regulares do .NET.
[Exemplos de expressões regulares](regex-examples.md) | Oferece exemplos de código que ilustram usos típicos de expressões regulares.


## <a name="reference"></a>Referência

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex)




<!--HONumber=Nov16_HO3-->


