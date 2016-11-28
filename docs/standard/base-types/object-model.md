---
title: "O modelo de objeto de expressão regular"
description: "O modelo de objeto de expressão regular"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a1e611ec-c6a2-48c6-9c52-0ed845787621
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: becfe2624ad1ee1d03707ef48c780f518eb8eb28

---

# <a name="the-regular-expression-object-model"></a>O modelo de objeto de expressão regular

Este tópico descreve o modelo do objeto usado ao trabalhar com expressões regulares do .NET. Ele contém as seguintes seções:

* [O mecanismo de expressões regulares](#the-regular-expression-engine)

* [Os objetos MatchCollection e Match](#the-matchcollection-and-match-objects)

* [A coleção de Grupo](#the-group-collection)

* [O grupo capturado](#the-captured-group)

* [A coleção de captura](#the-capture-collection)

* [A captura individual](#the-individual-capture)

## <a name="the-regular-expression-engine"></a>O mecanismo de expressões regulares

O mecanismo de expressões regulares no .NET é representada pela classe [Regex](xref:System.Text.RegularExpressions.Regex). O mecanismo de expressões regulares é responsável por analisar e compilar uma expressão regular e realizar operações que correspondem ao padrão da expressão regular com uma cadeia de caracteres de entrada. O mecanismo é o componente central no modelo do objeto da expressão regular do .NET.

Você pode usar o mecanismo de expressões regulares de duas maneiras:

* Chamando os métodos estáticos da classe [Regex](xref:System.Text.RegularExpressions.Regex). Os parâmetros do método incluem a cadeia de caracteres de entrada e o padrão da expressão regular. O mecanismo de expressões regulares armazena em cache expressões regulares que são usadas em chamadas de método estático; por isso, chamadas repetidas a métodos de expressão regular estáticos que usam a mesma expressão regular oferecem um desempenho relativamente bom.

* Ao instanciar um objeto [Regex](xref:System.Text.RegularExpressions.Regex), transmitindo uma expressão regular ao construtor da classe. Nesse caso, o objeto [Regex](xref:System.Text.RegularExpressions.Regex) é imutável (somente leitura) e representa um mecanismo de expressões regulares que está ligado rigorosamente a uma única expressão regular. Como as expressões regulares usadas por instâncias Regex não são armazenadas em cache, você não deve instanciar um objeto [Regex](xref:System.Text.RegularExpressions.Regex) várias vezes com a mesma expressão regular.

É possível chamar os métodos da classe [Regex](xref:System.Text.RegularExpressions.Regex) para realizar as seguintes operações: 

* Determinar se uma cadeia de caracteres corresponde a um padrão de expressão regular.

* Extrair uma única correspondência ou a primeira correspondência.

* Extrair todas as correspondências.

* Substituir uma subcadeia de caracteres correspondida.

* Dividir uma cadeia única em uma matriz de cadeias de caracteres.

Essas operações são descritas nas seções a seguir.

### <a name="matching-a-regular-expression-pattern"></a>Correspondendo a um padrão de expressão regular

O método [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) retorna `true` se a cadeia de caracteres corresponder ao padrão ou `false` se não corresponder. Geralmente, o método [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) é usado para validar a entrada da cadeia de caracteres. Por exemplo, o código a seguir assegura que uma cadeia de caracteres corresponda a um número do cadastro de pessoas físicas válido nos Estados Unidos.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] values = { "111-22-3333", "111-2-3333"};
      string pattern = @"^\d{3}-\d{2}-\d{4}$";
      foreach (string value in values) {
         if (Regex.IsMatch(value, pattern))
            Console.WriteLine("{0} is a valid SSN.", value);
         else   
            Console.WriteLine("{0}: Invalid", value);
      }
   }
}
// The example displays the following output:
//       111-22-3333 is a valid SSN.
//       111-2-3333: Invalid
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim values() As String = { "111-22-3333", "111-2-3333"}
      Dim pattern As String = "^\d{3}-\d{2}-\d{4}$"
      For Each value As String In values
         If Regex.IsMatch(value, pattern) Then
            Console.WriteLine("{0} is a valid SSN.", value)
         Else   
            Console.WriteLine("{0}: Invalid", value)
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       111-22-3333 is a valid SSN.
'       111-2-3333: Invalid
```

O padrão da expressão regular `^\d{3}-\d{2}-\d{4}$` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`^` | Corresponder ao início da cadeia de caracteres de entrada.
`\d{3}` | Corresponder a três dígitos decimais.
`-` | Corresponder a um hífen.
`\d{2}` | Corresponde a dois dígitos decimais.
`-` | Corresponder a um hífen.
`\d{4}` | Corresponder a quatro dígitos decimais.
`$` | Corresponder ao final da cadeia de caracteres de entrada.
 
### <a name="extracting-a-single-match-or-the-first-match"></a>Extraindo uma única correspondência ou a primeira correspondência

O método [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) retorna um objeto [Match](xref:System.Text.RegularExpressions.Match) que contém informações sobre a primeira subcadeia de caracteres que corresponde a um padrão de expressão regular. Se a propriedade `Match.Success` for retornada `true`, indicando que uma correspondência foi localizada, você pode recuperar informações sobre correspondências subsequentes chamando o método [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch). Essas chamadas de método podem continuar até que a propriedade `Match.Success` retorne `false`. Por exemplo, o código a seguir usa o método [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) para localizar a primeira ocorrência de uma palavra duplicada em uma cadeia de caracteres. Em seguida, ele chama o método [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) para encontrar ocorrências adicionais. O exemplo examina a propriedade `Match.Success` após cada chamada de método para determinar se a correspondência atual foi bem-sucedida e se uma chamada para o método [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) deve seguir.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is a a farm that that raises dairy cattle."; 
      string pattern = @"\b(\w+)\W+(\1)\b";
      Match match = Regex.Match(input, pattern);
      while (match.Success)
      {
         Console.WriteLine("Duplicate '{0}' found at position {1}.",  
                           match.Groups[1].Value, match.Groups[2].Index);
         match = match.NextMatch();
      }                       
   }
}
// The example displays the following output:
//       Duplicate 'a' found at position 10.
//       Duplicate 'that' found at position 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is a a farm that that raises dairy cattle." 
      Dim pattern As String = "\b(\w+)\W+(\1)\b"
      Dim match As Match = Regex.Match(input, pattern)
      Do While match.Success
         Console.WriteLine("Duplicate '{0}' found at position {1}.", _ 
                           match.Groups(1).Value, match.Groups(2).Index)
         match = match.NextMatch()
      Loop                       
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'a' found at position 10.
'       Duplicate 'that' found at position 22.
```

O padrão da expressão regular `\b(\w+)\W+(\1)\b` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Começa a correspondência em um limite de palavra.
`(\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. Este é o primeiro grupo de captura.
`\W+` | Estabeleça a correspondência com um ou mais caracteres que não compõem palavras.
`(\1)` | Corresponder à primeira cadeia capturada. Este é o segundo grupo de captura. 
`\b` | Termina a correspondência em um limite de palavra.
 
### <a name="extracting-all-matches"></a>Extraindo todas as correspondências

O método [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) retorna um objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) que contém informações sobre todas as correspondências que o mecanismo de expressões regulares localizou na cadeia de caracteres de entrada. Por exemplo, o exemplo anterior poderia ser regravado para chamar o método [Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) ao invés dos métodos [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) e [NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is a a farm that that raises dairy cattle."; 
      string pattern = @"\b(\w+)\W+(\1)\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Duplicate '{0}' found at position {1}.",  
                           match.Groups[1].Value, match.Groups[2].Index);
   }
}
// The example displays the following output:
//       Duplicate 'a' found at position 10.
//       Duplicate 'that' found at position 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is a a farm that that raises dairy cattle." 
      Dim pattern As String = "\b(\w+)\W+(\1)\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Duplicate '{0}' found at position {1}.", _ 
                           match.Groups(1).Value, match.Groups(2).Index)
      Next                       
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'a' found at position 10.
'       Duplicate 'that' found at position 22.
```

### <a name="replacing-a-matched-substring"></a>Substituindo uma subcadeia de caracteres correspondida

O método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) substitui cada subcadeia de caracteres que corresponde ao padrão da expressão regular com uma cadeia de caracteres ou padrão de expressão regular especificado e retorna a cadeia de caracteres de entrada inteira com as substituições. Por exemplo, o código a seguir adiciona um símbolo de moeda dos Estados Unidos antes de um número decimal em uma cadeia de caracteres.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\d+\.\d{2}\b";
      string replacement = "$$$&"; 
      string input = "Total Cost: 103.64";
      Console.WriteLine(Regex.Replace(input, pattern, replacement));     
   }
}
// The example displays the following output:
//       Total Cost: $103.64
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\d+\.\d{2}\b"
      Dim replacement As String = "$$$&" 
      Dim input As String = "Total Cost: 103.64"
      Console.WriteLine(Regex.Replace(input, pattern, replacement))     
   End Sub
End Module
' The example displays the following output:
'       Total Cost: $103.64
```

O padrão da expressão regular `\b\d+\.\d{2}\b` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\b` | Começar a correspondência em um limite de palavra.
`\d+` | Corresponde a um ou mais dígitos decimais.
`\.` | Corresponde a um ponto final.
`\d{2}` | Corresponde a dois dígitos decimais.
`\b` | Termina a correspondência em um limite de palavra.
 
O padrão de substituição `$$$&` é interpretado conforme a tabela a seguir.

Padrão | Cadeia de caracteres de substituição
------- | ------------------ 
`$$` | O caractere de cifrão (**$**).
`$&` | A subcadeia de caracteres correspondida inteira.
 
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Dividindo uma cadeia de caracteres única em uma matriz de cadeias de caracteres

O método [Regex.Split](xref:System.Text.RegularExpressions.Regex.Split(System.String)) divide a cadeia de caracteres de entrada nas posições definidas por uma correspondência de expressão regular. Por exemplo, o código a seguir coloca os itens em uma lista numerada em uma matriz de cadeia de caracteres.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "1. Eggs 2. Bread 3. Milk 4. Coffee 5. Tea";
      string pattern = @"\b\d{1,2}\.\s";
      foreach (string item in Regex.Split(input, pattern))
      {
         if (! String.IsNullOrEmpty(item))
            Console.WriteLine(item);
      }      
   }
}
// The example displays the following output:
//       Eggs
//       Bread
//       Milk
//       Coffee
//       Tea
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "1. Eggs 2. Bread 3. Milk 4. Coffee 5. Tea"
      Dim pattern As String = "\b\d{1,2}\.\s"
      For Each item As String In Regex.Split(input, pattern)
         If Not String.IsNullOrEmpty(item) Then
            Console.WriteLine(item)
         End If
      Next      
   End Sub
End Module
' The example displays the following output:
'       Eggs
'       Bread
'       Milk
'       Coffee
'       Tea
```

O padrão da expressão regular `\b\d{1,2}\.\s` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começar a correspondência em um limite de palavra.
`\d{1,2}` | Corresponder a um ou dois dígitos decimais.
`\.` | Corresponde a um ponto final.
`\s` | Corresponde a um caractere de espaço em branco.
 
## <a name="the-matchcollection-and-match-objects"></a>Os objetos MatchCollection e Match

Métodos [Regex](xref:System.Text.RegularExpressions.Regex) retornam dois objetos que fazem parte do modelo de objeto de expressão regular: os objetos [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) e [Match](xref:System.Text.RegularExpressions.Match). 

### <a name="the-match-collection"></a>A coleção Match

O método [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) retorna um objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) que contém objetos [Match](xref:System.Text.RegularExpressions.Match) que representam todas as correspondências localizadas pelo mecanismo de expressões regulares na ordem em que elas ocorrem na cadeia de caracteres de entrada. Caso não haja correspondências, o método retorna um objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) que contém um objeto  [Match](xref:System.Text.RegularExpressions.Match) sem membros. A propriedade [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) `Item` permite que você acesse membros individuais da coleção por índice, de zero a um valor uma vez menor do que o valor da propriedade [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count). 'Item' é o indexador da coleção (no C#) e a propriedade padrão (no Visual Basic).

Por padrão, a chamada para o método [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) usa a avaliação lenta para preencher o objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection). O acesso a propriedades que requerem uma coleção completamente preenchida, como as propriedades [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) e `Item`, pode envolver uma penalização de desempenho. Como resultado, recomendamos que você acesse a coleção usando o objeto [IEnumerator](xref:System.Collections.IEnumerator) retornado pelo método [MatchCollection.GetEnumerator](xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator). Linguagens individuais fornecem constructos, como `foreach` no C# e 'For Each' no Visual Basic, o que encapsula a interface IEnumerator](xref:System.Collections.IEnumerator) da coleção.

O exemplo a seguir usa o método [Regex.Matches(String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) para preencher um objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) com todas as correspondências localizadas em uma cadeia de caracteres de entrada. O exemplo enumera a coleção, copia as correspondências para uma matriz de cadeia de caracteres e registra as posições dos caracteres em uma matriz de inteiros.

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
       MatchCollection matches;
       List<string> results = new List<string>();
       List<int> matchposition = new List<int>();

       // Create a new Regex object and define the regular expression.
       Regex r = new Regex("abc");
       // Use the Matches method to find all matches in the input string.
       matches = r.Matches("123abc4abcd");
       // Enumerate the collection to retrieve all matches and positions.
       foreach (Match match in matches)
       {
          // Add the match string to the string array.
           results.Add(match.Value);
           // Record the character position where the match was found.
           matchposition.Add(match.Index);
       }
       // List the results.
       for (int ctr = 0; ctr < results.Count; ctr++)
         Console.WriteLine("'{0}' found at position {1}.", 
                           results[ctr], matchposition[ctr]);  
   }
}
// The example displays the following output:
//       'abc' found at position 3.
//       'abc' found at position 7.
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
       Dim matches As MatchCollection
       Dim results As New List(Of String)
       Dim matchposition As New List(Of Integer)

       ' Create a new Regex object and define the regular expression.
       Dim r As New Regex("abc")
       ' Use the Matches method to find all matches in the input string.
       matches = r.Matches("123abc4abcd")
       ' Enumerate the collection to retrieve all matches and positions.
       For Each match As Match In matches
          ' Add the match string to the string array.
           results.Add(match.Value)
           ' Record the character position where the match was found.
           matchposition.Add(match.Index)
       Next
       ' List the results.
       For ctr As Integer = 0 To results.Count - 1
         Console.WriteLine("'{0}' found at position {1}.", _
                           results(ctr), matchposition(ctr))  
       Next
   End Sub
End Module
' The example displays the following output:
'       'abc' found at position 3.
'       'abc' found at position 7.
```

### <a name="the-match"></a>A correspondência

A classe [Match](xref:System.Text.RegularExpressions.Match) representa o resultado de uma única correspondência de expressão regular. É possível acessar objetos [Match](xref:System.Text.RegularExpressions.Match) de duas formas:

* Recuperando-os do objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) que é retornado pelo método Regex.Matches. Para recuperar objetos [Match](xref:System.Text.RegularExpressions.Match) individuais, itere a coleção usando um constructo `foreach` (no C#) ou `For Each...Next` (no Visual Basic) ou use a propriedade [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) `Item` para recuperar um objeto [Match](xref:System.Text.RegularExpressions.Match) específico por índice ou por nome. Também é possível recuperar objetos [Match](xref:System.Text.RegularExpressions.Match) individuais da coleção iterando-a por índice, de zero a um valor uma vez menor do que o número de objetos na coleção. Entretanto, esse método não utiliza a avaliação lenta, pois acessa a propriedade [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count). 

  O exemplo a seguir recupera objetos [Match](xref:System.Text.RegularExpressions.Match) individuais de um objeto [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) ao iterar a solução usando o constructo `foreach`. A expressão regular simplesmente corresponde a cadeia de caracteres “abc” na cadeia de caracteres de entrada.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "abc";
        string input = "abc123abc456abc789";
        foreach (Match match in Regex.Matches(input, pattern))
           Console.WriteLine("{0} found at position {1}.", 
                             match.Value, match.Index);
     }
  }
  // The example displays the following output:
  //       abc found at position 0.
  //       abc found at position 6.
  //       abc found at position 12.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "abc"
        Dim input As String = "abc123abc456abc789"
        For Each match As Match In Regex.Matches(input, pattern)
           Console.WriteLine("{0} found at position {1}.", _
                             match.Value, match.Index)
        Next                     
     End Sub
  End Module
  ' The example displays the following output:
  '       abc found at position 0.
  '       abc found at position 6.
  '       abc found at position 12.
  ```

* Ao chamar o método [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)), que retorna um objeto [Match](xref:System.Text.RegularExpressions.Match) que representa a primeira correspondência em uma cadeia de caracteres ou parte de uma cadeia. É possível determinar se a correspondência foi localizada recuperando o valor da propriedade `Match.Success`. Para recuperar objetos [Match](xref:System.Text.RegularExpressions.Match) que representam correspondências subsequentes, chame o método [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) repetidas vezes até que a propriedade `Success` do objeto [Match](xref:System.Text.RegularExpressions.Match) retornado seja `false`. 

  O exemplo a seguir usa os métodos [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) e [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) para corresponder à cadeia de caracteres “abc” na cadeia de caracteres de entrada.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "abc";
        string input = "abc123abc456abc789";
        Match match = Regex.Match(input, pattern);
        while (match.Success)
        {
           Console.WriteLine("{0} found at position {1}.", 
                             match.Value, match.Index);
           match = match.NextMatch();                  
        }                     
     }
  }
  // The example displays the following output:
  //       abc found at position 0.
  //       abc found at position 6.
  //       abc found at position 12.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "abc"
        Dim input As String = "abc123abc456abc789"
        Dim match As Match = Regex.Match(input, pattern)
        Do While match.Success
           Console.WriteLine("{0} found at position {1}.", _
                             match.Value, match.Index)
           match = match.NextMatch()                  
        Loop                     
     End Sub
  End Module
  ' The example displays the following output:
  '       abc found at position 0.
  '       abc found at position 6.
  '       abc found at position 12.
  ```

Duas propriedades da classe [Match](xref:System.Text.RegularExpressions.Match) retornam objetos de coleção:

* A propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) retorna um objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) que contém informações sobre as subcadeias de caracteres que correspondem a grupos de captura no padrão de expressão regular. 

* A propriedade `Match.Captures` retorna um objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) de uso limitado. A coleção não é preenchida para um objeto [Match](xref:System.Text.RegularExpressions.Match) cuja propriedade `Success` é `false`. Caso contrário, ela contém um único objeto [Capture](xref:System.Text.RegularExpressions.Capture) que tem as mesmas informações do objeto [Match](xref:System.Text.RegularExpressions.Match). 

Para obter mais informações sobre esses objetos, consulte as seções [A coleção de Grupo](#the-group-collection) e [A coleção de captura](#the-capture-collection) mais adiante neste tópico.

Duas propriedades adicionais da classe [Match](xref:System.Text.RegularExpressions.Match) oferecem informações sobre a correspondência. A propriedade `Match.Value` retorna a subcadeia na cadeia de caracteres de entrada que corresponde ao padrão de expressão regular. A propriedade `Match.Index` retorna a posição inicial baseada em zero da cadeia correspondida na cadeia de caracteres de entrada.

A classe [Match](xref:System.Text.RegularExpressions.Match) também tem dois métodos de correspondência de padrões:

* O método [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) localiza a correspondência após a correspondência representada pelo objeto [Match](xref:System.Text.RegularExpressions.Match) atual e retorna um objeto [Match](xref:System.Text.RegularExpressions.Match) que representa essa correspondência.

* O método [Match.Result](xref:System.Text.RegularExpressions.Match.NextMatch) realiza uma operação de substituição especificada na cadeia de caracteres correspondida e retorna o resultado. 


O exemplo a seguir usa o método [Match.Result](xref:System.Text.RegularExpressions.Match.NextMatch) para inserir um símbolo **$** e um espaço antes de cada número que inclua dois dígitos fracionários. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\d+(,\d{3})*\.\d{2}\b";
      string input = "16.32\n194.03\n1,903,672.08"; 

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Result("$$ $&"));
   }
}
// The example displays the following output:
//       $ 16.32
//       $ 194.03
//       $ 1,903,672.08
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\d+(,\d{3})*\.\d{2}\b"
      Dim input As String = "16.32" + vbCrLf + "194.03" + vbCrLf + "1,903,672.08" 

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Result("$$ $&"))
      Next
   End Sub
End Module
' The example displays the following output:
'       $ 16.32
'       $ 194.03
'       $ 1,903,672.08
```

O padrão de expressão regular `\b\d+(,\d{3})*\.\d{2}\b` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começar a correspondência em um limite de palavra.
`\d+` | Corresponde a um ou mais dígitos decimais.
`(,\d{3})*` | Corresponder a zero ou mais ocorrências de uma vírgula seguida por três dígitos decimais.
`\.` | Corresponder ao caractere de vírgula decimal.
`\d{2} | Corresponde a dois dígitos decimais.
`\b` | Termina a correspondência em um limite de palavra.
 
O padrão de substituição **$$ $&** indica que a subcadeia de caracteres correspondida deve ser substituída por um símbolo de cifrão (**$**) (o padrão `$$`), um espaço e o valor da correspondência (o padrão `$&`).

## <a name="the-group-collection"></a>A coleção de Grupo

A propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) retorna um objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) que contém objetos [Group](xref:System.Text.RegularExpressions.Group) que representam grupos capturados em uma única correspondência. O primeiro objeto [Group](xref:System.Text.RegularExpressions.Group) na coleção (no índice 0) representa a correspondência inteira. Cada objeto que se segue representa os resultados de um único grupo de captura. 

É possível recuperar objetos [Group](xref:System.Text.RegularExpressions.Group) individuais na coleção usando a propriedade [GroupCollection.Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)). É possível recuperar grupos não nomeados por sua posição ordinal na coleção e recuperar grupos nomeados por nome ou posição ordinal. Capturas não nomeadas aparecem primeiro na coleção e são indexadas da esquerda para a direita na ordem na qual aparecem no padrão de expressão regular. Capturas nomeadas são indexadas após as capturas não nomeadas, da esquerda para a direita, na ordem em que aparecem no padrão de expressão regular. Para determinar quais grupos numerados estão disponíveis na coleção retornada para um método específico de correspondência de expressão regular, você pode chamar o método da instância [Regex.GetGroupNumbers](xref:System.Text.RegularExpressions.Regex.GetGroupNumbers). Para determinar quais grupos nomeados estão disponíveis na coleção, você pode chamar o método da instância R[Regex.GetGroupNames](xref:System.Text.RegularExpressions.Regex.GetGroupNames). Os dois métodos são especificamente úteis em rotinas gerais que analisam as correspondências encontradas por qualquer expressão regular. 

A propriedade [GroupCollection.Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) é o indexador da coleção no C# e a propriedade padrão do objeto da coleção no Visual Basic. Isso significa que objetos [Group](xref:System.Text.RegularExpressions.Group) individuais podem ser acessados por índice (ou por nome, no caso de grupos nomeados), como a seguir: 

```csharp
Group group = match.Groups[ctr];
```

```vb
Dim group As Group = match.Groups(ctr)
```

O exemplo a seguir define uma expressão regular que usa constructos de agrupamento para capturar o mês, o dia e o ano de uma data. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)\s(\d{1,2}),\s(\d{4})\b";
      string input = "Born: July 28, 1989";
      Match match = Regex.Match(input, pattern);
      if (match.Success)
         for (int ctr = 0; ctr <  match.Groups.Count; ctr++)
            Console.WriteLine("Group {0}: {1}", ctr, match.Groups[ctr].Value);
    }
}
// The example displays the following output:
//       Group 0: July 28, 1989
//       Group 1: July
//       Group 2: 28
//       Group 3: 1989
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)\s(\d{1,2}),\s(\d{4})\b"
      Dim input As String = "Born: July 28, 1989"
      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         For ctr As Integer = 0 To match.Groups.Count - 1
            Console.WriteLine("Group {0}: {1}", ctr, match.Groups(ctr).Value)
         Next      
      End If   
   End Sub
End Module
' The example displays the following output:
'       Group 0: July 28, 1989
'       Group 1: July
'       Group 2: 28
'       Group 3: 1989
```

O padrão de expressão regular `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começa a correspondência em um limite de palavra.
`(\w+)` | Corresponde a um ou mais caracteres de palavra. Este é o primeiro grupo de captura.
`\s` | Corresponde a um caractere de espaço em branco.
`(\d{1,2})` | Corresponder a um ou dois dígitos decimais. Este é o segundo grupo de captura.
`,` | Corresponde a uma vírgula.
`\s` | Corresponde a um caractere de espaço em branco.
`(\d{4})` | Corresponder a quatro dígitos decimais. Este é o terceiro grupo de captura.
`\b` | Termina a correspondência em um limite de palavra.
 
## <a name="the-captured-group"></a>O grupo capturado

A classe [Group](xref:System.Text.RegularExpressions.Group) representa o resultado de um único grupo de captura. Os objetos [Group](xref:System.Text.RegularExpressions.Group) que representam os grupos de captura definidos em uma expressão regular são retornados pela propriedade [Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) do objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups). A propriedade [Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) é o indexador (no C#) e a propriedade padrão (no Visual Basic) da classe [Group](xref:System.Text.RegularExpressions.Group). Também é possível recuperar membros individuais iterando a coleção usando o constructo `foreach`. Para ver um exemplo, consulte a seção anterior.

O exemplo a seguir usa constructos de agrupamento aninhados para capturar subcadeias de caracteres em grupos. O padrão de expressão regular `(a(b))c` corresponde à cadeia de caracteres “abc”. Ele atribui a subcadeia “ab” ao primeiro grupo de captura e a subcadeia de caracteres “b” ao segundo grupo de captura.

```csharp
List<int> matchposition = new List<int>();
List<string> results = new List<string>();
// Define substrings abc, ab, b.
Regex r = new Regex("(a(b))c"); 
Match m = r.Match("abdabc");
for (int i = 0; m.Groups[i].Value != ""; i++) 
{
   // Add groups to string array.
   results.Add(m.Groups[i].Value); 
   // Record character position.
   matchposition.Add(m.Groups[i].Index); 
}

// Display the capture groups.
for (int ctr = 0; ctr < results.Count; ctr++)
   Console.WriteLine("{0} at position {1}", 
                     results[ctr], matchposition[ctr]);
// The example displays the following output:
//       abc at position 3
//       ab at position 3
//       b at position 4
```

```vb
Dim matchposition As New List(Of Integer)
 Dim results As New List(Of String)
 ' Define substrings abc, ab, b.
 Dim r As New Regex("(a(b))c") 
 Dim m As Match = r.Match("abdabc")
 Dim i As Integer = 0
 While Not (m.Groups(i).Value = "")    
    ' Add groups to string array.
    results.Add(m.Groups(i).Value)     
    ' Record character position. 
    matchposition.Add(m.Groups(i).Index) 
     i += 1
 End While

 ' Display the capture groups.
 For ctr As Integer = 0 to results.Count - 1
    Console.WriteLine("{0} at position {1}", _ 
                      results(ctr), matchposition(ctr))
 Next                     
' The example displays the following output:
'       abc at position 3
'       ab at position 3
'       b at position 4
```

O exemplo a seguir usa constructos de agrupamento nomeados para capturar subcadeias de caracteres de uma cadeia que contém dados no formato “DATANAME:VALUE”, que a expressão regular divide usando dois pontos (:).

```csharp
Regex r = new Regex("^(?<name>\\w+):(?<value>\\w+)");
Match m = r.Match("Section1:119900");
Console.WriteLine(m.Groups["name"].Value);
Console.WriteLine(m.Groups["value"].Value);
// The example displays the following output:
//       Section1
//       119900
```

```vb
Dim r As New Regex("^(?<name>\w+):(?<value>\w+)")
Dim m As Match = r.Match("Section1:119900")
Console.WriteLine(m.Groups("name").Value)
Console.WriteLine(m.Groups("value").Value)
' The example displays the following output:
'       Section1
'       119900
```

O padrão de expressão regular `^(?<name>\w+):(?<value>\w+)` é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`^` | Começar a correspondência no início da cadeia de caracteres de entrada.
`(?<name>\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. O nome deste grupo de captura é nome.
`:` | Corresponder a dois pontos.
`(?<value>\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. O nome deste grupo de captura é valor.
 
As propriedades da classe [Group](xref:System.Text.RegularExpressions.Group) fornecem informações sobre o grupo capturado: a propriedade `Group.Value` contém a subcadeia de caracteres capturada, a propriedade `Group.Index` indica a posição inicial do grupo capturado no texto de entrada, a propriedade `Group.Length` contém o comprimento do texto capturado e a propriedade `Group.Success` indica se uma subcadeia de caracteres corresponde ao padrão definido pelo grupo de captura.

Aplicar quantificadores a um grupo (para obter mais informações, consulte [Quantificadores em expressões regulares](quantifiers.md)) modifica a relação de uma captura por grupo de captura de duas formas:

* Se o quantificador __*__ ou __*?__ (que especifica zero ou mais correspondências) for aplicado a um grupo, um grupo de captura pode não ter uma correspondência na cadeia de caracteres de entrada. Quando não há texto capturado, as propriedades do objeto [Group](xref:System.Text.RegularExpressions.Group) são definidas como mostrado na tabela a seguir.

  Propriedade do grupo | Valor
  -------------- | ----- 
  `Success` | `false`
  `Value` | [String.Empty](xref:System.String.Empty) 
  `Length` | 0
 
  O exemplo a seguir fornece uma ilustração. No padrão de expressão regular `aaa(bbb)*ccc`, o primeiro grupo de captura (a subcadeia de caracteres “bbb”) pode ser correspondido a zero ou mais vezes. Como a cadeia de caracteres de entrada “aaaccc” corresponde ao padrão, o grupo de captura não tem correspondência.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "aaa(bbb)*ccc";
        string input = "aaaccc";
        Match match = Regex.Match(input, pattern);
        Console.WriteLine("Match value: {0}", match.Value);
        if (match.Groups[1].Success)
           Console.WriteLine("Group 1 value: {0}", match.Groups[1].Value);
        else
           Console.WriteLine("The first capturing group has no match.");
     }
  }
  // The example displays the following output:
  //       Match value: aaaccc
  //       The first capturing group has no match.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "aaa(bbb)*ccc"
        Dim input As String = "aaaccc"
        Dim match As Match = Regex.Match(input, pattern)
        Console.WriteLine("Match value: {0}", match.Value)
        If match.Groups(1).Success Then
           Console.WriteLine("Group 1 value: {0}", match.Groups(1).Value)
        Else
           Console.WriteLine("The first capturing group has no match.")
       End If   
     End Sub
  End Module
  ' The example displays the following output:
  '       Match value: aaaccc
  '       The first capturing group has no match.
  ```

* Os quantificadores podem corresponder a diversas ocorrências de um padrão que é definido por um grupo de captura. Nesse caso, as propriedades `Value` e `Length` de um objeto [Group](xref:System.Text.RegularExpressions.Group) contêm informações somente sobre a última subcadeia de caracteres capturada. Por exemplo, a seguinte expressão regular corresponde a uma única sentença que termina com um ponto. Ela utiliza dois constructos de agrupamento: o primeiro captura palavras individuais, juntamente com um caractere de espaço em branco; o segundo captura palavras individuais. Como a saída do exemplo mostra, embora a expressão regular tenha sucesso ao capturar uma sequência inteira, o segundo grupo de captura só captura a última palavra.

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = @"\b((\w+)\s?)+\.";
        string input = "This is a sentence. This is another sentence.";
        Match match = Regex.Match(input, pattern);
        if (match.Success)
        {
           Console.WriteLine("Match: " + match.Value);
           Console.WriteLine("Group 2: " + match.Groups[2].Value);
        }   
     }
  }
  // The example displays the following output:
  //       Match: This is a sentence.
  //       Group 2: sentence
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "\b((\w+)\s?)+\."
        Dim input As String = "This is a sentence. This is another sentence."
        Dim match As Match = Regex.Match(input, pattern)
        If match.Success Then
           Console.WriteLine("Match: " + match.Value)
           Console.WriteLine("Group 2: " + match.Groups(2).Value)
        End If   
     End Sub
  End Module
  ' The example displays the following output:
  '       Match: This is a sentence.
  '       Group 2: sentence
  ```

## <a name="the-capture-collection"></a>A coleção de captura

O objeto [Group](xref:System.Text.RegularExpressions.Group) contém informações somente sobre a última captura. No entanto, o conjunto inteiro de capturas realizadas por um grupo de captura ainda estará disponível no objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) que é retornado pela propriedade [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures). Cada membro da coleção é um objeto [Capture](xref:System.Text.RegularExpressions.Capture) que representa uma captura realizada por esse grupo de captura, na ordem na qual elas foram capturadas (e, portanto, na ordem em que as cadeias capturadas foram correspondidas da esquerda para a direita na cadeia de caracteres de entrada). Você pode recuperar objetos [Capture](xref:System.Text.RegularExpressions.Capture) individuais na coleção de duas formas: 

* Ao iterar pela coleção usando um constructo como `foreach` (no C#) ou `For Each` (no Visual Basic).

* Ao usar a propriedade [CaptureCollection.Item](xref:System.Text.RegularExpressions.CaptureCollection.Item(System.Int32)) para recuperar um objeto específico por índice. A propriedade do Item é a propriedade padrão [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) do objeto (no Visual Basic) ou o indexador (no C#).


Se um quantificador não for aplicado a um grupo de captura, o objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) conterá um único objeto [Capture](xref:System.Text.RegularExpressions.Capture) de pouco interesse, pois ele fornece informações sobre a mesma correspondência que seu objeto [Group](xref:System.Text.RegularExpressions.Group). Se um quantificador for aplicado a um grupo de captura, o objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) conterá todas as capturas realizadas pelo grupo de captura e o último membro da coleção representará a mesma captura que o objeto [Group](xref:System.Text.RegularExpressions.Group). 

Por exemplo, se você usar o padrão de expressão regular `((a(b))c)+` (em que o quantificador `+` especifica uma ou mais correspondências) para capturar correspondências da cadeia de caracteres “abcabcabc”, o objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) para cada objeto [Group](xref:System.Text.RegularExpressions.Group) conterá três membros.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "((a(b))c)+";
      string input = "abcabcabc";

      Match match = Regex.Match(input, pattern);
      if (match.Success)
      {
         Console.WriteLine("Match: '{0}' at position {1}",  
                           match.Value, match.Index);
         GroupCollection groups = match.Groups;
         for (int ctr = 0; ctr < groups.Count; ctr++) {
            Console.WriteLine("   Group {0}: '{1}' at position {2}", 
                              ctr, groups[ctr].Value, groups[ctr].Index);
            CaptureCollection captures = groups[ctr].Captures;
            for (int ctr2 = 0; ctr2 < captures.Count; ctr2++) {
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", 
                                 ctr2, captures[ctr2].Value, captures[ctr2].Index);
            }                     
         }
      }
   }
}
// The example displays the following output:
//       Match: 'abcabcabc' at position 0
//          Group 0: 'abcabcabc' at position 0
//             Capture 0: 'abcabcabc' at position 0
//          Group 1: 'abc' at position 6
//             Capture 0: 'abc' at position 0
//             Capture 1: 'abc' at position 3
//             Capture 2: 'abc' at position 6
//          Group 2: 'ab' at position 6
//             Capture 0: 'ab' at position 0
//             Capture 1: 'ab' at position 3
//             Capture 2: 'ab' at position 6
//          Group 3: 'b' at position 7
//             Capture 0: 'b' at position 1
//             Capture 1: 'b' at position 4
//             Capture 2: 'b' at position 7
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "((a(b))c)+"
      Dim input As STring = "abcabcabc"

      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Match: '{0}' at position {1}", _ 
                           match.Value, match.Index)
         Dim groups As GroupCollection = match.Groups
         For ctr As Integer = 0 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at position {2}", _
                              ctr, groups(ctr).Value, groups(ctr).Index)
            Dim captures As CaptureCollection = groups(ctr).Captures
            For ctr2 As Integer = 0 To captures.Count - 1
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", _
                                 ctr2, captures(ctr2).Value, captures(ctr2).Index)
            Next
         Next
      End If
   End Sub
End Module
' The example dosplays the following output:
'       Match: 'abcabcabc' at position 0
'          Group 0: 'abcabcabc' at position 0
'             Capture 0: 'abcabcabc' at position 0
'          Group 1: 'abc' at position 6
'             Capture 0: 'abc' at position 0
'             Capture 1: 'abc' at position 3
'             Capture 2: 'abc' at position 6
'          Group 2: 'ab' at position 6
'             Capture 0: 'ab' at position 0
'             Capture 1: 'ab' at position 3
'             Capture 2: 'ab' at position 6
'          Group 3: 'b' at position 7
'             Capture 0: 'b' at position 1
'             Capture 1: 'b' at position 4
'             Capture 2: 'b' at position 7
```

O exemplo a seguir usa a expressão regular `(Abc)+` para localizar uma ou mais execuções consecutivas da cadeia de caracteres “Abc” na cadeia “XYZAbcAbcAbcXYZAbcAb”. O exemplo ilustra o uso da propriedade [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) para retornar vários grupos de subcadeias de caracteres capturadas.

```csharp
{
   int counter;
   Match m;
   CaptureCollection cc;
   GroupCollection gc;

   // Look for groupings of "Abc".
   Regex r = new Regex("(Abc)+"); 
   // Define the string to search.
   m = r.Match("XYZAbcAbcAbcXYZAbcAb"); 
   gc = m.Groups;

   // Display the number of groups.
   Console.WriteLine("Captured groups = " + gc.Count.ToString());

   // Loop through each group.
   for (int i=0; i < gc.Count; i++) 
   {
      cc = gc[i].Captures;
      counter = cc.Count;

      // Display the number of captures in this group.
      Console.WriteLine("Captures count = " + counter.ToString());

      // Loop through each capture in the group.
      for (int ii = 0; ii < counter; ii++) 
      {
         // Display the capture and its position.
         Console.WriteLine(cc[ii] + "   Starts at character " + 
              cc[ii].Index);
      }
   }
}
// The example displays the following output:
//       Captured groups = 2
//       Captures count = 1
//       AbcAbcAbc   Starts at character 3
//       Captures count = 3
//       Abc   Starts at character 3
//       Abc   Starts at character 6
//       Abc   Starts at character 9  
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "((a(b))c)+"
      Dim input As STring = "abcabcabc"

      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Match: '{0}' at position {1}", _ 
                           match.Value, match.Index)
         Dim groups As GroupCollection = match.Groups
         For ctr As Integer = 0 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at position {2}", _
                              ctr, groups(ctr).Value, groups(ctr).Index)
            Dim captures As CaptureCollection = groups(ctr).Captures
            For ctr2 As Integer = 0 To captures.Count - 1
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", _
                                 ctr2, captures(ctr2).Value, captures(ctr2).Index)
            Next
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Match: 'abcabcabc' at position 0
'          Group 0: 'abcabcabc' at position 0
'             Capture 0: 'abcabcabc' at position 0
'          Group 1: 'abc' at position 6
'             Capture 0: 'abc' at position 0
'             Capture 1: 'abc' at position 3
'             Capture 2: 'abc' at position 6
'          Group 2: 'ab' at position 6
'             Capture 0: 'ab' at position 0
'             Capture 1: 'ab' at position 3
'             Capture 2: 'ab' at position 6
'          Group 3: 'b' at position 7
'             Capture 0: 'b' at position 1
'             Capture 1: 'b' at position 4
'             Capture 2: 'b' at position 7
```

## <a name="the-individual-capture"></a>A captura individual

A classe [Capture](xref:System.Text.RegularExpressions.Capture) contém os resultados de uma única captura de subexpressão. A propriedade [Capture.Value](xref:System.Text.RegularExpressions.Capture.Value) contém o texto correspondido, enquanto a propriedade [Capture.Index](xref:System.Text.RegularExpressions.Capture.Index) indica a posição baseada em zero na cadeia de caracteres de entrada na qual a subcadeia de caracteres correspondida começa. 

O exemplo a seguir analisa uma cadeia de caracteres de entrada para a temperatura das cidades escolhidas. Uma vírgula (“,”) é usada para separar uma cidade e sua temperatura, enquanto um ponto e vírgula (“;”) é usado para separar os dados de cada cidade. A cadeia de caracteres de entrada inteira representa uma única correspondência. No padrão de expressão regular `((\w+(\s\w+)*),(\d+);)+`, usado para analisar a cadeia de caracteres, o nome da cidade é atribuído ao segundo grupo de captura, enquanto a temperatura é atribuída ao quarto grupo de captura.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "Miami,78;Chicago,62;New York,67;San Francisco,59;Seattle,58;"; 
      string pattern = @"((\w+(\s\w+)*),(\d+);)+";
      Match match = Regex.Match(input, pattern);
      if (match.Success)
      {
         Console.WriteLine("Current temperatures:");
         for (int ctr = 0; ctr < match.Groups[2].Captures.Count; ctr++)
            Console.WriteLine("{0,-20} {1,3}", match.Groups[2].Captures[ctr].Value, 
                              match.Groups[4].Captures[ctr].Value);
      }
   }
}
// The example displays the following output:
//       Current temperatures:
//       Miami                 78
//       Chicago               62
//       New York              67
//       San Francisco         59
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "Miami,78;Chicago,62;New York,67;San Francisco,59;Seattle,58;" 
      Dim pattern As String = "((\w+(\s\w+)*),(\d+);)+"
      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Current temperatures:")
         For ctr As Integer = 0 To match.Groups(2).Captures.Count - 1
            Console.WriteLine("{0,-20} {1,3}", match.Groups(2).Captures(ctr).Value, _
                              match.Groups(4).Captures(ctr).Value)
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Current temperatures:
'       Miami                 78
'       Chicago               62
'       New York              67
'       San Francisco         59
```

A expressão regular é definida como mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`(\s\w+)*` | Corresponder a zero ou mais ocorrências de um caractere de espaço em branco seguido por um ou mais caracteres de palavra. Este padrão corresponde a nomes de cidade com várias palavras. Este é o terceiro grupo de captura.
`(\w+(\s\w+)*)` | Corresponder a um ou mais caracteres de palavra seguido por zero ou mais ocorrências de um caractere de espaço em branco e um ou mais caracteres de palavra. Este é o segundo grupo de captura.
`,` | Corresponde a uma vírgula.
`(\d+)` | Corresponder a um ou mais dígitos. Este é o quarto grupo de captura.
`;` | Corresponder a um ponto e vírgula.
`((\w+(\s\w+)*),(\d+);)+` | Corresponder ao padrão de uma palavra seguida por qualquer palavra adicional seguida por uma vírgula, um ou mais dígitos e um ponto e vírgula, uma ou mais vezes. Este é o primeiro grupo de captura. 
 
## <a name="see-also"></a>Consulte também

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[Expressões regulares do .NET](regular-expressions.md)

[Linguagem de expressão regular – referência rápida](quick-ref.md)




<!--HONumber=Nov16_HO4-->


