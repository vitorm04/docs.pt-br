---
title: "Escapes de caracteres em expressões regulares"
description: "Escapes de caracteres em expressões regulares"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 41d35531-2af9-47d4-9780-fbc1e682fbc2
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 68355baa75feb8559b921c877ea42517fc942c7e
ms.lasthandoff: 03/02/2017

---

# <a name="character-escapes-in-regular-expressions"></a>Escapes de caracteres em expressões regulares

A barra invertida (\)) em uma expressão regular indica uma das situações a seguir: 

* O caractere que segue é um caractere especial, conforme mostrado na tabela na seção a seguir. Por exemplo, **\b** é uma âncora que indica que uma correspondência da expressão regular deve começar em um limite de palavra, **\t** representa uma tabulação e **\x020** representa um espaço.

* Um caractere que, caso contrário, seria interpretado como um constructo de linguagem sem escape deve ser interpretado literalmente. Por exemplo, uma chave (**{**) inicia a definição de um quantificador, mas uma barra invertida seguida por uma chave (**\{**) indica que o mecanismo de expressão regular deve corresponder à chave. Da mesma forma, uma única barra invertida marca o início de um constructo de linguagem com escape, mas duas barras invertidas (**\\**) indicam que o mecanismo de expressão regular deve corresponder à barra invertida.

> [!NOTE]
> Escapes de caracteres são reconhecidos em padrões de expressão regulares, mas não em padrões de substituição. 
 
## <a name="character-escapes-in-net"></a>Escapes de caracteres em .NET

A tabela a seguir lista os escapes de caracteres com suporte das expressões regulares em .NET.

Caractere ou sequência | Descrição
--------------------- | ----------- 
Todos os caracteres, exceto pelos seguintes: **. $ ^ { [ ( &#124; ) * + ? \** | Caracteres diferentes dos listados na coluna **Caractere ou sequência** não têm significado especial em expressões regulares; eles correspondem a si mesmos. Os caracteres incluídos na coluna **Caractere ou sequência** são elementos especiais na linguagem de expressão regular. Para que seja feita a correspondência com eles em uma expressão regular, eles devem receber um escape ou ser incluídos em um grupo de caracteres positivo. Por exemplo, a expressão regular `\$\d+ or [$]\d+` corresponde a "$1200". 
**\a** | Corresponde a um caractere de sino (alarme), **\u0007**.
**\b** | Em uma classe de caracteres __[__*grupo de*_*caracteres*__]__, corresponde a uma barra invertida, **\ u0008**. (Consulte [Classes de caracteres em expressões regulares](classes.md).) Fora de uma classe de caracteres, **\b** é uma âncora que corresponde a um limite de palavra. (Consulte [Âncoras em expressões regulares](anchors.md).)
**\t** | Corresponde a uma tabulação, **\u0009**.
**\r** | Corresponde a um retorno de carro, **\u000D**. Observe que **\r** não é equivalente ao caractere de nova linha, **\n**.
**\v** | Corresponde a uma tabulação vertical, **\u000B**.
**\f** | Corresponde a um avanço de página, **\u000C**.
**\n** | Corresponde a uma nova linha, **\u000A**.
**\e** | Corresponde a um escape, **\u001B**.
**\**_nnn_ | Corresponde a um caractere ASCII, em que nnn são dois ou três dígitos que representam o código de caracteres octal. Por exemplo, `\040` representa um caractere de espaço. Esse constructo é interpretado como referência inversa se tiver apenas um dígito (por exemplo, `\2`) ou se corresponder ao número de um grupo de captura. Consulte ([Construtores de referência inversa em expressões regulares](backreference.md).) 
**\x**_nn_ | Corresponde a um caractere ASCII, em que *nn* é um código de caractere hexadecimal com dois dígitos.
**\c**_X_ | Corresponde a um caractere de controle ASCII, em que *X* é a letra do caractere de controle. Por exemplo, `\cC` é CTRL-C.
**\u**_nnnn_ | Corresponde a uma unidade de código UTF-16 cujo valor é *nnnn* hexadecimal. **Observação** O escape de caractere Perl 5 que é usado para especificar Unicode não tem suporte no .NET. O caractere de escape Perl 5 tem o formato **\x{###...}**, em que **####…** é uma série de dígitos hexadecimais. Em vez disso, use **\u**_nnnn_. 
**\** | Quando seguido por um caractere que não é reconhecido como um caractere com escape, corresponde a esse caractere. Por exemplo, `\*` corresponde a um asterisco (*) e é igual a `\x2A`.
 
## <a name="example"></a>Exemplo

O exemplo a seguir ilustra o uso de escapes de caracteres em uma expressão regular. Ele analisa uma cadeia de caracteres que contém os nomes das maiores cidades do mundo e suas populações em 2009. O nome de cada cidade é separado da sua população por uma tabulação (**\t**) ou uma barra vertical (| ou `\u007c`). Cidades individuais e suas populações são separadas umas das outras por um retorno de carro e uma alimentação de linha. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string delimited = @"\G(.+)[\t\u007c](.+)\r?\n";
      string input = "Mumbai, India|13,922,125\t\n" + 
                            "Shanghai, China\t13,831,900\n" + 
                            "Karachi, Pakistan|12,991,000\n" + 
                            "Delhi, India\t12,259,230\n" + 
                            "Istanbul, Turkey|11,372,613\n";
      Console.WriteLine("Population of the World's Largest Cities, 2009");
      Console.WriteLine();
      Console.WriteLine("{0,-20} {1,10}", "City", "Population");
      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, delimited))
         Console.WriteLine("{0,-20} {1,10}", match.Groups[1].Value, 
                                            match.Groups[2].Value);
   }
}
// The example displyas the following output:
//       Population of the World's Largest Cities, 2009
//       
//       City                 Population
//       
//       Mumbai, India        13,922,125
//       Shanghai, China      13,831,900
//       Karachi, Pakistan    12,991,000
//       Delhi, India         12,259,230
//       Istanbul, Turkey     11,372,613
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim delimited As String = "\G(.+)[\t\u007c](.+)\r?\n"
      Dim input As String = "Mumbai, India|13,922,125" + vbCrLf + _
                            "Shanghai, China" + vbTab + "13,831,900" + vbCrLf + _
                            "Karachi, Pakistan|12,991,000" + vbCrLf + _
                            "Delhi, India" + vbTab + "12,259,230" + vbCrLf + _
                            "Istanbul, Turkey|11,372,613" + vbCrLf
      Console.WriteLine("Population of the World's Largest Cities, 2009")
      Console.WriteLine()
      Console.WriteLine("{0,-20} {1,10}", "City", "Population")
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, delimited)
         Console.WriteLine("{0,-20} {1,10}", match.Groups(1).Value, _
                                            match.Groups(2).Value)
      Next                         
   End Sub
End Module
' The example displays the following output:
'       Population of the World's Largest Cities, 2009
'       
'       City                 Population
'       
'       Mumbai, India        13,922,125
'       Shanghai, China      13,831,900
'       Karachi, Pakistan    12,991,000
'       Delhi, India         12,259,230
'       Istanbul, Turkey     11,372,613
```

A expressão regular `\G(.+)[\t|\u007c](.+)\r?\n` é interpretada conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`\G` | Inicia a correspondência onde a última correspondência terminou.
`(.+)` | Corresponde qualquer caractere uma ou mais vezes. Este é o primeiro grupo de captura.
`[\t\u007c]` | Corresponde a uma tabulação (**\t**) ou a uma barra vertical (&#124;).
`(.+)` | Corresponde qualquer caractere uma ou mais vezes. Este é o segundo grupo de captura.
`\r?\n` | Corresponde a zero ou uma ocorrência de um retorno de carro, seguida por uma nova linha.
 
## <a name="see-also"></a>Consulte também

[Linguagem de expressão regular – referência rápida](quick-ref.md)


