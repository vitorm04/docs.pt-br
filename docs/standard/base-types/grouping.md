---
title: "Constructos de agrupamento em expressões regulares"
description: "Constructos de agrupamento em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e0bf3718-e64b-460b-b73d-66678cec6093
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 6aa304f5c4ed400faddd3869006cdd011aa06466

---

# <a name="grouping-constructs-in-regular-expressions"></a>Constructos de agrupamento em expressões regulares

As construções de agrupamento delineiam as subexpressões de uma expressão regular e capturam a subcadeia de caracteres de uma cadeia de caracteres de entrada. Você pode usar construções de agrupamento para fazer isto:

* Fazer a correspondência de uma subexpressão que é repetida na cadeia de caracteres de entrada.

* Aplicar um quantificador a uma subexpressão com diversos elementos de linguagem de expressão regular. Para obter mais informações sobre quantificadores, consulte [Quantificadores em expressões regulares](quantifiers.md).

* Inclua uma subexpressão na cadeia de caracteres retornada pelos métodos [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) e [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)).

* Recupere subexpressões individuais da propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) e processe-as separadamente do texto correspondente como um todo.

A tabela a seguir lista as construções de agrupamento com suporte pelo mecanismo de expressões regulares .NET e indica captura ou não captura. 

Constructo de agrupamento | Captura ou não captura
------------------ | -------------------------
[Subexpressões correspondentes](#matched-subexpressions) | Capturando
[Subexpressões correspondentes nomeadas](#named-matched-subexpressions) | Capturando
[Definições de grupo de balanceamento](#balancing-group-definitions) | Capturando
[Grupos de não captura](#noncapturing-groups) | Não captura
[Opções de grupo](#group-options) | Não captura
[Asserções lookahead positivas de largura zero](#zero-width-positive-lookahead-assertions) | Não captura
[Asserções lookahead negativas de largura zero](#zero-width-negative-lookahead-assertions) | Não captura
[Asserções lookbehind positivas de largura zero](#zero-width-positive-lookbehind-assertions) | Não captura
[Asserções lookbehind negativas de largura zero](#zero-width-negative-lookbehind-assertions) | Não captura
[Subexpressões sem retrocesso](#nonbacktracking-subexpressions) | Não captura

Para saber mais sobre grupos e modelos de objetos de expressão regular, veja [Construções de agrupamento e objetos de expressão regular](#grouping-constructs-and-regular-expression-objects). 

## <a name="matched-subexpressions"></a>Subexpressões correspondentes

O constructo de agrupamento a seguir captura uma subexpressão correspondente: 

**(**_subexpression_**)**

em que *subexpression* é qualquer padrão de expressão regular válido. As capturas que usam parênteses são numeradas automaticamente, da esquerda para a direita, com base na ordem do parêntese de abertura na expressão regular, começando em um. A captura que recebe o número zero é o texto que coincide com todo o padrão da expressão regular.

> [!NOTE]
> Por padrão, o elemento da linguagem (subexpressão) captura a subexpressão correspondente. Porém, se o parâmetro RegexOptions de um padrão de expressão regular que corresponde ao método incluir o sinalizador RegexOptions.ExplicitCapture ou se a opção n for aplicada a essa subexpressão (veja Opções de grupo mais adiante neste tópico), a subexpressão correspondente não será capturada.
 
Você pode acessar os grupos capturados de quatro formas:

* Usando o constructo de referência inversa na expressão regular. A subexpressão correspondente é referenciada na mesma expressão regular usando a sintaxe **\**_number_, em que *number* é o número ordinal da subexpressão capturada.

* Usando o constructo de referência inversa nomeado na expressão regular. A subexpressão correspondente é referenciada na mesma expressão regular usando a sintaxe **\k<**_name_**>**, em que *name* é o nome de um grupo de captura ou **\k**_<number_**>**, em que *number* é o número ordinal de um grupo de captura. O grupo de captura tem um nome padrão que é idêntico a seu número ordinal. Para obter mais informações, veja Construções de agrupamento e objetos de expressão regular posteriormente neste tópico.

* Ao usar a sequência de substituição **$**_number_ em uma chamada de método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) ou [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)), em que número é o *number* ordinal da subexpressão capturada.

* Programaticamente, pelo uso do objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups). O membro na posição zero da coleção representa toda a correspondência da expressão regular. Cada membro subsequente representa uma subexpressão correspondente. Para obter mais informações, veja a seção [Construções de agrupamento e objetos de expressão regular](#grouping-constructs-and-regular-expression-objects).

O exemplo a seguir mostra uma expressão regular que identifica palavras duplicadas no texto. Os dois grupos de captura padrão da expressão regular representam as duas instâncias da palavra duplicada. A segunda instância é capturada para relatar a posição inicial na cadeia de caracteres de entrada.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\w+)\s(\1)";
      string input = "He said that that was the the correct answer.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine("Duplicate '{0}' found at positions {1} and {2}.", 
                           match.Groups[1].Value, match.Groups[1].Index, match.Groups[2].Index);
   }
}
// The example displays the following output:
//       Duplicate 'that' found at positions 8 and 13.
//       Duplicate 'the' found at positions 22 and 26.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\w+)\s(\1)\W"
      Dim input As String = "He said that that was the the correct answer."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine("Duplicate '{0}' found at positions {1} and {2}.", _
                           match.Groups(1).Value, match.Groups(1).Index, match.Groups(2).Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'that' found at positions 8 and 13.
'       Duplicate 'the' found at positions 22 and 26.
```

Este é o padrão da expressão regular:

```
(\w+)\s(\1)\W
```

A tabela a seguir mostra como o padrão da expressão regular é interpretado. 

Padrão | Descrição
------- | ----------- 
`(\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. Este é o primeiro grupo de captura.
`\s` | Corresponde a um caractere de espaço em branco.
`(\1)` | Corresponde à cadeia de caracteres no primeiro grupo capturado. Este é o segundo grupo de captura. O exemplo o atribui a um grupo capturado para que seja possível recuperar a posição inicial da palavra duplicada da propriedade `Match.Index`.
`\W` | Estabeleça a correspondência com caracteres que não compõem palavras, como espaços em branco e pontuação. Isso impede a correspondência de um padrão de expressão regular com uma expressão que começa com a palavra do primeiro grupo capturado.
 
## <a name="named-matched-subexpressions"></a>Subexpressões correspondentes nomeadas

O constructo de agrupamento a seguir captura uma subexpressão correspondente e permite acessá-la usando seu nome ou número: 

```
(?<name>subexpression)
```

ou:

```
(?'name'subexpression)
```

em que *name* é um nome de grupo válido e *subexpression* é qualquer padrão de expressão regular válido. *name* não deve conter caracteres de pontuação nem começar com um número.

> [!NOTE]
> Se o parâmetro [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) de um padrão de expressão regular que corresponde ao método incluir o sinalizador [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) ou se a opção **n** for aplicada a essa subexpressão (veja [Opções de grupo](#group-options) mais adiante neste tópico), a única forma de capturar uma subexpressão será atribuir nomes explícitos a grupos de captura.
 
Você pode acessar grupos capturados nomeados destas formas:

* Usando o constructo de referência inversa nomeado na expressão regular. A subexpressão correspondente é referenciada na mesma expressão regular usando a sintaxe **\k<**_name_**>**, em que *name* é o nome da subexpressão capturada. 

* Usando o constructo de referência inversa na expressão regular. A subexpressão correspondente é referenciada na mesma expressão regular usando a sintaxe **\**_number_, em que *number* é o número ordinal da subexpressão capturada. As subexpressões correspondentes nomeadas são numeradas em ordem de sequência, da esquerda da direita, após as subexpressões correspondentes.

* Ao usar a sequência de substituição **${**_name_**}** em uma chamada de método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) ou [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)), em que *name* é o nome da subexpressão capturada.

* Ao usar a sequência de substituição **$**_number_ em uma chamada de método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) ou [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)), em que número é o *number* ordinal da subexpressão capturada.

* Programaticamente, pelo uso do objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups). O membro na posição zero da coleção representa toda a correspondência da expressão regular. Cada membro subsequente representa uma subexpressão correspondente. Os grupos capturados nomeados são armazenados na coleção depois dos grupos capturados numerados.

* De forma programática, ao fornecer o nome da subexpressão ao indexador do objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) (no C#) ou a sua propriedade Item (no Visual Basic).

Um padrão de expressão regular simples mostra como os grupos numerados (sem nome) e nomeados podem ser usados como referência de forma programática ou usando sintaxe de linguagem de expressão regular. A expressão regular `((?<One>abc)\d+)?(?<Two>xyz)(.*)` gera os seguintes grupos de captura por número e nome. O primeiro grupo de captura (o número 0) sempre faz referência a todo o padrão.

Número | Nome | Padrão
------ | ---- | ------- 
0 | 0 (nome padrão) | `((?<One>abc)\d+)?(?<Two>xyz)(.*)`
1 | 1 (nome padrão) | `((?<One>abc)\d+)`
2 | 2 (nome padrão) | `(.*)`
3 | Um | `(?<One>abc)`
4 | Dois | `(?<Two>xyz)`
 
O exemplo a seguir mostra uma expressão regular que identifica palavras duplicadas e a palavra que aparece logo na sequência. O padrão da expressão regular define duas subexpressões nomeadas: `duplicateWord`, que representa a palavra duplicada e `nextWord`, que representa a palavra que aparece logo na sequência. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)";
      string input = "He said that that was the the correct answer.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine("A duplicate '{0}' at position {1} is followed by '{2}'.", 
                           match.Groups["duplicateWord"].Value, match.Groups["duplicateWord"].Index, 
                           match.Groups["nextWord"].Value);

   }
}
// The example displays the following output:
//       A duplicate 'that' at position 8 is followed by 'was'.
//       A duplicate 'the' at position 22 is followed by 'correct'.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)"
      Dim input As String = "He said that that was the the correct answer."
      Console.WriteLine(Regex.Matches(input, pattern, RegexOptions.IgnoreCase).Count)
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine("A duplicate '{0}' at position {1} is followed by '{2}'.", _
                           match.Groups("duplicateWord").Value, match.Groups("duplicateWord").Index, _
                           match.Groups("nextWord").Value)
      Next
   End Sub
End Module
' The example displays the following output:
'    A duplicate 'that' at position 8 is followed by 'was'.
'    A duplicate 'the' at position 22 is followed by 'correct'.
```

Este é o padrão da expressão regular:

```
(?<duplicateWord>\w+)\s\k<duplicateWord>\W(?<nextWord>\w+)
```

A tabela a seguir mostra como a expressão regular é interpretada.

Padrão | Descrição
------- | -----------
`(?<duplicateWord>\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. Atribua um nome ao grupo de captura `duplicateWord`.
`\s` | Corresponde a um caractere de espaço em branco.
`\k<duplicateWord>` | Estabeleça a correspondência com o grupo de captura chamado `duplicateWord`. 
`\W` | Estabeleça a correspondência com caracteres que não compõem palavras, como espaços em branco e pontuação. Isso impede a correspondência de um padrão de expressão regular com uma expressão que começa com a palavra do primeiro grupo capturado.
`(?<nextWord>\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. Atribua um nome ao grupo de captura `nextWord`.
 
Observe que o nome de um grupo pode ser repetido em uma expressão regular. Por exemplo, é possível que mais de um grupo seja nomeado como `digit`, como mostra o exemplo a seguir. No caso de nomes duplicados, o valor do objeto [Group](xref:System.Text.RegularExpressions.Group) é determinado pela última captura bem-sucedida na cadeia de caracteres de entrada. Além disso, a [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) é populada com informações sobre cada captura exatamente como seria se o nome do grupo não fosse duplicado. 

No exemplo a seguir, a expressão regular `\D+(?<digit>\d+)\D+(?<digit>\d+)?` inclui duas ocorrências de um grupo chamado `digit`. O primeiro grupo chamado `digit` captura um ou mais caracteres de dígito. O primeiro grupo chamado `digit` captura zero ou uma ocorrência de um ou mais caracteres de dígito. Como a saída do exemplo apresentado mostra, se o segundo grupo de captura corresponder ao texto com êxito, o valor desse texto definirá o valor do objeto [Group](xref:System.Text.RegularExpressions.Group). Se o segundo grupo de captura não corresponder à cadeia de caracteres de entrada, o valor da última correspondência bem-sucedida definirá o valor do objeto [Group](xref:System.Text.RegularExpressions.Group). 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      String pattern = @"\D+(?<digit>\d+)\D+(?<digit>\d+)?";
      String[] inputs = { "abc123def456", "abc123def" };
      foreach (var input in inputs) {
         Match m = Regex.Match(input, pattern);
         if (m.Success) {
            Console.WriteLine("Match: {0}", m.Value);
            for (int grpCtr = 1; grpCtr < m.Groups.Count; grpCtr++) {
               Group grp = m.Groups[grpCtr];
               Console.WriteLine("Group {0}: {1}", grpCtr, grp.Value);
               for (int capCtr = 0; capCtr < grp.Captures.Count; capCtr++)
                  Console.WriteLine("   Capture {0}: {1}", capCtr,
                                    grp.Captures[capCtr].Value);
            }
         }
         else {
            Console.WriteLine("The match failed.");
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//       Match: abc123def456
//       Group 1: 456
//          Capture 0: 123
//          Capture 1: 456
//
//       Match: abc123def
//       Group 1: 123
//          Capture 0: 123
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\D+(?<digit>\d+)\D+(?<digit>\d+)?"
      Dim inputs() As String = { "abc123def456", "abc123def" }
      For Each input As String In inputs
         Dim m As Match = Regex.Match(input, pattern)
         If m.Success Then
            Console.WriteLine("Match: {0}", m.Value)
            For grpCtr As Integer = 1 to m.Groups.Count - 1
               Dim grp As Group = m.Groups(grpCtr)
               Console.WriteLine("Group {0}: {1}", grpCtr, grp.Value)
               For capCtr As Integer = 0 To grp.Captures.Count - 1
                  Console.WriteLine("   Capture {0}: {1}", capCtr,
                                    grp.Captures(capCtr).Value)
               Next
            Next
         Else
            Console.WriteLine("The match failed.")
         End If
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'       Match: abc123def456
'       Group 1: 456
'          Capture 0: 123
'          Capture 1: 456
'
'       Match: abc123def
'       Group 1: 123
'          Capture 0: 123
```

A tabela a seguir mostra como a expressão regular é interpretada.

Padrão | Descrição
------- | -----------
`\D+` | Corresponder a um ou mais caracteres de dígito não decimal. 
`(?<digit>\d+)` | Corresponder a um ou mais caracteres de dígito decimal. Atribuir a correspondência ao grupo chamado `digit`. 
`\D+` | Corresponder a um ou mais caracteres de dígito não decimal. 
`(?<digit>\d+)?` | Faz a correspondência de zero ou uma ocorrência de um período seguido por um ou mais caracteres de dígito decimal. Atribuir a correspondência ao grupo chamado `digit`.
 
## <a name="balancing-group-definitions"></a>Definições de grupo de balanceamento

Uma definição de grupo de balanceamento exclui a definição de um grupo definido anteriormente e armazena, no grupo atual, o intervalo entre o grupo definido anteriormente e o atual. Esse constructo de agrupamento tem o seguinte formato: 

```
(?<name1-name2>subexpression)
```

ou:

```
(?'name1-name2' subexpression)
```

em que *name1* é o grupo atual (opcional), *name2* é um grupo definido anteriormente e *subexpression* é qualquer padrão de expressão regular válido. A definição de grupo de balanceamento exclui a definição de *name2* e armazena o intervalo entre *name2* e *name1* em *name1*. Se nenhum grupo *name2* for definido, a correspondência retrocede. Como a exclusão da última definição de *name2* revela a definição anterior de *name2*, essa construção permite que você use a pilha de capturas para o grupo *name2* como um contador, a fim de registrar construções aninhadas, como parênteses e colchetes. 

A definição de grupo de balanceamento usa *name2* como uma pilha. O caractere inicial de cada constructo aninhado é colocado no grupo e em sua coleção [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures). Quando o caractere de fechamento passa pela correspondência, seu caractere de abertura é removido do grupo e a coleção [Captures](xref:System.Text.RegularExpressions.Group.Captures) diminui em um. Depois da correspondência dos caracteres de abertura e fechamento de todas as construções, *name1* fica vazio.

> [!NOTE]
> Depois de modificar a expressão regular do exemplo a seguir para usar o caractere de abertura e fechamento adequado de um constructo aninhado, você pode usá-lo para gerenciar a maioria dos constructo aninhados, como expressões matemáticas ou linhas do código do programa que incluem diversas chamadas de método aninhado. 
 
O exemplo a seguir usa uma definição de grupo de balanceamento para estabelecer a correspondência entre os sinais de menor e maior (<>) em uma cadeia de caracteres de entrada. O exemplo define dois grupos nomeados, `Open` e `Close`, que são usados como pilha para acompanhar a correspondência entre esses sinais. Cada sinal de menor capturado é enviado para a coleção da captura do grupo `Open` e cada sinal de maior capturado é enviado para a coleção de captura do grupo `Close`. A definição do grupo de balanceamento assegura que há um sinal de maior para cada sinal de menor. Caso não haja, o subpadrão final `(?(Open)(?!))`, só será avaliado se o grupo `Open` não estiver vazio, ou seja, se todas as construções aninhadas não tiverem sido fechadas. Se o subpadrão final for avaliado, a correspondência falha, porque o subpadrão `(?!)` é uma asserção lookahead negativa de largura zero que sempre falha. 

```csharp
using System;
using System.Text.RegularExpressions;

class Example
{
   public static void Main() 
   {
      string pattern = "^[^<>]*" +
                       "(" + 
                       "((?'Open'<)[^<>]*)+" +
                       "((?'Close-Open'>)[^<>]*)+" +
                       ")*" +
                       "(?(Open)(?!))$";
      string input = "<abc><mno<xyz>>";

      Match m = Regex.Match(input, pattern);
      if (m.Success == true)
      {
         Console.WriteLine("Input: \"{0}\" \nMatch: \"{1}\"", input, m);
         int grpCtr = 0;
         foreach (Group grp in m.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", grpCtr, grp.Value);
            grpCtr++;
            int capCtr = 0;
            foreach (Capture cap in grp.Captures)
            {            
                Console.WriteLine("      Capture {0}: {1}", capCtr, cap.Value);
                capCtr++;
            }
          }
      }
      else
      {
         Console.WriteLine("Match failed.");
      }   
    }
}
// The example displays the following output:
//    Input: "<abc><mno<xyz>>"
//    Match: "<abc><mno<xyz>>"
//       Group 0: <abc><mno<xyz>>
//          Capture 0: <abc><mno<xyz>>
//       Group 1: <mno<xyz>>
//          Capture 0: <abc>
//          Capture 1: <mno<xyz>>
//       Group 2: <xyz
//          Capture 0: <abc
//          Capture 1: <mno
//          Capture 2: <xyz
//       Group 3: >
//          Capture 0: >
//          Capture 1: >
//          Capture 2: >
//       Group 4:
//       Group 5: mno<xyz>
//          Capture 0: abc
//          Capture 1: xyz
//          Capture 2: mno<xyz>
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main() 
        Dim pattern As String = "^[^<>]*" & _
                                "(" + "((?'Open'<)[^<>]*)+" & _
                                "((?'Close-Open'>)[^<>]*)+" + ")*" & _
                                "(?(Open)(?!))$"
        Dim input As String = "<abc><mno<xyz>>"
        Dim rgx AS New Regex(pattern)'
        Dim m As Match = Regex.Match(input, pattern)
        If m.Success Then
            Console.WriteLine("Input: ""{0}"" " & vbCrLf & "Match: ""{1}""", _
                               input, m)
            Dim grpCtr As Integer = 0
            For Each grp As Group In m.Groups
               Console.WriteLine("   Group {0}: {1}", grpCtr, grp.Value)
               grpCtr += 1
               Dim capCtr As Integer = 0
               For Each cap As Capture In grp.Captures            
                  Console.WriteLine("      Capture {0}: {1}", capCtr, cap.Value)
                  capCtr += 1
               Next
            Next
        Else
            Console.WriteLine("Match failed.")
        End If
    End Sub
End Module  
' The example displays the following output:
'       Input: "<abc><mno<xyz>>"
'       Match: "<abc><mno<xyz>>"
'          Group 0: <abc><mno<xyz>>
'             Capture 0: <abc><mno<xyz>>
'          Group 1: <mno<xyz>>
'             Capture 0: <abc>
'             Capture 1: <mno<xyz>>
'          Group 2: <xyz
'             Capture 0: <abc
'             Capture 1: <mno
'             Capture 2: <xyz
'          Group 3: >
'             Capture 0: >
'             Capture 1: >
'             Capture 2: >
'          Group 4:
'          Group 5: mno<xyz>
'             Capture 0: abc
'             Capture 1: xyz
'             Capture 2: mno<xyz>
```

O padrão da expressão regular é:

```
^[^<>]*(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*(?(Open)(?!))$
```

A expressão regular é interpretada da seguinte forma:

Padrão | Descrição
------- | -----------
`^` | Começa no início da cadeia de caracteres.
`[^<>]*` | Corresponde a zero ou mais caracteres que não são sinais de menor nem maior.
`(?'Open'<)` | Corresponde a um sinal de menor e o atribui a um grupo nomeado `Open`.
`[^<>]*` | Corresponde a zero ou mais caracteres que não são sinais de menor nem maior.
`((?'Open'<)[^<>]*) +` | Corresponde uma ou mais ocorrências de um sinal de menor, seguida por zero ou mais caracteres que não são sinais de menor ou maior. Este é o segundo grupo de captura.
`(?'Close-Open'>)` | Corresponde a um sinal de maior, atribui a subcadeia de caracteres entre o grupo `Open` e o grupo atual ao grupo `Close` e exclui a definição do grupo `Open`.
`[^<>]*` | Corresponde a zero ou mais ocorrências de caracteres que não são sinais de menor ou maior. 
`((?'Close-Open'>)[^<>]*)+` | Corresponde a uma ou mais ocorrências de sinal de menor seguidas por zero ou mais ocorrências de qualquer caractere que não seja um sinal de menor ou maior. Ao estabelecer a correspondência de um sinal de maior, atribua a subcadeia de caracteres entre o grupo `Open` e o grupo atual ao grupo `Close` e exclua a definição do grupo `Open`. Este é o terceiro grupo de captura.
`(((?'Open'<)[^<>]*)+((?'Close-Open'>)[^<>]*)+)*` | Corresponde a zero ou mais ocorrências do seguinte padrão: uma ou mais ocorrências de sinal de menor seguidas por zero ou mais ocorrências de qualquer caractere que não seja um sinal de menor ou maior, seguida por uma ou mais ocorrências de sinal de maior, seguida por zero ou mais ocorrências de caracteres que não sejam sinais de menor ou maior. Ao estabelecer a correspondência de um sinal de maior, exclua a definição do grupo `Open` e atribua a subcadeia entre o grupo `Open` e o grupo atual ao grupo `Close`. Este é o primeiro grupo de captura.
`(?(Open)(?!))` | Se o grupo `Open` existir, abandone a correspondência se for possível estabelecer a correspondência de uma cadeia de caracteres vazia, mas não avance a posição do mecanismo de expressão regular na cadeia de caracteres. Trata-se de uma asserção lookahead negativa de largura zero. Como sempre há cadeias de caracteres vazias presentes em cadeias de caracteres de entrada, essa correspondência sempre falha. A falha nessa correspondência indica que os sinais de menor e maior não estão balanceados. 
`$` | Corresponder ao final da cadeia de caracteres de entrada.
 
A subexpressão final, `(?(Open)(?!))`, indica se a construção de aninhamento da cadeia de caracteres de entrada está balanceada corretamente (por exemplo, se cada sinal de maior corresponde a um sinal de menor). Ela usa a correspondência condicional com base em um grupo capturado válido; para obter mais informações, veja [Construções de alternância em expressões regulares](alternation.md). Se o grupo `Open` for definido, o mecanismo de expressão regular tenta estabelecer a correspondência da subexpressão `(?!)` na cadeia de caracteres de saída. O grupo `Open` só deve ser definido se as construções de aninhamento não estiverem balanceadas. Portanto, o padrão para correspondência na cadeia de caracteres de entrada sempre deve fazer com que a correspondência falhe. Nesse caso, `(?!)` é uma asserção lookahead negativa de largura zero que sempre falha, porque sempre há cadeias de caracteres vazias presentes na próxima posição da cadeia de caracteres de entrada.

No exemplo, o mecanismo da expressão regular avalia a cadeia de caracteres de entrada "<abc><mno<xyz>>", conforme mostra a tabela a seguir.

Etapa | Padrão | Resultado
---- | ------- | ------ 
1 | `^` | Começa a correspondência no início da cadeia de caracteres de entrada
2 | `[^<>]*` | Procura caracteres que não sejam sinais de menor e maior antes do sinal de menor e não encontra correspondências. 
3 | `(((?'Open'<)` | Corresponde ao sinal de menor em "<abc>" e o atribui ao grupo `Open`.
4 | `[^<>]*` | Corresponde a "abc".
5 | `)+` | "<abc" é o valor do segundo grupo capturado. O próximo caractere na cadeia de caracteres de entrada não é um sinal de menor. Por isso, o mecanismo de expressão regular não volta para o subpadrão `(?'Open'<)[^<>]*)`.
6 | `((?'Close-Open'>)` | Corresponde ao sinal de maior de "<abc>", atribui "abc", que é a subcadeia de caracteres entre o grupo `Open` e o sinal de menor, para o grupo `Close` e exclui o valor atual ("<") do grupo `Open`, deixando-o vazio.
7 | `[^<>]*` | Procura caracteres que não sejam sinais de menor e maior depois do sinal de maior e não encontra correspondências.
8 | `)+` | O valor do terceiro grupo capturado é ">". O próximo caractere na cadeia de caracteres de entrada não é um sinal de maior. Por isso, o mecanismo de expressão regular não volta para o subpadrão `((?'Close-Open'>)[^<>]*)`.
9 | `)*` | O valor do primeiro grupo capturado é "<abc>". O próximo caractere na cadeia de caracteres de entrada é um sinal de menor. Por isso, o mecanismo de expressão regular volta para o subpadrão `(((?'Open'<)`.
10 | `(((?'Open'<)` | Corresponde ao sinal de menor em "<mno>" e o atribui ao grupo `Open`. Agora, sua coleção `Group.Captures` tem um único valor, "<".
11 | `[^<>]*` | Corresponde a "mno".
12 | `)+` | "<mno" é o valor do segundo grupo capturado. O próximo caractere na cadeia de caracteres de entrada é um sinal de menor. Por isso, o mecanismo de expressão regular volta para o subpadrão `(?'Open'<)[^<>]*)`.
13 | `(((?'Open'<)` | Corresponde ao sinal de menor em "<xyz>" e o atribui ao grupo `Open`. Agora, a coleção `Group.Captures` do grupo `Open` inclui duas capturas: o sinal de menor de "<mno>" e de "<xyz>".
14 | `[^<>]*` | Corresponde a "xyz".
15 | `)+` | "<xyz" é o valor do segundo grupo capturado. O próximo caractere na cadeia de caracteres de entrada não é um sinal de menor. Por isso, o mecanismo de expressão regular não volta para o subpadrão `(?'Open'<)[^<>]*)`.
16 | `((?'Close-Open'>)` | Corresponde ao sinal de maior em "<xyz>". "xyz" atribui a subcadeia de caracteres entre o grupo `Open` e o sinal de maior ao grupo `Close` e exclui o valor atual do grupo `Open`. O valor da captura anterior (ao sinal de menor em "<mno>") torna-se o valor atual do grupo `Open`. Agora, a coleção `Captures` do grupo `Open` inclui uma única captura: o sinal de menor de "<xyz>".
17 | `[^<>]*` | Procura caracteres que não sejam sinais de menor e maior e não encontra correspondências.
18 | `)+` | O valor do terceiro grupo capturado é ">". O próximo caractere na cadeia de caracteres de entrada é um sinal de maior. Por isso, o mecanismo de expressão regular volta para o subpadrão `((?'Close-Open'>)[^<>]*)`.
19 | `((?'Close-Open'>)` | Corresponde ao sinal de maior final de "xyz>>", atribui "mno<xyz>" (a subcadeia de caracteres entre o grupo `Open` e o sinal de maior) ao grupo `Close` e exclui o valor atual do grupo `Open`. Agora, o grupo `Open` está vazio.
20 | `[^<>]*` | Procura caracteres que não sejam sinais de menor e maior e não encontra correspondências.
21 | `)+` | O valor do terceiro grupo capturado é ">". O próximo caractere na cadeia de caracteres de entrada não é um sinal de maior. Por isso, o mecanismo de expressão regular não volta para o subpadrão `((?'Close-Open'>)[^<>]*)`.
22 | `)*` | O valor do primeiro grupo capturado é "<mno<xyz>>". O próximo caractere na cadeia de caracteres de entrada não é um sinal de menor. Por isso, o mecanismo de expressão regular não volta para o subpadrão `(((?'Open'<)`.
23 | `(?(Open)(?!))` | O grupo `Open` não é definido. Por isso, não há tentativa de correspondência.
24 | `$` | Corresponde ao final da cadeia de caracteres de entrada.

## <a name="noncapturing-groups"></a>Grupos de não captura

O constructo de grupo a seguir não captura a subcadeia de caracteres correspondente a uma subexpressão:

```
**(?**:_subexpression_**)**
```

em que *subexpression* é qualquer padrão de expressão regular válido. O constructo de grupo de não captura geralmente é usada quando um quantificador é aplicado a um grupo, mas as subcadeias de caracteres capturadas pelo grupo não são úteis.

>[!NOTE]
> Se uma expressão regular inclui constructos aninhados de agrupamento, um constructo de grupo de não captura externo não se aplica às construções aninhadas internas de grupo. 
 
O exemplo a seguir mostra uma expressão regular que inclui grupos de não captura. O resultado não inclui grupos capturados.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?:\b(?:\w+)\W*)+\.";
      string input = "This is a short sentence.";
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: {0}", match.Value);
      for (int ctr = 1; ctr < match.Groups.Count; ctr++)
         Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
   }
}
// The example displays the following output:
//       Match: This is a short sentence.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?:\b(?:\w+)\W*)+\."
      Dim input As String = "This is a short sentence."
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: {0}", match.Value)
      For ctr As Integer = 1 To match.Groups.Count - 1
         Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       Match: This is a short sentence.
```

A expressão regular `(?:\b(?:\w+)\W*)+\.` corresponde a uma sentença terminada por um ponto final. Como a expressão regular concentra-se em sentenças, e não em palavras, as construções de agrupamento são usadas apenas como quantificadores. O padrão da expressão regular é interpretado conforme a tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começa a correspondência em um limite de palavra.
`(?:\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. Não atribui o texto coincidente a um grupo capturado.
`\W*` | Corresponde a zero ou mais caracteres que não compõem palavras.
`(?:\b(?:\w+)\W*)+` | Corresponde ao padrão de um ou mais caracteres de palavra que começam com um limite de palavra, seguido por zero ou um espaço em branco uma ou mais vezes. Não atribui o texto coincidente a um grupo capturado.
`\.` | Corresponde a um ponto final.
 
## <a name="group-options"></a>Opções de grupo

O constructo de agrupamento a seguir aplica ou desabilita as opções especificadas em uma subexpressão:

**(?imnsx-imnsx:**_subexpression_**)**

em que *subexpression* é qualquer padrão de expressão regular válido. Por exemplo, `(?i-s:)` ativa a diferenciação de maiúsculas e minúsculas e desabilita o modo de linha única. Para saber mais sobre as opções embutidas que você pode especificar, veja [Opções de expressões regulares](options.md).

> [!NOTE]
> Você pode especificar opções que se aplicam a toda uma expressão regular, em vez de a uma subexpressão, usando um construtor de classe [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) ou método estático. Você também pode especificar opções embutidas que são aplicadas após um ponto específico de uma expressão regular, usando o constructo de linguagem `(?imnsx-imnsx)`.
 
O constructo de opções de grupo não é um grupo de captura. Ou seja, embora todas as porções de uma cadeia de caracteres que são capturadas pela *subexpression* sejam incluídas na correspondência, elas não são incluídas em grupos capturados nem usadas para preencher o objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection).

Por exemplo, a expressão regular `\b(?ix: d \w+)\s ` do exemplo a seguir usa opções embutidas em um constructo de agrupamento para habilitar a correspondência com diferenciação de letras maiúsculas e minúsculas, e ignora espaços em branco ao identificar palavras que começam com a letra "d". A expressão regular é definida como mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começar a correspondência em um limite de palavra.
 `(?ix: d \w+)` | Usa a correspondência sem diferenciar letras maiúsculas e minúsculas e ignora espaços em branco nesse padrão e corresponde um "d" seguido por um ou mais caracteres que compõem palavras. 
`\s` | Corresponde a um caractere de espaço em branco.
 
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

## <a name="zero-width-positive-lookahead-assertions"></a>Asserções lookahead positivas de largura zero

O constructo de agrupamento a seguir define uma asserção lookahead positiva de largura zero:

**(?**=*subexpression*__)__

em que *subexpression* é qualquer padrão de expressão regular. Para que a correspondência seja executada com êxito, a cadeia de caracteres de entrada deve corresponder ao padrão de expressão regular na *subexpression*, embora a subcadeia de caracteres com a qual a correspondência foi estabelecida não conste no resultado. A asserção lookahead positiva de largura zero não retrocede.

Geralmente, as asserções desse tipo podem ser encontradas no final de um padrão de expressão regular. Isso define uma subcadeia de caracteres que deve estar presente no final da cadeia de caracteres para que seja possível estabelecer a correspondência, mas que não seja incluída na correspondência. Isso também é útil para evitar retrocessos em excesso. Você pode usar asserções lookahead positivas de largura zero que garantam que um grupo capturado específico seja iniciado por um texto que corresponda a um subconjunto do padrão definido para o grupo capturado. Por exemplo, se um grupo de captura corresponder a caracteres de palavras em sequência, você pode usar uma asserção desse tipo para que o primeiro caractere seja uma caractere alfabético maiúsculo.

O exemplo a seguir usa asserção lookahead positiva de largura zero para estabelecer a correspondência da palavra que precede o verbo "is" na cadeia de caracteres de entrada. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\w+(?=\sis\b)";
      string[] inputs = { "The dog is a Malamute.", 
                          "The island has beautiful birds.", 
                          "The pitch missed home plate.", 
                          "Sunday is a weekend day." };

      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine("'{0}' precedes 'is'.", match.Value);
         else
            Console.WriteLine("'{0}' does not match the pattern.", input); 
      }
   }
}
// The example displays the following output:
//    'dog' precedes 'is'.
//    'The island has beautiful birds.' does not match the pattern.
//    'The pitch missed home plate.' does not match the pattern.
//    'Sunday' precedes 'is'.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\w+(?=\sis\b)"
      Dim inputs() As String = { "The dog is a Malamute.", _
                                 "The island has beautiful birds.", _
                                 "The pitch missed home plate.", _
                                 "Sunday is a weekend day." }

      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("'{0}' precedes 'is'.", match.Value)
         Else
            Console.WriteLine("'{0}' does not match the pattern.", input) 
         End If     
      Next
   End Sub
End Module
' The example displays the following output:
'       'dog' precedes 'is'.
'       'The island has beautiful birds.' does not match the pattern.
'       'The pitch missed home plate.' does not match the pattern.
'       'Sunday' precedes 'is'.
```

O padrão da expressão regular \b\w+(?=\sis\b) é interpretado conforme a tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começa a correspondência em um limite de palavra.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`(?=\sis\b)` | Determina se os caracteres que compõem palavras são seguidos por um caractere de espaço em branco e pela cadeia de caracteres "is", que termina com um limite de palavra. Nesse caso, a correspondência ocorreu com êxito.

## <a name="zero-width-negative-lookahead-assertions"></a>Asserções lookahead negativas de largura zero

O constructo de agrupamento a seguir define uma asserção lookahead negativa de largura zero:

**(?!**_subexpression_**)**

em que *subexpression* é qualquer padrão de expressão regular. Para que a correspondência seja executada com êxito, a cadeia de caracteres de entrada não deve corresponder ao padrão de expressão regular na *subexpression*, embora a cadeia de caracteres com a qual a correspondência foi estabelecida não conste no resultado. 

Geralmente, as asserções desse tipo podem ser encontradas no início ou no final de uma expressão regular. No início da expressão regular, elas podem definir um padrão específico que não deve ser correspondido quando o início da expressão regular definir um padrão parecido, mas mais geral, para a correspondência. Nesse caso, ela geralmente é usada para limitar o retrocesso. No final de uma expressão regular, pode definir uma subexpressão que pode não ocorrer no final de uma correspondência. 

O exemplo a seguir define uma expressão regular que usa uma asserção lookahead de largura zero no início da expressão regular para fazer a correspondência de palavras que não começam com "un". 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?!un)\w+\b";
      string input = "unite one unethical ethics use untie ultimate";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       one
//       ethics
//       use
//       ultimate
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?!un)\w+\b"
      Dim input As String = "unite one unethical ethics use untie ultimate"
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       one
'       ethics
'       use
'       ultimate
```

O padrão da expressão regular \b(?!un)\w+\b é interpretado conforme a tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começar a correspondência em um limite de palavra.
`(?!un)` | Determina se os dois caracteres seguintes são "un". Caso não sejam, é possível estabelecer a correspondência.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`\b` | Termina a correspondência em um limite de palavra.
 
O exemplo a seguir define uma expressão regular que usa uma asserção lookahead de largura zero no final da expressão regular para fazer a correspondência de palavras que não terminam com um caractere de pontuação.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\w+\b(?!\p{P})";
      string input = "Disconnected, disjointed thoughts in a sentence fragment.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       disjointed
//       thoughts
//       in
//       a
//       sentence
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\w+\b(?!\p{P})"
      Dim input As String = "Disconnected, disjointed thoughts in a sentence fragment."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next   
   End Sub
End Module
' The example displays the following output:
'       disjointed
'       thoughts
'       in
'       a
'       sentence
```

A expressão regular `\b\w+\b(?!\p{P})` é interpretada conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começa a correspondência em um limite de palavra.
`\w+` | Fazer a correspondência a um ou mais caracteres de palavra.
`\b` | Termina a correspondência em um limite de palavra.
`\p{P})` | Se o caractere seguinte não for um símbolo de pontuação (por exemplo, um ponto final ou uma vírgula), a correspondência é estabelecida.
 
## <a name="zero-width-positive-lookbehind-assertions"></a>Asserções lookbehind positivas de largura zero

O constructo de agrupamento a seguir define uma asserção lookbehind positiva de largura zero:

**(?<=**_subexpression_**)**

em que *subexpression* é qualquer padrão de expressão regular. Para que a correspondência seja executada com êxito, a *subexpressão* deve ocorrer na cadeia de caracteres de entrada à esquerda da posição atual, embora a subexpressão não conste no resultado. A asserção lookbehind positiva de largura zero não retrocede.

As asserções lookbehind positivas de largura zero geralmente são usadas no início de expressões regulares. O padrão que elas definem é uma pré-condição para a correspondência, embora não constem no resultado. 

Por exemplo, o exemplo a seguir estabelece a correspondência para os dois últimos dígitos de ano no século XXI (ou seja, ele requer que os dígitos "20" apareçam antes da cadeia de caracteres coincidente).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "2010 1999 1861 2140 2009";
      string pattern = @"(?<=\b20)\d{2}\b";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       10
//       09
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "2010 1999 1861 2140 2009"
      Dim pattern As String = "(?<=\b20)\d{2}\b"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next      
   End Sub
End Module
' The example displays the following output:
'       10
'       09
```

O padrão da expressão regular `(?<=\b20)\d{2}\b` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\d{2}` | Corresponde a dois dígitos decimais.
`{?<=\b20)` | Continua a estabelecer a correspondência se os dois dígitos decimais forem precedidos por dígitos decimais "20" em um limite de palavra.
`\b` | Termina a correspondência em um limite de palavra.
 
As asserções lookbehind positivas de largura zero também são usadas para limitar o retrocesso quando o último caractere de um grupo capturado precisar ser um subconjunto de caracteres que corresponde ao padrão de expressão regular desse grupo. Por exemplo, se um grupo captura todos os caracteres de palavras em sequência, você pode usar uma asserção lookbehind positivas de largura zero tipo para que o primeiro caractere seja uma letra. 

## <a name="zero-width-negative-lookbehind-assertions"></a>Asserções lookbehind negativas de largura zero

O constructo de agrupamento a seguir define uma asserção lookbehind negativa de largura zero:

**(?<!**_subexpression_**)**

em que *subexpression* é qualquer padrão de expressão regular. Para que a correspondência seja executada com êxito, a *subexpressão* não deve ocorrer na cadeia de caracteres de entrada à esquerda da posição atual. No entanto, todas as subcadeias de caracteres que não corresponderem à subexpressão não serão incluídas no resultado.

As asserções lookbehind negativas de largura zero geralmente são usadas no início de expressões regulares. O padrão definido por elas elimina uma correspondência na cadeia de caracteres seguinte. Elas também são usadas para limitar o retrocesso quando o último caractere de um grupo capturado não precisar ser um ou mais caracteres que corresponde ao padrão de expressão regular desse grupo. Por exemplo, se um grupo captura todos os caracteres de palavras em sequência, você pode usar uma asserção lookbehind positiva de largura zero para que o primeiro caractere não seja um sublinhado (_).

O exemplo a seguir estabelece a correspondência de data para qualquer dia da semana que não seja sábado nem domingo. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] dates = { "Monday February 1, 2010", 
                         "Wednesday February 3, 2010", 
                         "Saturday February 6, 2010", 
                         "Sunday February 7, 2010", 
                         "Monday, February 8, 2010" };
      string pattern = @"(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b";

      foreach (string dateValue in dates)
      {
         Match match = Regex.Match(dateValue, pattern);
         if (match.Success)
            Console.WriteLine(match.Value);
      }      
   }
}
// The example displays the following output:
//       February 1, 2010
//       February 3, 2010
//       February 8, 2010
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim dates() As String = { "Monday February 1, 2010", _
                                "Wednesday February 3, 2010", _
                                "Saturday February 6, 2010", _
                                "Sunday February 7, 2010", _
                                "Monday, February 8, 2010" }
      Dim pattern As String = "(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b"

      For Each dateValue As String In dates
         Dim match As Match = Regex.Match(dateValue, pattern)
         If match.Success Then
            Console.WriteLine(match.Value)
         End If   
      Next      
   End Sub
End Module
' The example displays the following output:
'       February 1, 2010
'       February 3, 2010
'       February 8, 2010
```

O padrão da expressão regular `(?<!(Saturday|Sunday) )\b\w+ \d{1,2}, \d{4}\b` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começar a correspondência em um limite de palavra.
`\w+` | Corresponde a um ou mais caracteres de palavra seguido por um espaço em branco.
`\d{1,2},` | Corresponde a um ou dois dígitos decimais seguidos por uma caractere de espaço em branco e uma vírgula.
`\d{4}\b` | Corresponde a quatro dígitos decimais e encerra a correspondência em um limite de palavra.
`(?<!(Saturday|Sunday) )` | Se a correspondência for precedida por algo que não seja as cadeias de caracteres "Sábado" ou "Domingo" seguidas por um espaço, a correspondência é realizada com êxito.

## <a name="nonbacktracking-subexpressions"></a>Subexpressões sem retrocesso

O constructo de agrupamento a seguir representa uma subexpressão sem retrocesso, também conhecida como subexpressão "greedy":

**(?>**_subexpression_**)**

em que *subexpression* é qualquer padrão de expressão regular.

Geralmente, se uma expressão regular incluir um padrão de correspondência opcional ou alternativo e a correspondência não for realizada com êxito, o mecanismo da expressão regular pode ramificar em diversas orientações para estabelecer a correspondência entre uma cadeia de caracteres de entrada e um padrão. Se a correspondência não for encontrada na primeira ramificação, o mecanismo da expressão regular pode voltar ou retroceder ao ponto da primeira correspondência e tentar estabelecer a correspondência usando a segunda ramificação. Esse processo pode continuar até que as tentativas se esgotem.

O constructo de linguagem da **(?>**_subexpression_**)** desabilita o retrocesso. O mecanismo de expressão regular estabelece a correspondência entre o máximo de caracteres da cadeia de caracteres de entrada. Quando não for possível estabelecer outras correspondências, ele não retrocede para tentar alternativas. Ou seja, a subexpressão corresponde somente às cadeias de caracteres que poderiam corresponder somente à subexpressão. Ela não tenta fazer a correspondência de uma cadeia de caracteres com base na subexpressão em questão e nas subexpressões seguintes. 

Essa opção é recomendada quando você sabe que o retrocesso não terá êxito. Evitar que o mecanismo de expressão regular faça pesquisas desnecessárias, melhora o desempenho. 

O exemplo a seguir mostra como uma subexpressão sem retrocesso modifica os resultados de uma correspondência padrão. A expressão regular de retrocesso estabelece a correspondência de diversos caracteres repetidos, seguidos por outra ocorrência do mesmo caractere de um limite de palavra, mas a expressão regular sem retrocesso não faz isso. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "cccd.", "aaad", "aaaa" };
      string back = @"(\w)\1+.\b";
      string noback = @"(?>(\w)\1+).\b";

      foreach (string input in inputs)
      {
         Match match1 = Regex.Match(input, back);
         Match match2 = Regex.Match(input, noback);
         Console.WriteLine("{0}: ", input);

         Console.Write("   Backtracking : ");
         if (match1.Success)
            Console.WriteLine(match1.Value);
         else
            Console.WriteLine("No match");

         Console.Write("   Nonbacktracking: ");
         if (match2.Success)
            Console.WriteLine(match2.Value);
         else
            Console.WriteLine("No match");
      }
   }
}
// The example displays the following output:
//    cccd.:
//       Backtracking : cccd
//       Nonbacktracking: cccd
//    aaad:
//       Backtracking : aaad
//       Nonbacktracking: aaad
//    aaaa:
//       Backtracking : aaaa
//       Nonbacktracking: No match
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "cccd.", "aaad", "aaaa" }
      Dim back As String = "(\w)\1+.\b"
      Dim noback As String = "(?>(\w)\1+).\b"

      For Each input As String In inputs
         Dim match1 As Match = Regex.Match(input, back)
         Dim match2 As Match = Regex.Match(input, noback)
         Console.WriteLine("{0}: ", input)

         Console.Write("   Backtracking : ")
         If match1.Success Then
            Console.WriteLine(match1.Value)
         Else
            Console.WriteLine("No match")
         End If

         Console.Write("   Nonbacktracking: ")
         If match2.Success Then
            Console.WriteLine(match2.Value)
         Else
            Console.WriteLine("No match")
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'    cccd.:
'       Backtracking : cccd
'       Nonbacktracking: cccd
'    aaad:
'       Backtracking : aaad
'       Nonbacktracking: aaad
'    aaaa:
'       Backtracking : aaaa
'       Nonbacktracking: No match
```

A expressão regular sem retrocesso `(?>(\w)\1+).\b` é definida como mostra a tabela a seguir.

Padrão | Descrição
------- | -----------
`(\w)` | Corresponde a um único caractere que compõe palavras e o atribui ao primeiro grupo de captura.
`\1+` | Corresponde ao valor da primeira subcadeia de caracteres de captura uma ou mais vezes.
`.` | Corresponde a qualquer caractere.
`\b` | Termina a correspondência em um limite de palavra.
`(?>(\w)\1+)` | Corresponde a uma ou mais ocorrências de um caractere de palavra duplicado, mas não executa o retrocesso para estabelecer a correspondência com o último caractere em um limite de palavra.
 
## <a name="grouping-constructs-and-regular-expression-objects"></a>Agrupando construções e objetos de expressão regulares

Subcadeias de caracteres que correspondem a um grupo de captura de expressão regular são representadas por objetos [System.Text.RegularExpressions.Group](xref:System.Text.RegularExpressions.Group), que podem ser recuperados do objeto [System.Text.RegularExpressions.GroupCollection](xref:System.Text.RegularExpressions.GroupCollection), que é retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups). O objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) é preenchido conforme demonstrado a seguir:

* O primeiro objeto [Group](xref:System.Text.RegularExpressions.Group) da coleção (o objeto de índice zero) representa a correspondência total.

* O conjunto seguinte de objetos [Group](xref:System.Text.RegularExpressions.Group) representa os grupos de captura não nomeados (numerados). Eles aparecem na ordem em que são definidos na expressão regular, da esquerda para a direita. Os valores dos índices desses grupos variam de 1 até o número de grupos de captura não nomeados presentes na coleção. O índice de um determinado grupo equivale a sua referência inversa numerada. Para obter mais informações sobre referências inversas, veja [Construções de referências inversas em expressões regulares](backreference.md)

* O conjunto final de objetos [Group](xref:System.Text.RegularExpressions.Group) representa os grupos de captura nomeados. Eles aparecem na ordem em que são definidos na expressão regular, da esquerda para a direita. O valor do índice do primeiro grupo de captura nomeado é um número maior que o índice do último grupo de captura não nomeado. Se não houver grupos de captura não nomeados na expressão regular, o valor do índice do primeiro grupo de captura nomeado será um. 


Se você aplicar um quantificador a um grupo de captura, as propriedades [Capture.Value](xref:System.Text.RegularExpressions.Capture.Value), [Capture.Index](xref:System.Text.RegularExpressions.Capture.Index) e [Capture.Length](xref:System.Text.RegularExpressions.Capture.Length) do objeto [Group](xref:System.Text.RegularExpressions.Group) refletirão a última subcadeia de caracteres capturada por um grupo de captura. Você pode recuperar todo o conjunto de subcadeias de caracteres capturadas por grupos que têm quantificadores do objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) e que são retornados pela propriedade [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures).

O exemplo a seguir esclarece a relação entre os objetos [Group](xref:System.Text.RegularExpressions.Group) e [Capture](xref:System.Text.RegularExpressions.Capture). 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\b(\w+)\W+)+";
      string input = "This is a short sentence.";
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}'", match.Value);
      for (int ctr = 1; ctr < match.Groups.Count; ctr++)
      {
         Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups[ctr].Value);
         int capCtr = 0;
         foreach (Capture capture in match.Groups[ctr].Captures)
         {
            Console.WriteLine("      Capture {0}: '{1}'", capCtr, capture.Value);
            capCtr++;
         }
      }
   }
}
// The example displays the following output:
//       Match: 'This is a short sentence. '
//          Group 1: 'sentence.'
//             Capture 0: 'This '
//             Capture 1: 'is '
//             Capture 2: 'a '
//             Capture 3: 'short '
//             Capture 4: 'sentence.'
//          Group 2: 'sentence'
//             Capture 0: 'This'
//             Capture 1: 'is'
//             Capture 2: 'a'
//             Capture 3: 'short'
//             Capture 4: 'sentence'
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\b(\w+)\W+)+"
      Dim input As String = "This is a short sentence."
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}'", match.Value)
      For ctr As Integer = 1 To match.Groups.Count - 1
         Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups(ctr).Value)
         Dim capCtr As Integer = 0
         For Each capture As Capture In match.Groups(ctr).Captures
            Console.WriteLine("      Capture {0}: '{1}'", capCtr, capture.Value)
            capCtr += 1
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is a short sentence.'
'          Group 1: 'sentence.'
'             Capture 0: 'This '
'             Capture 1: 'is '
'             Capture 2: 'a '
'             Capture 3: 'short '
'             Capture 4: 'sentence.'
'          Group 2: 'sentence'
'             Capture 0: 'This'
'             Capture 1: 'is'
'             Capture 2: 'a'
'             Capture 3: 'short'
'             Capture 4: 'sentence'
```

O padrão da expressão regular `\b(\w+)\W+)+` extrai palavras, uma a uma, da cadeia de caracteres. Ele é definido conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Começa a correspondência em um limite de palavra.
`(\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. Juntos, esses caracteres compõem uma palavra. Este é o segundo grupo de captura.
`\W+` | Estabeleça a correspondência com um ou mais caracteres que não compõem palavras.
`(\w+)\W+)+` | Corresponde ao padrão de um ou mais caracteres de palavra, seguido por um ou mais caracteres que não compõem palavras, uma ou mais vezes. Este é o primeiro grupo de captura.
 
O primeiro grupo de captura corresponde a cada palavra da sentença. O segundo grupo de captura corresponde a cada palavras com a pontuação ou o espaço em branco que segue a palavra em questão. O objeto [Group](xref:System.Text.RegularExpressions.Group), cujo índice é 2, fornece informações sobre o texto correspondente ao segundo grupo de captura. O conjunto completo de palavras capturadas pelo grupo de captura está disponível no objeto [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection), retornado pela propriedade [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures).

## <a name="see-also"></a>Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)

[Retrocesso em expressões regulares](backtracking.md)



<!--HONumber=Nov16_HO4-->


