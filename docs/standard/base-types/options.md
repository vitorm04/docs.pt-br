---
title: "Opções de expressões regulares"
description: "Opções de expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2db2c3e6-953e-4913-8168-d707c437f2df
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: a2a9fe356a0b2e9cf9415714bc01b77ea86229fc

---

# <a name="regular-expression-options"></a>Opções de expressões regulares

Por padrão, a comparação de uma cadeia de caracteres de entrada com quaisquer caracteres literais em um padrão de expressão regular diferencia maiúsculas e minúsculas; o espaço em branco em um padrão de expressão regular é interpretado como caracteres de espaço em branco literais e os grupos de captura em uma expressão regular são nomeados implícita e explicitamente. É possível modificar esses e vários outros aspectos do comportamento de expressão regular especificando opções de expressões regulares. Essas opções, que estão listadas na tabela a seguir, podem ser incluídas embutidas como parte do padrão de expressão regular ou podem ser fornecidas a um construtor de classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) ou método de correspondência padrão estático como um valor de enumeração [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions). 

Membro de RegexOptions | Caractere embutido | Efeito
------------------- | ---------------- | ------ 
[Nenhum](xref:System.Text.RegularExpressions.RegexOptions.None) | Não disponível | Use o comportamento padrão. Para obter mais informações, consulte [Opções padrão](#default-options).
[IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) | **i** | Use correspondência sem diferenciação de maiúsculas e minúsculas. Para obter mais informações, consulte [Correspondência sem diferenciação de maiúsculas e minúsculas](#case-insensitive-matching).
[Multilinha](xref:System.Text.RegularExpressions.RegexOptions.Multiline) | **m** | Use o modo multilinha, em que **^** e **$** correspondem ao início e o fim de cada linha (em vez do início e o fim da cadeia de caracteres de entrada). Para obter mais informações, consulte [Modo multilinha](#multiline-mode).
[Linha única](xref:System.Text.RegularExpressions.RegexOptions.Singleline) | **s** | Use o modo de linha única, em que o ponto (**.**) corresponde a todos os caracteres (em vez de todos os caracteres, exceto **\n**). Para obter mais informações, consulte [Modo de linha única](#single-line-mode).
[ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) | **n** | Não capture grupos sem nome. As únicas capturas válidas são grupos explicitamente nomeados ou numerados na forma **(?<**_name_**>** _subexpression_**)**. Para obter mais informações, consulte [Apenas capturas explícitas](#explicit-captures-only).
[Compilado](xref:System.Text.RegularExpressions.RegexOptions.Compiled) | Não disponível | Compile a expressão regular para um assembly. Para obter mais informações, consulte [Expressões regulares compiladas](#compiled-regular-expressions).
[IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) | **x** | Exclua um espaço em branco sem escape do padrão e habilite comentários após uma tecla de cerquilha (**#**). Para obter mais informações, consulte [Ignorar espaço em branco](#ignore-white-space).
[RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) | Não disponível | Altera a direção da pesquisa. A pesquisa se move da direita para a esquerda, em vez de da esquerda para a direita. Para obter mais informações, consulte [Modo da direita para a esquerda](#right-to-left-mode).
[ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) | Não disponível | Habilite o comportamento compatível com ECMAScript para a expressão. Para obter mais informações, consulte [Comportamento de correspondência de ECMAScript](#ecmascript-matching-behavior).
[CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) | Não disponível | Ignorar diferenças culturais no idioma. Para obter mais informações, consulte [Comparação usando cultura invariável](#comparison-using-the-invariant-culture).
 
## <a name="specifying-the-options"></a>Especificando as opções

É possível especificar opções para expressões regulares de uma destas três maneiras:

* No parâmetro *options* de um construtor da classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) como [Regex.Regex(String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions)) ou método de correspondência de padrão estático (Compartilhado no Visual Basic), como  [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)). O parâmetro *options* é uma combinação OR bit a bit de valores enumerados [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions). 

  Quando as opções são fornecidas a uma instância [Regex](xref:System.Text.RegularExpressions.Regex) mediante uso do parâmetro *options* de um construtor de classe, as opções são designadas para a propriedade [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions). No entanto, a propriedade [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) não reflete opções embutidas no próprio padrão de expressão regular. 

  O exemplo a seguir fornece uma ilustração. Ele usa o parâmetro *options* do método [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) para habilitar a correspondência sem diferenciação de maiúsculas e minúsculas e ignorar o espaço em branco do padrão ao identificar palavras que começam com a letra “d”.

  ```csharp
  string pattern = @"d \w+ \s";
  string input = "Dogs are decidedly good pets.";
  RegexOptions options = RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace;
  
  foreach (Match match in Regex.Matches(input, pattern, options))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "d \w+ \s"
  Dim input As String = "Dogs are decidedly good pets."
  Dim options As RegexOptions = RegexOptions.IgnoreCase Or RegexOptions.IgnorePatternWhitespace

  For Each match As Match In Regex.Matches(input, pattern, options)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9.  
  ```

* Aplicando opções embutidas em um padrão de expressão regular com a sintaxe **(?imnsx-imnsx)**. A opção se aplica ao padrão do ponto em que a opção é definida até o fim do padrão ou o ponto em que a opção tem é indefinida por outra opção embutida. Observe que a propriedade [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) de uma instância [Regex](xref:System.Text.RegularExpressions.Regex) não reflete essas opções embutidas. Para obter mais informações, consulte o tópico [Constructos diversos em expressões regulares](miscellaneous.md).

  O exemplo a seguir fornece uma ilustração. Ele usa opções embutidas para habilitar a correspondência sem diferenciação entre maiúsculas e minúsculas e ignorar o espaço em branco do padrão ao identificar palavras que começam com a letra “d”.

  ```csharp
  string pattern = @"(?ix) d \w+ \s";
  string input = "Dogs are decidedly good pets.";
  
  foreach (Match match in Regex.Matches(input, pattern))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "\b(?ix) d \w+ \s"
  Dim input As String = "Dogs are decidedly good pets."

  For Each match As Match In Regex.Matches(input, pattern)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9.  
  ```

* Aplicando opções embutidas em um constructo de agrupamento em particular em um padrão de expressão regular com a sintaxe **(?imnsx-imnsx:**_subexpression_**)**. Nenhum sinal antes de um conjunto de opções ativa o conjunto; um sinal de subtração antes de um conjunto de opções desativa o conjunto. (**?** é uma parte fixa da sintaxe do constructo do idioma exigida com as opções habilitadas ou desabilitadas.) A opção se aplica apenas àquele grupo. Para obter mais informações, consulte [Constructos de agrupamento em expressões regulares](grouping.md).

  O exemplo a seguir fornece uma ilustração. Ele usa opções embutidas em um constructo de agrupamento para habilitar a correspondência sem diferenciação entre maiúsculas e minúsculas e ignorar espaço em branco do padrão ao identificar palavras que começam com a letra “d”.

  ```csharp
  string pattern = @"\b(?ix: d \w+)\s";
  string input = "Dogs are decidedly good pets.";
  
  foreach (Match match in Regex.Matches(input, pattern))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "\b(?ix: d \w+)\s"
  Dim input As String = "Dogs are decidedly good pets."

  For Each match As Match In Regex.Matches(input, pattern)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9. 
  ```


Caso as opções sejam especificadas como embutidas, um sinal de subtração (-) antes de uma opção ou conjunto de opções as desativa. Por exemplo, o constructo embutido **(?ix-ms)** ativa as opções [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) e [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) e desativa as opções [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) e [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline). Todas as opções de expressões regulares são desativadas por padrão.

> [!NOTE]
> Se as opções de expressões regulares especificadas no parâmetro options de um construtor ou chamada de método entrarem em conflito com as opções especificadas como embutidas em um padrão de expressão regular, serão usadas as opções embutidas.
 

As cinco opções de expressões regulares a seguir podem ser definidas com o parâmetro *options* e embutidas:

* [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase)

* [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline)

* [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline)

* [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture)

* [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace)

As cinco opções de expressões regulares a seguir podem ser definidas usando o parâmetro *options*, mas não podem ser definidas como embutidas:

* [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None)

* [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled)

* [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft)

* [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant)

* [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript)

## <a name="determining-the-options"></a>Determinando as opções

É possível determinar quais opções foram fornecidas a um objeto [Regex](xref:System.Text.RegularExpressions.Regex) quando ele tiver sido instanciado recuperando o valor da propriedade [Regex.Options](xref:System.Text.RegularExpressions.Regex.Options) somente leitura.

Para testar a presença de qualquer opção, exceto [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None), realize uma operação AND com o valor da propriedade [Regex.Options](xref:System.Text.RegularExpressions.Regex.Options) e o valor [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) no qual você está interessado. Em seguida, teste se o resultado é igual ao valor de [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions). O exemplo a seguir testa se a opção [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) foi definida. 

```csharp
if ((rgx.Options & RegexOptions.IgnoreCase) == RegexOptions.IgnoreCase)
   Console.WriteLine("Case-insensitive pattern comparison.");
else
   Console.WriteLine("Case-sensitive pattern comparison.");
```

```vb
If (rgx.Options And RegexOptions.IgnoreCase) = RegexOptions.IgnoreCase Then
   Console.WriteLine("Case-insensitive pattern comparison.")
Else
   Console.WriteLine("Case-sensitive pattern comparison.")
End If 
```

Para testar [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None), determine se o valor da propriedade [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) é igual a [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None), como mostra o exemplo a seguir. 

```csharp
if (rgx.Options == RegexOptions.None)
   Console.WriteLine("No options have been set.");
```

```vb
If rgx.Options = RegexOptions.None Then
   Console.WriteLine("No options have been set.")
End If
```

As seções a seguir listam as opções com suporte na expressão regular no .NET. 

## <a name="default-options"></a>Opções padrão

A opção [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) indica que nenhuma opção foi especificada e o mecanismo de expressões regulares usa seu comportamento padrão. Isso inclui o seguinte:

* O padrão é interpretado como canônico e não como uma expressão regular ECMAScript.

* O padrão da expressão regular é combinado na cadeia de caracteres de entrada da esquerda para a direita.

* As comparações diferenciam maiúsculas de minúsculas.

* Os elementos de linguagem **^** e **$** correspondem ao início e o fim da cadeia de caracteres de entrada.

* O elemento de linguagem **.** corresponde a todos os caracteres, exceto **\n**.

* Qualquer espaço em branco em um padrão de expressão regular é interpretado como caractere de espaço literal.

* As convenções da cultura atual são usadas ao comparar o padrão com a cadeia de caracteres de entrada. 

* Os grupos de capturas no padrão de expressão regular são implícitos e explícitos. 

> [!NOTE]
> A opção [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) não tem equivalente embutido. Quando as opções de expressões regulares são embutidas aplicadas, o comportamento padrão é restaurado de modo opção a opção, desativando uma opção em particular. Por exemplo, `(?i)` ativa a comparação sem diferenciar maiúsculas de minúsculas e `(?-i)` restaura a comparação que diferencia maiúsculas de minúsculas.
 
Como a opção [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) representa o comportamento padrão do mecanismo de expressões regulares, ela raramente é especificada de forma explícita em uma chamada de método. Em vez disso, é chamado um método de construtor ou de correspondência padrão estático sem um parâmetro options.

## <a name="case-insensitive-matching"></a>Correspondência sem diferenciação entre maiúsculas e minúsculas

A opção [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) ou a opção embutida **i** fornecem correspondência sem diferenciação entre maiúsculas e minúsculas. Por padrão, são usadas as convenções de diferenciação entre maiúsculas e minúsculas da cultura atual.

O exemplo a seguir define um padrão de expressão regular, `\bthe\w*\b`, que corresponde a todas as palavras que começam com “the”. Como a primeira chamada para o método Match usa a comparação que diferencia maiúsculas de minúsculas padrão, a saída indica que a cadeia de caracteres “The”, que inicia a frase, não tem correspondência. Ela corresponde quando o método [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) é chamado com opções definidas para [IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase). 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bthe\w*\b";
      string input = "The man then told them about that event.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);

      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern, 
                                            RegexOptions.IgnoreCase))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found then at index 8.
//       Found them at index 18.
//       
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bthe\w*\b"
      Dim input As String = "The man then told them about that event."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern, _
                                               RegexOptions.IgnoreCase)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Found then at index 8.
'       Found them at index 18.
'       
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
```

O exemplo a seguir modifica o padrão da expressão regular do exemplo anterior para usar opções embutidas, em vez do parâmetro *options* para fornecer comparação sem diferenciação entre maiúsculas e minúsculas. O primeiro padrão define a opção que não diferencia maiúsculas de minúsculas em um constructo de agrupamento que se aplica apenas à letra “t” na cadeia de caracteres “the”. Como o constructo da opção ocorre no início do padrão, o segundo padrão aplica a opção que não diferencia maiúsculas de minúsculas a toda a expressão regular.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?i:t)he\w*\b";
      string input = "The man then told them about that event.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);

      Console.WriteLine();
      pattern = @"(?i)\bthe\w*\b";
      foreach (Match match in Regex.Matches(input, pattern, 
                                            RegexOptions.IgnoreCase))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
//       
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?i:t)he\w*\b"
      Dim input As String = "The man then told them about that event."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
      Console.WriteLine()
      pattern = "(?i)\bthe\w*\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
'       
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
```

## <a name="multiline-mode"></a>Modo multilinha

A opção [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) ou a opção embutida **m** habilita o mecanismo de expressões regulares para processar uma cadeia de caracteres de entrada que consiste em várias linhas. Altera a interpretação dos elementos de linguagem **^** e **$** para que correspondam ao início e o fim de uma linha, em vez de o início e o fim da cadeia de caracteres de entrada. 

Por padrão, **$** corresponde apenas ao final da cadeia de caracteres de entrada. Se você especificar a opção [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline), ela corresponde ao caractere de nova linha **(\n)** ou ao final da cadeia de caracteres de entrada. Porém, não corresponde à combinação de caractere de retorno de carro/avanço de linha. Para uma correspondência bem-sucedida, use a subexpressão **\r?$** em vez de apenas **$**. 

O exemplo a seguir extrai nomes e pontuações de jogadores de boliche e os adiciona a uma coleção [SortedList&lt;TKey, TValue&gt;](xref:System.Collections.Generic.SortedList%602), que os classifica em ordem decrescente. O método [Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) é chamado duas vezes. Na primeira chamada do método, a expressão regular é `^(\w+)\s(\d+)$` e nenhuma opção é definida. Como a saída mostra, uma vez que o mecanismo de expressões regulares não pode corresponder ao padrão de entrada junto com o início e o fim da cadeia de caracteres de entrada, nenhuma correspondência é encontrada. Na segunda chamada do método, a expressão regular é alterada para `^(\w+)\s(\d+)\r?$` e as opções são definidas como [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). Como a saída mostra, os nomes e pontuações são combinados com sucesso e as pontuações são exibidas em ordem decrescente.

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      SortedList<int, string> scores = new SortedList<int, string>(new DescendingComparer<int>());

      string input = "Joe 164\n" + 
                     "Sam 208\n" + 
                     "Allison 211\n" + 
                     "Gwen 171\n"; 
      string pattern = @"^(\w+)\s(\d+)$";
      bool matched = false;

      Console.WriteLine("Without Multiline option:");
      foreach (Match match in Regex.Matches(input, pattern))
      {
         scores.Add(Int32.Parse(match.Groups[2].Value), (string) match.Groups[1].Value);
         matched = true;
      }
      if (! matched)
         Console.WriteLine("   No matches.");
      Console.WriteLine();

      // Redefine pattern to handle multiple lines.
      pattern = @"^(\w+)\s(\d+)\r*$";
      Console.WriteLine("With multiline option:");
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
         scores.Add(Int32.Parse(match.Groups[2].Value), (string) match.Groups[1].Value);

      // List scores in descending order. 
      foreach (KeyValuePair<int, string> score in scores)
         Console.WriteLine("{0}: {1}", score.Value, score.Key);
   }
}

public class DescendingComparer<T> : IComparer<T>
{
   public int Compare(T x, T y)
   {
      return Comparer<T>.Default.Compare(x, y) * -1;       
   }
}
// The example displays the following output:
//   Without Multiline option:
//      No matches.
//   
//   With multiline option:
//   Allison: 211
//   Sam: 208
//   Gwen: 171
//   Joe: 164
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim scores As New SortedList(Of Integer, String)(New DescendingComparer(Of Integer)())

      Dim input As String = "Joe 164" + vbCrLf + _
                            "Sam 208" + vbCrLf + _
                            "Allison 211" + vbCrLf + _
                            "Gwen 171" + vbCrLf
      Dim pattern As String = "^(\w+)\s(\d+)$"
      Dim matched As Boolean = False

      Console.WriteLine("Without Multiline option:")
      For Each match As Match In Regex.Matches(input, pattern)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
         matched = True
      Next
      If Not matched Then Console.WriteLine("   No matches.")
      Console.WriteLine()

      ' Redefine pattern to handle multiple lines.
      pattern = "^(\w+)\s(\d+)\r*$"
      Console.WriteLine("With multiline option:")
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
      Next
      ' List scores in descending order. 
      For Each score As KeyValuePair(Of Integer, String) In scores
         Console.WriteLine("{0}: {1}", score.Value, score.Key)
      Next
   End Sub
End Module

Public Class DescendingComparer(Of T) : Implements IComparer(Of T)
   Public Function Compare(x As T, y As T) As Integer _
          Implements IComparer(Of T).Compare
      Return Comparer(Of T).Default.Compare(x, y) * -1       
   End Function
End Class
' The example displays the following output:
'    Without Multiline option:
'       No matches.
'    
'    With multiline option:
'    Allison: 211
'    Sam: 208
'    Gwen: 171
'    Joe: 164
```

O padrão de expressão regular `^(\w+)\s(\d+)\r*$` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`^` | Começar no início da linha.
`(\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. Este é o primeiro grupo de captura.
`\s` | Corresponde a um caractere de espaço em branco.
`(\d+)` | Corresponde a um ou mais dígitos decimais. Este é o segundo grupo de captura.
`\r?` | Corresponder a zero ou um caractere de retorno de carro.
`$` | Terminar no fim da linha.
 
O exemplo a seguir é equivalente ao anterior, exceto pelo fato de usar a opção embutida **(?m)** para definir a opção de multilinha.

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      SortedList<int, string> scores = new SortedList<int, string>(new DescendingComparer<int>());

      string input = "Joe 164\n" +  
                     "Sam 208\n" +  
                     "Allison 211\n" +  
                     "Gwen 171\n"; 
      string pattern = @"(?m)^(\w+)\s(\d+)\r*$";

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
         scores.Add(Convert.ToInt32(match.Groups[2].Value), match.Groups[1].Value);

      // List scores in descending order. 
      foreach (KeyValuePair<int, string> score in scores)
         Console.WriteLine("{0}: {1}", score.Value, score.Key);
   }
}

public class DescendingComparer<T> : IComparer<T>
{
   public int Compare(T x, T y) 
   {
      return Comparer<T>.Default.Compare(x, y) * -1;       
   }
}
// The example displays the following output:
//    Allison: 211
//    Sam: 208
//    Gwen: 171
//    Joe: 164
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim scores As New SortedList(Of Integer, String)(New DescendingComparer(Of Integer)())

      Dim input As String = "Joe 164" + vbCrLf + _
                            "Sam 208" + vbCrLf + _
                            "Allison 211" + vbCrLf + _
                            "Gwen 171" + vbCrLf
      Dim pattern As String = "(?m)^(\w+)\s(\d+)\r*$"

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
      Next
      ' List scores in descending order. 
      For Each score As KeyValuePair(Of Integer, String) In scores
         Console.WriteLine("{0}: {1}", score.Value, score.Key)
      Next
   End Sub
End Module

Public Class DescendingComparer(Of T) : Implements IComparer(Of T)
   Public Function Compare(x As T, y As T) As Integer _
          Implements IComparer(Of T).Compare
      Return Comparer(Of T).Default.Compare(x, y) * -1       
   End Function
End Class
' The example displays the following output:
'    Allison: 211
'    Sam: 208
'    Gwen: 171
'    Joe: 164
```

## <a name="single-line-mode"></a>Modo de linha única

A opção [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) ou a opção embutida s, faz o mecanismo de expressões regulares tratar a cadeia de caracteres de entrada como se consistisse em uma única linha. Isso é feito mudando o comportamento do elemento de linguagem de ponto (**.**) para que corresponda a todos os caracteres, em vez de corresponder a todo caractere exceto o caractere de nova linha **\n** ou \u000A.

O exemplo a seguir ilustra como o comportamento do . elemento de linguagem muda quando se usa a opção [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline). A expressão regular `^.+` começa no início da cadeia de caracteres e corresponde a todos os caracteres. Por padrão, a correspondência termina no final da primeira linha; o padrão de expressão regular corresponde ao caractere de retorno de carro, **\r** ou \u000D, mas não corresponde a **\n**. Como a opção [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) interpreta toda a cadeia de caracteres de entrada como uma única linha; ela corresponde a cada caractere na cadeia de caracteres de entrada, incluindo **\n**.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "^.+";
      string input = "This is one line and" + Environment.NewLine + "this is the second.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(Regex.Escape(match.Value));

      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Singleline))
         Console.WriteLine(Regex.Escape(match.Value));
   }
}
// The example displays the following output:
//       This\ is\ one\ line\ and\r
//       
//       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^.+"
      Dim input As String = "This is one line and" + vbCrLf + "this is the second."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.SingleLine)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
   End Sub
End Module
' The example displays the following output:
'       This\ is\ one\ line\ and\r
'       
'       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

O exemplo a seguir é equivalente ao anterior, exceto por usar a opção embutida **(?s)** para habilitar o modo de linha única. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {      
      string pattern = "(?s)^.+";
      string input = "This is one line and" + Environment.NewLine + "this is the second.";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(Regex.Escape(match.Value));
   }
}
// The example displays the following output:
//       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?s)^.+"
      Dim input As String = "This is one line and" + vbCrLf + "this is the second."

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
   End Sub
End Module
' The example displays the following output:
'       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

## <a name="explicit-captures-only"></a>Apenas capturas explícitas

Por padrão, grupos de capturas são definidos pelo uso de parênteses no padrão de expressão regular. Grupos nomeados recebem um nome ou número pela opção de linguagem **(?<**_name_**>** _subexpression_**)**, enquanto grupos não nomeados são acessíveis por índice. No objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection), grupos não nomeados antecedem grupos nomeados. 

Constructos de agrupamento costumam ser usados apenas para aplicar quantificadores a vários elementos de linguagem; as subcadeias de caracteres capturadas não são de interesse. Por exemplo, se a seguinte expressão regular:

```
\b\(?((\w+),?\s?)+[\.!?]\)?
```

for feita somente para extrair frases que terminem com um ponto, ponto de exclamação ou ponto de interrogação de um documento, apenas a frase resultante (representada pelo objeto [Match](xref:System.Text.RegularExpressions.Match)) é de interesse. As palavras individuais na coleção não são. 

Capturar grupos que não serão usados posteriormente pode ser caro, pois o mecanismo de expressões regulares precisa preencher os objetos de coleção [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) e [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection). Como alternativa, você pode usar a opção [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) ou a opção embutida **n** para especificar que apenas as capturas válidas são explicitamente nomeadas ou grupos numerados que são designados pelo constructo **(?<**_name_**>** _subexpression_**)**. 

O exemplo a seguir exibe informações sobre as correspondências retornadas pelo padrão de expressão regular `\b\(?((\w+),?\s?)+[\.!?]\)?` quando o método [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.Int32)) é chamado com e sem a opção [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture). Como mostra a saída da chamada do primeiro método, o mecanismo de expressões regulares preenche totalmente os objetos da coleção [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) e [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) com informações sobre subcadeias de caracteres capturadas. Como o segundo método é chamado com as opções definidas como [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture), ele não captura informações sobre grupos.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?((?>\w+),?\s?)+[\.!?]\)?";
      Console.WriteLine("With implicit captures:");
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
      Console.WriteLine();
      Console.WriteLine("With explicit captures only:");
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.ExplicitCapture))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//    With implicit captures:
//    The match: This is the first sentence.
//       Group 0: This is the first sentence.
//          Capture 0: This is the first sentence.
//       Group 1: sentence
//          Capture 0: This
//          Capture 1: is
//          Capture 2: the
//          Capture 3: first
//          Capture 4: sentence
//       Group 2: sentence
//          Capture 0: This
//          Capture 1: is
//          Capture 2: the
//          Capture 3: first
//          Capture 4: sentence
//    The match: Is it the beginning of a literary masterpiece?
//       Group 0: Is it the beginning of a literary masterpiece?
//          Capture 0: Is it the beginning of a literary masterpiece?
//       Group 1: masterpiece
//          Capture 0: Is
//          Capture 1: it
//          Capture 2: the
//          Capture 3: beginning
//          Capture 4: of
//          Capture 5: a
//          Capture 6: literary
//          Capture 7: masterpiece
//       Group 2: masterpiece
//          Capture 0: Is
//          Capture 1: it
//          Capture 2: the
//          Capture 3: beginning
//          Capture 4: of
//          Capture 5: a
//          Capture 6: literary
//          Capture 7: masterpiece
//    The match: I think not.
//       Group 0: I think not.
//          Capture 0: I think not.
//       Group 1: not
//          Capture 0: I
//          Capture 1: think
//          Capture 2: not
//       Group 2: not
//          Capture 0: I
//          Capture 1: think
//          Capture 2: not
//    The match: Instead, it is a nonsensical paragraph.
//       Group 0: Instead, it is a nonsensical paragraph.
//          Capture 0: Instead, it is a nonsensical paragraph.
//       Group 1: paragraph
//          Capture 0: Instead,
//          Capture 1: it
//          Capture 2: is
//          Capture 3: a
//          Capture 4: nonsensical
//          Capture 5: paragraph
//       Group 2: paragraph
//          Capture 0: Instead
//          Capture 1: it
//          Capture 2: is
//          Capture 3: a
//          Capture 4: nonsensical
//          Capture 5: paragraph
//    
//    With explicit captures only:
//    The match: This is the first sentence.
//       Group 0: This is the first sentence.
//          Capture 0: This is the first sentence.
//    The match: Is it the beginning of a literary masterpiece?
//       Group 0: Is it the beginning of a literary masterpiece?
//          Capture 0: Is it the beginning of a literary masterpiece?
//    The match: I think not.
//       Group 0: I think not.
//          Capture 0: I think not.
//    The match: Instead, it is a nonsensical paragraph.
//       Group 0: Instead, it is a nonsensical paragraph.
//          Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b\(?((?>\w+),?\s?)+[\.!?]\)?"
      Console.WriteLine("With implicit captures:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
      Console.WriteLine()
      Console.WriteLine("With explicit captures only:")
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.ExplicitCapture)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'    With implicit captures:
'    The match: This is the first sentence.
'       Group 0: This is the first sentence.
'          Capture 0: This is the first sentence.
'       Group 1: sentence
'          Capture 0: This
'          Capture 1: is
'          Capture 2: the
'          Capture 3: first
'          Capture 4: sentence
'       Group 2: sentence
'          Capture 0: This
'          Capture 1: is
'          Capture 2: the
'          Capture 3: first
'          Capture 4: sentence
'    The match: Is it the beginning of a literary masterpiece?
'       Group 0: Is it the beginning of a literary masterpiece?
'          Capture 0: Is it the beginning of a literary masterpiece?
'       Group 1: masterpiece
'          Capture 0: Is
'          Capture 1: it
'          Capture 2: the
'          Capture 3: beginning
'          Capture 4: of
'          Capture 5: a
'          Capture 6: literary
'          Capture 7: masterpiece
'       Group 2: masterpiece
'          Capture 0: Is
'          Capture 1: it
'          Capture 2: the
'          Capture 3: beginning
'          Capture 4: of
'          Capture 5: a
'          Capture 6: literary
'          Capture 7: masterpiece
'    The match: I think not.
'       Group 0: I think not.
'          Capture 0: I think not.
'       Group 1: not
'          Capture 0: I
'          Capture 1: think
'          Capture 2: not
'       Group 2: not
'          Capture 0: I
'          Capture 1: think
'          Capture 2: not
'    The match: Instead, it is a nonsensical paragraph.
'       Group 0: Instead, it is a nonsensical paragraph.
'          Capture 0: Instead, it is a nonsensical paragraph.
'       Group 1: paragraph
'          Capture 0: Instead,
'          Capture 1: it
'          Capture 2: is
'          Capture 3: a
'          Capture 4: nonsensical
'          Capture 5: paragraph
'       Group 2: paragraph
'          Capture 0: Instead
'          Capture 1: it
'          Capture 2: is
'          Capture 3: a
'          Capture 4: nonsensical
'          Capture 5: paragraph
'    
'    With explicit captures only:
'    The match: This is the first sentence.
'       Group 0: This is the first sentence.
'          Capture 0: This is the first sentence.
'    The match: Is it the beginning of a literary masterpiece?
'       Group 0: Is it the beginning of a literary masterpiece?
'          Capture 0: Is it the beginning of a literary masterpiece?
'    The match: I think not.
'       Group 0: I think not.
'          Capture 0: I think not.
'    The match: Instead, it is a nonsensical paragraph.
'       Group 0: Instead, it is a nonsensical paragraph.
'          Capture 0: Instead, it is a nonsensical paragraph.
```

O padrão de expressão regular `\b\(?((?>\w+),?\s?)+[\.!?]\)?` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Começar em um limite de palavra.
`\(?` | Corresponder zero ou uma ocorrência do parêntese de abertura (“(“).
`(?>\w+),?` | Corresponder um ou mais caracteres de palavra seguidos por zero ou uma vírgula. Não retroceda ao corresponder caracteres de palavra.
`\s?` | Corresponder a zero ou a um caractere de espaço em branco.
`((\w+),?\s?)+` | Corresponder a combinação de um ou mais caracteres de palavra, zero ou mais vírgulas e zero ou um caractere de espaço em branco uma ou mais vezes.
`[\.!?]\)?` | Corresponder qualquer um dos três símbolos de pontuação seguidos por zero ou um parêntese de fechamento (“)”).
 
Você também pode usar o elemento embutido **(?n)** para suprimir capturas automáticas. O exemplo a seguir modifica o padrão de expressão regular anterior para usar o elemento embutido **(?n)** em vez da opção [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"(?n)\b\(?((?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//       The match: This is the first sentence.
//          Group 0: This is the first sentence.
//             Capture 0: This is the first sentence.
//       The match: Is it the beginning of a literary masterpiece?
//          Group 0: Is it the beginning of a literary masterpiece?
//             Capture 0: Is it the beginning of a literary masterpiece?
//       The match: I think not.
//          Group 0: I think not.
//             Capture 0: I think not.
//       The match: Instead, it is a nonsensical paragraph.
//          Group 0: Instead, it is a nonsensical paragraph.
//             Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "(?n)\b\(?((?>\w+),?\s?)+[\.!?]\)?"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       The match: This is the first sentence.
'          Group 0: This is the first sentence.
'             Capture 0: This is the first sentence.
'       The match: Is it the beginning of a literary masterpiece?
'          Group 0: Is it the beginning of a literary masterpiece?
'             Capture 0: Is it the beginning of a literary masterpiece?
'       The match: I think not.
'          Group 0: I think not.
'             Capture 0: I think not.
'       The match: Instead, it is a nonsensical paragraph.
'          Group 0: Instead, it is a nonsensical paragraph.
'             Capture 0: Instead, it is a nonsensical paragraph.
```

Por fim, é possível usar o elemento do grupo embutido **(?n:)** para suprimir capturas automáticas de forma grupo a grupo. O exemplo a seguir modifica o padrão anterior para suprimir capturas sem nome no grupo externo, `((?>\w+),?\s?)`. Observe que isso também suprime capturas sem nome no grupo interno.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?(?n:(?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//       The match: This is the first sentence.
//          Group 0: This is the first sentence.
//             Capture 0: This is the first sentence.
//       The match: Is it the beginning of a literary masterpiece?
//          Group 0: Is it the beginning of a literary masterpiece?
//             Capture 0: Is it the beginning of a literary masterpiece?
//       The match: I think not.
//          Group 0: I think not.
//             Capture 0: I think not.
//       The match: Instead, it is a nonsensical paragraph.
//          Group 0: Instead, it is a nonsensical paragraph.
//             Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b\(?(?n:(?>\w+),?\s?)+[\.!?]\)?"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       The match: This is the first sentence.
'          Group 0: This is the first sentence.
'             Capture 0: This is the first sentence.
'       The match: Is it the beginning of a literary masterpiece?
'          Group 0: Is it the beginning of a literary masterpiece?
'             Capture 0: Is it the beginning of a literary masterpiece?
'       The match: I think not.
'          Group 0: I think not.
'             Capture 0: I think not.
'       The match: Instead, it is a nonsensical paragraph.
'          Group 0: Instead, it is a nonsensical paragraph.
'             Capture 0: Instead, it is a nonsensical paragraph.
```

## <a name="compiled-regular-expressions"></a>Expressões regulares compiladas

Por padrão, as expressões regulares no .NET são interpretadas. Quando um objeto [Regex](xref:System.Text.RegularExpressions.Regex) é instanciado ou um método [Regex](xref:System.Text.RegularExpressions.Regex) estático é chamado, o padrão de expressão regular é analisado em um conjunto de opcodes personalizados e um interpretador usa esses opcodes para executar a expressão regular. Isso envolve uma troca: o custo de inicializar o mecanismo de expressões regulares é minimizado com prejuízo do desempenho do tempo de execução.

Você pode usar expressões regulares compiladas, em vez de interpretadas, usando a opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled). Neste caso, quando um padrão é enviado ao mecanismo de expressões regulares, ele é analisado em um subconjunto de opcodes e convertido para a MSIL (linguagem intermediária da Microsoft), que pode ser enviada diretamente ao Common Language Runtime. Expressões regulares compiladas maximizam o desempenho do tempo de execução às custas do tempo de inicialização.

> [!NOTE]
> Uma expressão regular só pode ser compilada fornecendo o valor [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) ao parâmetro options de um construtor de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou um método de correspondência padrão estático. Não está disponível como uma opção embutida. 
 

É possível usar expressões regulares compiladas em chamadas para expressões regulares estáticas e de instância. Em expressões regulares estáticas, a opção [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) é enviada ao parâmetro options do método de correspondência padrão de expressão regular. Em expressões regulares de instância, é enviada ao parâmetro options do construtor de classe [Regex](xref:System.Text.RegularExpressions.Regex). Em ambos os casos, resulta em melhoria de desempenho. 

Porém, essa melhoria de desempenho ocorre apenas sob as seguintes condições:

* É usado um objeto [Regex](xref:System.Text.RegularExpressions.Regex) que representa uma expressão regular em particular, em várias chamadas para métodos de correspondência padrão de expressão regular.

* O objeto [Regex](xref:System.Text.RegularExpressions.Regex) não pode sair do escopo, então pode ser reutilizado.

* Uma expressão regular estática é usada em várias chamadas para métodos de correspondência padrão de expressão regular. (A melhoria de desempenho é possível porque as expressões regulares usadas em chamadas de método estático são armazenadas em cache pelo mecanismo de expressões regulares.) 

## <a name="ignore-white-space"></a>Ignorar espaço em branco

Por padrão, o espaço em branco em um padrão de expressão regular é significativo; ele força o mecanismo de expressões regulares para combinar um caractere de espaço em branco na cadeia de caracteres de entrada. Devido a isso, as expressões regulares `"\b\w+\s"` e `"\b\w+ "` são, de um modo geral, equivalentes. Além disso, quando a tecla de cerquilha (**#**) é encontrada em um padrão de expressão regular, ela é interpretada como um caractere literal a ser combinado.

A opção [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) ou a opção embutida **x**, altera esse comportamento padrão da seguinte maneira:

* É ignorado o espaço em branco sem escape no padrão de expressão regular. Para fazer parte de um padrão de expressão regular, os caracteres de espaço em branco devem ter escape (por exemplo, como **\s** ou “**\** ”).

* A tecla de cerquilha (**#**) é interpretada como o início de um comentário, em vez de um caractere literal. Todo o texto no padrão de expressão regular do caractere **#** até o fim da cadeia de caracteres é interpretado como comentário.

Porém, nos seguintes casos, os caracteres de espaço em branco em uma expressão regular não são ignorados, mesmo se você usar a opção [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace): 

* O espaço em branco dentro de uma classe de caractere sempre é interpretado literalmente. Por exemplo, o padrão da expressão regular `[ .,;:]` corresponde a qualquer caractere de espaço em branco, ponto, vírgula, dois pontos ou ponto e vírgula único. 

* Espaço em branco não é permitido dentro de um quantificador entre colchetes, como **{**_n_**}**, **{**_n_**,}** e **{**_n_**,**_m_**}**. Por exemplo, o padrão de expressão regular **\d{1. 3}** falha ao corresponder quaisquer sequências de dígitos de um a três dígitos porque contém um caractere de espaço em branco. 

* Não é permitido espaço em branco dentro da sequência de caracteres que introduz um elemento de linguagem. Por exemplo: 

    * O elemento de linguagem **(?:**_subexpression_**)** representa um grupo sem captura; a parte **(?:** do elemento não pode ter espaços inseridos. O padrão **(? :**_subexpression_**)** lança uma [ArgumentException](xref:System.ArgumentException) no tempo de execução porque o mecanismo de expressões regulares não consegue analisar o padrão; o padrão **(? :**_subexpression_**)** não consegue corresponder a *subexpression*.

    * O elemento de linguagem **\p{**_name_**}**, que representa uma categoria Unicode ou um bloco nomeado, não pode incluir espaços embutidos na parte **\p{** do elemento. Se você incluir um espaço em branco, o elemento lança uma [ArgumentException](xref:System.ArgumentException) no tempo de execução. 

Habilitar essa opção ajuda a simplificar expressões regulares que costumam ser difíceis de analisar e entender. Melhora a legibilidade e torna possível documentar uma expressão regular. 

O exemplo a seguir define o padrão de expressão regular a seguir:

`\b \(? ( (?>\w+) ,?\s? )+ [\.!?] \)? # Matches an entire sentence`.

Esse padrão é similar ao padrão definido na seção [Apenas capturas explícitas](#explicit-captures-only), exceto por usar a opção [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) para ignorar o espaço em branco padrão.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?((?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This is the first sentence.
//       Is it the beginning of a literary masterpiece?
//       I think not.
//       Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence."

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This is the first sentence.
'       Is it the beginning of a literary masterpiece?
'       I think not.
'       Instead, it is a nonsensical paragraph.
```

O exemplo a seguir usa a opção embutida **(?x)** para ignorar o espaço em branco padrão.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"(?x)\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This is the first sentence.
//       Is it the beginning of a literary masterpiece?
//       I think not.
//       Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "(?x)\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence."

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This is the first sentence.
'       Is it the beginning of a literary masterpiece?
'       I think not.
'       Instead, it is a nonsensical paragraph.
```

## <a name="right-to-left-mode"></a>Modo da direita para a esquerda

Por padrão, o mecanismo de expressões regulares pesquisa da esquerda para a direita. É possível reverter a direção de pesquisa usando a opção [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft). A pesquisa inicia automaticamente na última posição de caractere da cadeia de caracteres. Para métodos de correspondência padrão que incluem um parâmetro de posição inicial, como [Regex.Match(String, Int32)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.Int32)), a posição inicial é o índice da posição do caractere mais à direita em que a pesquisa deve iniciar. 

> [!NOTE]
> O modo de padrão da direita para a esquerda está disponível apenas fornecendo o valor [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) para o parâmetro options de um construtor de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou o método de correspondência padrão estático. Não está disponível como uma opção embutida. 
 

A opção [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) só muda a direção de pesquisa; ela não interpreta o padrão de expressão regular da direita para a esquerda. Por exemplo, a expressão regular `\bb\w+\s` corresponde palavras que começam com a letra “b” e são seguidas por um caractere de espaço em branco. No exemplo a seguir, a cadeia de caracteres de entrada consiste em três palavras que incluem um ou mais caracteres “b”. A primeira palavra começa com “b”, a segunda termina com “b” e a terceira inclui dois caracteres “b” no meio da palavra. Como a saída do exemplo mostra, apenas a primeira palavra corresponde ao padrão da expressão regular. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bb\w+\s";
      string input = "builder rob rabble";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.RightToLeft))
         Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);     
   }
}
// The example displays the following output:
//       'builder ' found at position 0.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bb\w+\s"
      Dim input As String = "builder rob rabble"
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.RightToLeft)
         Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)     
      Next
   End Sub
End Module
' The example displays the following output:
'       'builder ' found at position 0.
```

Observe também que a asserção lookahead (o elemento de linguagem **(?**=_subexpression_**)** e a asserção lookbehind (o elemento de linguagem **(?<**=_subexpression_**)** não mudam de direção. As asserções lookahead buscam à direita; as asserções lookbehind buscam à esquerda. Por exemplo, a expressão regular `(?<=\d{1,2}\s)\w+,?\s\d{4}` usa a asserção lookbehind para testar uma data que antecede um nome de mês. A expressão regular corresponde ao mês e o ano. Para obter informações sobre as asserções lookahead e lookbehind, consulte [Constructos de agrupamento em expressões regulares](grouping.md).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "1 May 1917", "June 16, 2003" };
      string pattern = @"(?<=\d{1,2}\s)\w+,?\s\d{4}";

      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern, RegexOptions.RightToLeft);
         if (match.Success)
            Console.WriteLine("The date occurs in {0}.", match.Value);
         else
            Console.WriteLine("{0} does not match.", input);
      }
   }
}
// The example displays the following output:
//       The date occurs in May 1917.
//       June 16, 2003 does not match.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "1 May 1917", "June 16, 2003" }
      Dim pattern As String = "(?<=\d{1,2}\s)\w+,?\s\d{4}"

      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern, RegexOptions.RightToLeft)
         If match.Success Then
            Console.WriteLine("The date occurs in {0}.", match.Value)
         Else
            Console.WriteLine("{0} does not match.", input)
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'       The date occurs in May 1917.
'       June 16, 2003 does not match.
```

O padrão de expressão regular é definido como mostra a tabela a seguir.

Padrão | Descrição
------- | ----------- 
`(?<=\d{1,2}\s)` | O início da correspondência deve ser antecedido por um ou dois dígitos decimais seguidos por um espaço.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`,?` | Corresponder a zero ou um caractere de vírgula.
`\s` | Corresponde a um caractere de espaço em branco.
`\d{4}` | Corresponder a quatro dígitos decimais.
 
## <a name="ecmascript-matching-behavior"></a>Comportamento de correspondência de ECMAScript

Por padrão, o mecanismo de expressões regulares usa comportamento canônico ao corresponder um padrão de expressão regular a um texto de entrada. Porém, é possível instruir o mecanismo de expressões regulares a usar o comportamento de correspondência ECMAScript especificando a opção [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript). 

> [!NOTE]
> O comportamento compatível com ECMAScript está disponível apenas fornecendo o valor [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) para o parâmetro options de um construtor de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou método de correspondência padrão estático. Não está disponível como uma opção embutida. 
 
A opção [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) pode ser combinada apenas com as opções [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) e [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline). O uso de qualquer outra opção em uma expressão regular resulta em uma [ArgumentOutOfRangeException](xref:System.ArgumentOutOfRangeException).

O comportamento das expressões regulares ECMAScript e canônicas difere em três áreas: sintaxe da classe de caractere, grupos de captura autorreferidos e interpretação octal versus de referência inversa. 

* Sintaxe da classe de caractere. Como as expressões regulares canônicas dão suporte a Unicode e o ECMAScrip não, as classes de caractere no ECMAScrip têm uma sintaxe mais limitada e alguns elementos de linguagem da classe de caractere têm um significado diferente. Por exemplo, o ECMAScript não dá suporte a elementos de linguagem como a categoria Unicode ou elementos de bloco *\p* e **\P**. De modo similar, o elemento **\w**, que corresponde um caractere de palavra, é equivalente à classe de caractere **[a-zA-Z_0-9]** ao usar ECMAScript e **[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]** ao usar comportamento canônico. Para obter mais informações, consulte [Classes de caracteres em expressões regulares](classes.md).

  O exemplo a seguir ilustra a diferença entre correspondência padrão ECMAScript e canônica. Define uma expressão regular, `\b(\w+\s*)+`, que combina palavras seguidas por caracteres de espaço em branco. A entrada consiste em duas cadeias de caracteres, uma que usa o conjunto de caracteres latinos e outra que usa o conjunto de caracteres cirílicos. Como a saída mostra, a chamada para o método [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) que usa correspondência ECMAScript falha ao combinar as palavras cirílicas, enquanto a chamada de método que usa correspondência canônica corresponde a essas palavras. 

  ```csharp
  using System;
  using System.Text.RegularExpressions;
  
  public class Example
  {
     public static void Main()
     {
        string[] values = { "целый мир", "the whole world" };
        string pattern = @"\b(\w+\s*)+";
        foreach (var value in values)
        {
           Console.Write("Canonical matching: ");
           if (Regex.IsMatch(value, pattern))
              Console.WriteLine("'{0}' matches the pattern.", value);
           else
              Console.WriteLine("{0} does not match the pattern.", value);
  
           Console.Write("ECMAScript matching: ");
           if (Regex.IsMatch(value, pattern, RegexOptions.ECMAScript))
              Console.WriteLine("'{0}' matches the pattern.", value);
           else
              Console.WriteLine("{0} does not match the pattern.", value);
           Console.WriteLine();
        }
     }
  }
  // The example displays the following output:
  //       Canonical matching: 'целый мир' matches the pattern.
  //       ECMAScript matching: целый мир does not match the pattern.
  //       
  //       Canonical matching: 'the whole world' matches the pattern.
  //       ECMAScript matching: 'the whole world' matches the pattern.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim values() As String = { "целый мир", "the whole world" }
        Dim pattern As String = "\b(\w+\s*)+"
        For Each value In values
           Console.Write("Canonical matching: ")
           If Regex.IsMatch(value, pattern)
              Console.WriteLine("'{0}' matches the pattern.", value)
           Else
              Console.WriteLine("{0} does not match the pattern.", value)
           End If

           Console.Write("ECMAScript matching: ")
           If Regex.IsMatch(value, pattern, RegexOptions.ECMAScript)
              Console.WriteLine("'{0}' matches the pattern.", value)
           Else
              Console.WriteLine("{0} does not match the pattern.", value)
           End If
           Console.WriteLine()
        Next
     End Sub
  End Module
  ' The example displays the following output:
  '       Canonical matching: 'целый мир' matches the pattern.
  '       ECMAScript matching: целый мир does not match the pattern.
  '       
  '       Canonical matching: 'the whole world' matches the pattern.
  '       ECMAScript matching: 'the whole world' matches the pattern.
  ```

* Grupos de capturas com autorreferência. Uma classe de captura de expressão regular com uma referência inversa para si mesma deve ser atualizada com cada iteração de captura. Como o exemplo a seguir mostra, esse recurso habilita a expressão regular `((a+)(\1) ?)+` para corresponder a cadeia de caracteres de entrada “ aa aaaa aaaaaa ” ao usar ECMAScript, mas não ao usar correspondência canônica. 

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     static string pattern;
  
     public static void Main()
     {
        string input = "aa aaaa aaaaaa "; 
        pattern = @"((a+)(\1) ?)+";
  
        // Match input using canonical matching.
        AnalyzeMatch(Regex.Match(input, pattern));

        // Match input using ECMAScript.
        AnalyzeMatch(Regex.Match(input, pattern, RegexOptions.ECMAScript));
     }   

     private static void AnalyzeMatch(Match m)
     {
        if (m.Success)
        {
           Console.WriteLine("'{0}' matches {1} at position {2}.",  
                             pattern, m.Value, m.Index);
           int grpCtr = 0;
           foreach (Group grp in m.Groups)
           {
              Console.WriteLine("   {0}: '{1}'", grpCtr, grp.Value);
              grpCtr++;
              int capCtr = 0;
              foreach (Capture cap in grp.Captures)
              {
                 Console.WriteLine("      {0}: '{1}'", capCtr, cap.Value);
                 capCtr++;
              }
           }
        }
        else
        {
           Console.WriteLine("No match found.");
        }   
        Console.WriteLine();
     }
  }
  // The example displays the following output:
  //    No match found.
  //    
  //    '((a+)(\1) ?)+' matches aa aaaa aaaaaa  at position 0.
  //       0: 'aa aaaa aaaaaa '
  //          0: 'aa aaaa aaaaaa '
  //       1: 'aaaaaa '
  //          0: 'aa '
  //          1: 'aaaa '
  //          2: 'aaaaaa '
  //       2: 'aa'
  //          0: 'aa'
  //          1: 'aa'
  //          2: 'aa'
  //       3: 'aaaa '
  //          0: ''
  //          1: 'aa '
  //          2: 'aaaa '
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Dim pattern As String

     Public Sub Main()
        Dim input As String = "aa aaaa aaaaaa " 
        pattern = "((a+)(\1) ?)+"
  
        ' Match input using canonical matching.
        AnalyzeMatch(Regex.Match(input, pattern))

        ' Match input using ECMAScript.
        AnalyzeMatch(Regex.Match(input, pattern, RegexOptions.ECMAScript))
     End Sub   

     Private Sub AnalyzeMatch(m As Match)
        If m.Success
           Console.WriteLine("'{0}' matches {1} at position {2}.", _ 
                             pattern, m.Value, m.Index)
           Dim grpCtr As Integer = 0
           For Each grp As Group In m.Groups
              Console.WriteLine("   {0}: '{1}'", grpCtr, grp.Value)
              grpCtr += 1
              Dim capCtr As Integer = 0
              For Each cap As Capture In grp.Captures
                 Console.WriteLine("      {0}: '{1}'", capCtr, cap.Value)
                 capCtr += 1
              Next
           Next
        Else
           Console.WriteLine("No match found.")
        End If   
        Console.WriteLine()
     End Sub
  End Module
  ' The example displays the following output:
  '    No match found.
  '    
  '    '((a+)(\1) ?)+' matches aa aaaa aaaaaa  at position 0.
  '       0: 'aa aaaa aaaaaa '
  '          0: 'aa aaaa aaaaaa '
  '       1: 'aaaaaa '
  '          0: 'aa '
  '          1: 'aaaa '  
  '          2: 'aaaaaa '
  '       2: 'aa'
  '          0: 'aa'
  '          1: 'aa'
  '          2: 'aa'
  '       3: 'aaaa '
  '          0: ''
  '          1: 'aa '
  '          2: 'aaaa '
  ``

  The regular expression is defined as shown in the following table.

Pattern | Description
------- | ----------- 
`(a+)` | Match the letter "a" one or more times. This is the second capturing group.
`(\1)` | Match the substring captured by the first capturing group. This is the third capturing group.
`?` | Match zero or one space characters.
`((a+)(\1) ?)+` | Match the pattern of one or more "a" characters followed by a string that matches the first capturing group followed by zero or one space characters one or more times. This is the first capturing group.
  
* Resolution of ambiguities between octal escapes and backreferences. The following table summarizes the differences in octal versus backreference interpretation by canonical and ECMAScript regular expressions.

Regular expression | Canonical behavior | ECMAScript behavior
------------------ | ------------------ | ------------------- 
`\0` followed by 0 to 2 octal digits | Interpret as an octal. For example, `\044` is always interpreted as an octal value and means "**$**". | Same behavior.
**\** followed by a digit from 1 to 9, followed by no additional decimal digits | Interpret as a backreference. For example, \9 always means backreference 9, even if a ninth capturing group does not exist. If the capturing group does not exist, the regular expression parser throws an [ArgumentException](xref:System.ArgumentException). | If a single decimal digit capturing group exists, backreference to that digit. Otherwise, interpret the value as a literal.
**\** followed by a digit from 1 to 9, followed by additional decimal digits | Interpret the digits as a decimal value. If that capturing group exists, interpret the expression as a backreference. Otherwise, interpret the leading octal digits up to octal 377; that is, consider only the low 8 bits of the value. Interpret the remaining digits as literals. For example, in the expression `\3000`, if capturing group 300 exists, interpret as backreference 300; if capturing group 300 does not exist, interpret as octal 300 followed by 0. | Interpret as a backreference by converting as many digits as possible to a decimal value that can refer to a capture. If no digits can be converted, interpret as an octal by using the leading octal digits up to octal 377; interpret the remaining digits as literals.
 
## Comparison using the invariant culture

By default, when the regular expression engine performs case-insensitive comparisons, it uses the casing conventions of the current culture to determine equivalent uppercase and lowercase characters. 

However, this behavior is undesirable for some types of comparisons, particularly when comparing user input to the names of system resources, such as passwords, files, or URLs. The following example illustrates such as scenario. The code is intended to block access to any resource whose URL is prefaced with **FILE://**. The regular expression attempts a case-insensitive match with the string by using the regular expression `$FILE://`. However, when the current system culture is tr-TR (Turkish-Turkey), "I" is not the uppercase equivalent of "i". As a result, the call to the [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method returns `false`, and access to the file is allowed. 

```csharp
CultureInfo defaultCulture = Thread.CurrentThread.CurrentCulture;
Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");

string input = "file://c:/Documents.MyReport.doc";
string pattern = "FILE://";

Console.WriteLine("Culture-sensitive matching ({0} culture)...", 
                  Thread.CurrentThread.CurrentCulture.Name);
if (Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("URLs that access files are not allowed.");      
else
   Console.WriteLine("Access to {0} is allowed.", input);

Thread.CurrentThread.CurrentCulture = defaultCulture;
// The example displays the following output:
//       Culture-sensitive matching (tr-TR culture)...
//       Access to file://c:/Documents.MyReport.doc is allowed.
```

```vb
Dim defaultCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")

Dim input As String = "file://c:/Documents.MyReport.doc"
Dim pattern As String = "$FILE://"

Console.WriteLine("Culture-sensitive matching ({0} culture)...", _
                  Thread.CurrentThread.CurrentCulture.Name)
If Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase) Then
   Console.WriteLine("URLs that access files are not allowed.")      
Else
   Console.WriteLine("Access to {0} is allowed.", input)
End If

Thread.CurrentThread.CurrentCulture = defaultCulture
' The example displays the following output:
'       Culture-sensitive matching (tr-TR culture)...
'       Access to file://c:/Documents.MyReport.doc is allowed.
```

> [!NOTE]
>   Para obter mais informações sobre comparações de cadeias de caracteres que diferenciam maiúsculas de minúsculas e usam cultura invariável, consulte [Práticas recomendadas para o uso de cadeias de caracteres](best-practices.md).
 
Em vez de usar comparações que não diferenciam maiúsculas de minúsculas da cultura atual, é possível especificar a opção [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) para ignorar diferenças culturais no idioma e usar as convenções da cultura invariável.

> [!NOTE]
> A comparação usando cultura invariável está disponível apenas fornecendo o valor [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) para o parâmetro options de um construtor de classe [Regex](xref:System.Text.RegularExpressions.Regex) ou método de correspondência padrão estático. Não está disponível como uma opção embutida. 
 
O exemplo a seguir é idêntico ao anterior, exceto pelo fato de o método estático [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) ser chamado com opções que incluem [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant). Mesmo quando a cultura atual é definida como turco (Turquia), o mecanismo de expressões regulares consegue corresponder com sucesso “FILE” e “file” e bloquear o acesso ao recurso do arquivo. 

```csharp
CultureInfo defaultCulture = Thread.CurrentThread.CurrentCulture;
Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");

string input = "file://c:/Documents.MyReport.doc";
string pattern = "FILE://";

Console.WriteLine("Culture-insensitive matching...");
if (Regex.IsMatch(input, pattern, 
                  RegexOptions.IgnoreCase | RegexOptions.CultureInvariant)) 
   Console.WriteLine("URLs that access files are not allowed.");
else
   Console.WriteLine("Access to {0} is allowed.", input);

Thread.CurrentThread.CurrentCulture = defaultCulture;
// The example displays the following output:
//       Culture-insensitive matching...
//       URLs that access files are not allowed.
```

```vb
Dim defaultCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")

Dim input As String = "file://c:/Documents.MyReport.doc"
Dim pattern As String = "$FILE://"

Console.WriteLine("Culture-insensitive matching...")
If Regex.IsMatch(input, pattern, _
               RegexOptions.IgnoreCase Or RegexOptions.CultureInvariant) Then
   Console.WriteLine("URLs that access files are not allowed.")      
Else
   Console.WriteLine("Access to {0} is allowed.", input)
End If
Thread.CurrentThread.CurrentCulture = defaultCulture
' The example displays the following output:
'        Culture-insensitive matching...
'        URLs that access files are not allowed.
```

## <a name="see-also"></a>Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)




<!--HONumber=Nov16_HO4-->


