---
title: "Constructos de alternância em expressões regulares"
description: "Constructos de alternância em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 59ffac4d-fc6e-461f-8783-d9f8dc88ce2c
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 2c31622ff97f30e565ed2cd82128518d04d5d1dc

---

# <a name="alternation-constructs-in-regular-expressions"></a>Constructos de alternância em expressões regulares

Os constructos de alternância modificam uma expressão regular para permitir uma correspondência condicional ou do tipo um/ou outro. O .NET dá suporte a três constructos de alternância:

* Correspondência de padrão com **|**

* Correspondência condicional com **(?(**_expressão_**)**_sim_**|**_não_**)**

* Correspondência condicional com base em um grupo capturado válido

## <a name="pattern-matching-with-"></a>Correspondência de padrão com |

Você pode usar o caractere de barra vertical (|) para corresponder a qualquer um de uma série de padrões, no qual o caractere | separa cada padrão. 

Como a classe de caracteres positivos, o caractere | pode ser usado para corresponder a qualquer um de vários caracteres únicos. O exemplo a seguir usa uma classe de caracteres positivos e um padrão do tipo um/ou outro correspondendo ao caractere | para localizar ocorrências das palavras “gray” ou “grey” em uma cadeia de caracteres. Nesse caso, o caractere | produz uma expressão regular que é mais detalhada. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Regular expression using character class.
      string pattern1 = @"\bgr[ae]y\b";
      // Regular expression using either/or.
      string pattern2 = @"\bgr(a|e)y\b";

      string input = "The gray wolf blended in among the grey rocks.";
      foreach (Match match in Regex.Matches(input, pattern1))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern2))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       'gray' found at position 4
//       'grey' found at position 35
//       
//       'gray' found at position 4
//       'grey' found at position 35           
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      ' Regular expression using character class.
      Dim pattern1 As String = "\bgr[ae]y\b"
      ' Regular expression using either/or.
      Dim pattern2 As String = "\bgr(a|e)y\b"

      Dim input As String = "The gray wolf blended in among the grey rocks."
      For Each match As Match In Regex.Matches(input, pattern1)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next      
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern2)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next      
   End Sub
End Module
' The example displays the following output:
'       'gray' found at position 4
'       'grey' found at position 35
'       
'       'gray' found at position 4
'       'grey' found at position 35 
```

A expressão regular que usa o caractere |, `\bgr(a|e)y\b,` é interpretada conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Iniciar em um limite de palavra.
`gr` | Corresponder aos caracteres "gr".
`(a|e)` | Corresponder a um "a" ou "e".
`y\b` | Corresponder a um “y” em um limite de palavra.


O caractere | também pode ser usado para executar uma correspondência do tipo um/ou outro com vários caracteres ou subexpressões, que podem incluir qualquer combinação de literais de caracteres e elementos de linguagem de expressão regular. (A classe de caracteres não fornece essa funcionalidade.) O exemplo a seguir usa o caractere | para extrair um SSN (cadastro de pessoas físicas) dos EUA, que é um número de 9 dígitos com o formato *ddd-dd-dddd* ou um EIN (Número de Identificação de Empregador) dos EUA, que é um número de 9 dígitos com o formato *dd-ddddddd*.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

A expressão regular `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretada conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Iniciar em um limite de palavra.
`(\d{2}-\d{7}|;\d{3}-\d{2}-\d{4})` | Corresponde a uma das seguintes opções: dois dígitos decimais seguidos por um hífen seguido por sete dígitos decimais ou três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais. 
`\d` | Termina a correspondência em um limite de palavra.
                                         
## <a name="conditional-matching-with-an-expression"></a>Correspondência condicional com uma expressão

Este elemento de linguagem tenta corresponder a um dos dois padrões dependendo de se ele pode corresponder a um padrão inicial. A sintaxe é:

**(?(**_expressão_**)**_sim_**|**_não_**)**

em que *expression* é o padrão inicial para correspondência, *sim* é o padrão para correspondência se a expressão for correspondida e *não* é o padrão opcional para correspondência se a *expression* for correspondida. O mecanismo de expressões regulares trata a *expressão* como uma asserção de largura zero, isto é, o mecanismo de expressões regulares não avança no fluxo de entrada após avaliar a *expressão*. Portanto, esse constructo é equivalente ao seguinte:

**(?(?**=_expressão_**)**_sim_**|**_não_**)**

em que **(?**=_expression_**)** é um constructo de asserção de largura zero. (Para obter mais informações, consulte [Constructos de agrupamento em expressões regulares](grouping.md).) Como o mecanismo de expressões regulares interpreta a *expressão* como uma âncora (uma asserção de largura zero), a *expressão* deve ser uma asserção de largura zero (para obter mais informações, confira [Âncoras em expressões regulares](anchors.md)) ou uma subexpressão que também está contida em *Sim*. Caso contrário, o padrão *sim* não pode ser correspondido. 

> [!NOTE]
> Se a *expressão* for um grupo de captura nomeado ou numerado, o constructo de alternância será interpretado como um teste de captura. Para obter mais informações, confira [Correspondência condicional com base em um grupo capturado válido](#conditional-matching-based-on-a-valid-captured-group). Em outras palavras, o mecanismo de expressões regulares não tenta corresponder a subcadeia de caracteres capturada, mas em vez disso, testa a presença ou ausência do grupo.
 

O exemplo a seguir é uma variação do exemplo que aparece na seção anterior. Ele usa a correspondência condicional para determinar se os três primeiros caracteres após um limite de palavra são dois dígitos seguidos por um hífen. Se forem, ele tenta corresponder a um EIN (Número de Identificação de Empregador) dos EUA. Se não, ele tenta corresponder a um SSN (cadastro de pessoas físicas).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

O padrão da expressão regular `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Iniciar em um limite de palavra.
`(?(\d{2}-)` | Determinar se os próximos três caracteres são compostos por dois dígitos seguidos por um hífen.
`\d{2}-\d{7}` | Se o padrão anterior corresponder, corresponder a dois dígitos seguidos por um hífen seguido por sete dígitos.
`\d{3}-\d{2}-\d{4}` | Se o padrão anterior não corresponder, corresponder a três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais. 
`\b` | Corresponder a um limite de palavra.
 
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Correspondência condicional com base em um grupo capturado válido

Este elemento de linguagem tenta corresponder a um dos dois padrões dependendo de se ele correspondeu a um grupo de captura especificado. A sintaxe é:

**(?(**_name_**)**_yes_**|**_no_**)**

ou

**(?(**_number_**)**_sim_**|**_não_**)**

em que *name* é o nome e *number* é o número de um grupo de captura, *yes* é a expressão para correspondência se o nome ou o número tiver uma correspondência e *no* é a expressão opcional para correspondência se não tiver.

Se *name* não corresponder ao nome de um grupo de captura que é usado no padrão de expressão regular, o constructo de alternância será interpretado como teste de expressão, conforme explicado na seção anterior. Normalmente, isso significa que a expressão é avaliada como `false`. Se `number` não corresponder a um grupo de captura numerado que é usado no padrão de expressão regular, o mecanismo de expressões regulares gerará um [ArgumentException](xref:System.ArgumentException).

O exemplo a seguir é uma variação do exemplo que aparece na seção anterior. Ele usa um grupo de captura chamado `n2` que consiste em dois dígitos seguidos por um hífen. O constructo de alternância testa se este grupo de captura foi correspondido na cadeia de caracteres de entrada. Em caso afirmativo, o constructo de alternância tenta corresponder aos sete últimos dígitos de um EIN (Número de Identificação de Empregador) dos EUA. Se não tiver, ele tenta corresponder a um SSN (cadastro de pessoas físicas).

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
```

O padrão da expressão regular `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` é interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | -----------
`\b` | Iniciar em um limite de palavra.
`(?<n2>\d{2}-)*` | Corresponder a zero ou uma ocorrência de dois dígitos seguidos por um hífen. Atribua um nome ao grupo de captura `n2`.
`(?(n2)` | Testar se `n2` foi correspondido na cadeia de caracteres de entrada. 
`)\d{7}` | Se `n2` tiver sido correspondido, corresponder a sete dígitos decimais.
`|;\d{3}-\d{2}-\d{4}` | Se `n2` não tiver sido correspondido, corresponder a três dígitos decimais, um hífen, dois dígitos decimais, outro hífen e quatro dígitos decimais. 
`\b` | Corresponder a um limite de palavra.
 
Uma variação desse exemplo que usa um grupo numerado em vez de um grupo nomeado é mostrada no exemplo a seguir. O padrão da expressão regular é `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example display the following output:
//       Matches for \b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)




<!--HONumber=Nov16_HO4-->


