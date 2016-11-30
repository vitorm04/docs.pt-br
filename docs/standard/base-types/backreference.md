---
title: "Constructos de referência inversa em expressões regulares"
description: "Constructos de referência inversa em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c453ed78-650f-4c3c-9ab4-9d89d250bf88
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 757c8c4e71bbafb12c8add925723daf1a24e06d1

---

# <a name="backreference-constructs-in-regular-expressions"></a>Constructos de referência inversa em expressões regulares

As referências inversas fornecem uma maneira conveniente de identificar um caractere ou subcadeia de caracteres repetida em uma cadeia de caracteres. Por exemplo, se a cadeia de caracteres de entrada contiver várias ocorrências de uma subcadeia de caracteres arbitrária, você poderá corresponder a primeira ocorrência a um grupo de captura e, em seguida, usar uma referência inversa para corresponder às ocorrências subsequentes da subcadeia de caracteres. 

> [!NOTE]
> Uma sintaxe separada é usada para se referir a grupos de captura nomeados e numerados em cadeias de caracteres de substituição. Para obter mais informações, consulte [Substituições em expressões regulares](substitutions.md).
 
O .NET define elementos de linguagem separados para se referir a grupos de captura nomeados e numerados. Para obter mais informações sobre os grupos de captura, confira [Constructos de agrupamento em expressões regulares](grouping.md).

## <a name="numbered-backreferences"></a>Referências inversas numeradas

Uma referência inversa numerada usa a seguinte sintaxe:

**\**_number_

em que *number* é a posição ordinal do grupo de captura na expressão regular. Por exemplo, `\4` corresponde ao conteúdo do quarto grupo de captura. Se *number* não for definido no padrão da expressão regular, ocorrerá um erro de análise e o mecanismo de expressões regulares gerará um [ArgumentException](xref:System.ArgumentException). Por exemplo, a expressão regular `\b(\w+)\s\1` é válida porque `(\w+)` é o primeiro e único grupo de captura na expressão. Por outro lado, `\b(\w+)\s\2` é inválida e gera uma exceção de argumento porque não há nenhum grupo de captura com o número `\2`.

Observe a ambiguidade entre códigos de escape octais (como `\16`) e as referências inversas **\**_number_ que usam a mesma notação. Essa ambiguidade é resolvida da seguinte maneira:

* As expressões `\1` a `\9` sempre são interpretadas como referências inversas e não como códigos octais.

* Se o primeiro dígito de uma expressão de diversos for 8 ou 9 (como `\80` ou `\91`), a expressão será interpretada como uma literal.

* Expressões de `\10` e maiores serão consideradas referências inversas se houver uma referência inversa correspondente àquele número, caso contrário, elas serão interpretadas como códigos octais.

* Se uma expressão regular contiver uma referência inversa para um número de grupo indefinido, ocorrerá um erro de análise e o mecanismo de expressões regulares gerará um [ArgumentException](xref:System.ArgumentException).

Se a ambiguidade for um problema, você poderá usar a notação **\k<**_name_**>**, que não é ambígua e não pode ser confundida com códigos de caracteres octais. Da mesma forma, os códigos hexadecimais como `\xdd` são não ambíguos e não podem ser confundidos com referências inversas.

O exemplo a seguir localiza caracteres de palavra duplicados em uma cadeia de caracteres. Ele define uma expressão regular, `(\w)\1,`, que consiste nos elementos a seguir.

Elemento | Descrição
------- | -----------
`(\w)` | Corresponde a um caractere de palavra e o atribui ao primeiro grupo de captura.
`\1` | Corresponde ao próximo caractere que é o mesmo que o valor do primeiro grupo de captura.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\w)\1";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\w)\1"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

## <a name="named-backreferences"></a>Referências inversas nomeadas

Uma referência inversa nomeada é definida usando a sintaxe a seguir:

**\k<**_name_**>**

ou:

**\k'**_name_**'**

em que *name* é o nome de um grupo de captura definido no padrão da expressão regular. Se *name* não for definido no padrão da expressão regular, ocorrerá um erro de análise e o mecanismo de expressões regulares gerará um [ArgumentException](xref:System.ArgumentException).

O exemplo a seguir localiza caracteres de palavra duplicados em uma cadeia de caracteres. Ele define uma expressão regular, `(?<char>\w)\k<char>`, que consiste nos elementos a seguir.

Elemento | Descrição
------- | -----------
`(?<char>\w)` | Corresponde a um caractere de palavra e o atribui a um char nomeado do grupo de captura.
`\k<char>` | Corresponde ao próximo caractere que é o mesmo que o valor do grupo de captura char.
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<char>\w)\k<char>";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<char>\w)\k<char>"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

Observe que *name* também pode ser a representação da cadeia de caracteres de um número. Por exemplo, o exemplo a seguir usa a expressão regular `(?<2>\w)\k<2>` para localizar caracteres de palavra duplicados em uma cadeia de caracteres.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<2>\w)\k<2>";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<2>\w)\k<2>"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

## <a name="what-backreferences-match"></a>A que as referências inversas correspondem

Uma referência inversa refere-se à definição mais recente de um grupo (a definição mais imediatamente à esquerda, ao fazer a correspondência da esquerda para a direita). Quando um grupo faz várias capturas, uma referência inversa refere-se à captura mais recente. 

O exemplo a seguir inclui um padrão de expressão regular, `(?<1>a)(?<1>\1b)*`, que redefine o grupo nomeado \1. A tabela a seguir descreve cada padrão na expressão regular. 

Padrão | Descrição
------- | -----------
`(?<1>a)` | Corresponde ao caractere "a" e atribui o resultado ao grupo de captura chamado 1.
`(?<1>\1b)*` |Corresponde à ocorrência 0 ou 1 do grupo chamado 1 junto com "b" e atribui o resultado ao grupo de captura chamado 1. 
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<1>a)(?<1>\1b)*";
      string input = "aababb";
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("Match: " + match.Value);
         foreach (Group group in match.Groups)
            Console.WriteLine("   Group: " + group.Value);
      }
   }
}
// The example displays the following output:
//          Group: aababb
//          Group: abb
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<1>a)(?<1>\1b)*"
      Dim input As String = "aababb"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: " + match.Value)
         For Each group As Group In match.Groups
            Console.WriteLIne("   Group: " + group.Value)
         Next
      Next
   End Sub
End Module
' The example display the following output:
'          Group: aababb
'          Group: abb
```

Comparando a expressão regular com a cadeia de caracteres de entrada ("aababb"), o mecanismo de expressões regulares realiza as seguintes operações:

1. Ele começa no início da cadeia de caracteres e corresponde com êxito o “a” com a expressão `(?<1>a)`. O valor do grupo 1 agora é "a".

2. Ele avança para o segundo caractere e corresponde com êxito a cadeia de caracteres "ab" com a expressão `\1b`, ou "ab". Em seguida, atribui o resultado, "ab", a `\1`.

3. Ele avança para o quarto caractere. A expressão `(?<1>\1b)` deve ser correspondida zero ou mais vezes, de forma que corresponda com êxito a cadeia de caracteres “abb” à expressão `\1b`. Ela atribui o resultado, “abb”, a `\1`.

Neste exemplo, \* é um quantificador looping – ele é avaliado repetidamente até que o mecanismo de expressões regulares não corresponda ao padrão definido. Os quantificadores de looping não limpam definições de grupo.

Se um grupo não capturou nenhuma subcadeia de caracteres, uma referência inversa a esse grupo é indefinida e nunca corresponde. Isso é ilustrado pelo padrão de expressão regular `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b,` que é definido da seguinte maneira:

Padrão | Descrição
------- | -----------
`\b` | Começa a correspondência em um limite de palavra.
`(\p{Lu}{2})` | Corresponde a duas letras maiúsculas. Este é o primeiro grupo de captura.
`(\d{2})?` | Corresponde a zero ou uma ocorrência de dois dígitos decimais. Este é o segundo grupo de captura.
`(\p{Lu}{2})` | Corresponde a duas letras maiúsculas. Este é o terceiro grupo de captura.
`\b` | Termina a correspondência em um limite de palavra.

Uma cadeia de caracteres de entrada pode corresponder a essa expressão regular, mesmo se os dois dígitos decimais que são definidos pelo segundo grupo de captura não estiverem presentes. O exemplo a seguir mostra que, embora a correspondência seja bem-sucedida, um grupo de captura vazio foi encontrado entre dois grupos de captura com êxito.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b";
      string[] inputs = { "AA22ZZ", "AABB" };
      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
         {
            Console.WriteLine("Match in {0}: {1}", input, match.Value);
            if (match.Groups.Count > 1)
            {
               for (int ctr = 1; ctr <= match.Groups.Count - 1; ctr++)
               {
                  if (match.Groups[ctr].Success)
                     Console.WriteLine("Group {0}: {1}", 
                                       ctr, match.Groups[ctr].Value);
                  else
                     Console.WriteLine("Group {0}: <no match>", ctr);
               }
            }
         }
         Console.WriteLine();
      }      
   }
}
// The example displays the following output:
//       Match in AA22ZZ: AA22ZZ
//       Group 1: AA
//       Group 2: 22
//       Group 3: ZZ
//       
//       Match in AABB: AABB
//       Group 1: AA
//       Group 2: <no match>
//       Group 3: BB
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b"
      Dim inputs() As String = { "AA22ZZ", "AABB" }
      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("Match in {0}: {1}", input, match.Value)
            If match.Groups.Count > 1 Then
               For ctr As Integer = 1 To match.Groups.Count - 1
                  If match.Groups(ctr).Success Then
                     Console.WriteLine("Group {0}: {1}", _
                                       ctr, match.Groups(ctr).Value)
                  Else
                     Console.WriteLine("Group {0}: <no match>", ctr)
                  End If      
               Next
            End If
         End If
         Console.WriteLine()
      Next      
   End Sub
End Module
' The example displays the following output:
'       Match in AA22ZZ: AA22ZZ
'       Group 1: AA
'       Group 2: 22
'       Group 3: ZZ
'       
'       Match in AABB: AABB
'       Group 1: AA
'       Group 2: <no match>
'       Group 3: BB
```

## <a name="see-also"></a>Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)




<!--HONumber=Nov16_HO5-->


