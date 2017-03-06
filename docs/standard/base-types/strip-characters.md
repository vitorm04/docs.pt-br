---
title: "Como retirar caracteres inválidos de uma cadeia de caracteres"
description: "Como retirar caracteres inválidos de uma cadeia de caracteres"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: f1df4967-7887-41d2-b60f-0da9be67c8fa
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 59824a372405036c2ab6fac2730b67c9c2dfa7f4
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-strip-invalid-characters-from-a-string"></a>Como retirar caracteres inválidos de uma cadeia de caracteres

O exemplo a seguir usa o método [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) estático para retirar caracteres inválidos de uma cadeia de caracteres. 

## <a name="example"></a>Exemplo

Você pode usar o método `CleanInput` definido neste exemplo para retirar caracteres potencialmente prejudiciais que tenham sido inseridos em um campo de texto que aceita entrada do usuário. Nesse caso, o `CleanInput` remove todos os caracteres não alfanuméricos, exceto pontos (.), arrobas (@) e hifens (-) e retorna a cadeia de caracteres restante. No entanto, você pode modificar o padrão da expressão regular para que ela elimine qualquer caractere que não deve ser incluído em uma cadeia de caracteres de entrada.

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
    static string CleanInput(string strIn)
    {
        // Replace invalid characters with empty strings.
        try {
           return Regex.Replace(strIn, @"[^\w\.@-]", "", 
                                RegexOptions.None, TimeSpan.FromSeconds(1.5)); 
        }
        // If we timeout when replacing invalid characters, 
        // we should return Empty.
        catch (RegexMatchTimeoutException) {
           return String.Empty;   
        }
    }
}
```

```vb
Imports System.Text.RegularExpressions

Module Example
    Function CleanInput(strIn As String) As String
        ' Replace invalid characters with empty strings.
        Try
           Return Regex.Replace(strIn, "[^\w\.@-]", "")
        ' If we timeout when replacing invalid characters, 
        ' we should return String.Empty.
        Catch e As RegexMatchTimeoutException
           Return String.Empty         
        End Try
    End Function
End Module
```

O padrão da expressão regular `[^\w\.@-]` corresponde a qualquer caractere que não seja um caractere de palavra, um ponto, um símbolo de @ ou um hífen. Um caractere de palavra é qualquer letra, dígito decimal ou conector de pontuação, como um sublinhado. Qualquer caractere que corresponde a esse padrão é substituído pelo [String.Empty](xref:System.String.Empty), que é a cadeia de caracteres definida pelo padrão de substituição. Para permitir caracteres adicionais na entrada do usuário, adicione esses caracteres à classe de caractere no padrão de expressão regular. Por exemplo, o padrão de expressão regular `[^\w\.@-\\%]` também permite um símbolo percentual e uma barra invertida em uma cadeia de caracteres de entrada.

## <a name="see-also"></a>Consulte também

[Expressões regulares do .NET](regular-expressions.md)

[Exemplos de expressões regulares](regex-examples.md)

