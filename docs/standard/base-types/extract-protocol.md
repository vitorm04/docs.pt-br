---
title: "Como extrair um protocolo e um número da porta de uma URL"
description: "Como extrair um protocolo e um número da porta de uma URL"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d2462fb4-6d61-44ab-8466-73f1f06c3058
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 72e0c9401406dcac4eb693b056b88a531f2a0748

---

# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Como extrair um protocolo e um número da porta de uma URL

O exemplo a seguir extrai um protocolo e um número da porta de uma URL. 

## <a name="example"></a>Exemplo

O exemplo usa o método [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) para retornar o protocolo seguido por dois-pontos seguido pelo número da porta. 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string url = "http://www.contoso.com:8080/letters/readme";

      Regex r = new Regex(@"^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/",
                          RegexOptions.None, TimeSpan.FromMilliseconds(150));
      Match m = r.Match(url);
      if (m.Success)
         Console.WriteLine(r.Match(url).Result("${proto}${port}")); 
   }
}
// The example displays the following output:
//       http:8080
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim url As String = "http://www.contoso.com:8080/letters/readme.html" 
      Dim r As New Regex("^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/",
                         RegexOptions.None, TimeSpan.FromMilliseconds(150))

      Dim m As Match = r.Match(url)
      If m.Success Then
         Console.WriteLine(r.Match(url).Result("${proto}${port}"))
      End If   
   End Sub
End Module
' The example displays the following output:
'       http:8080
```

O padrão de expressão regular `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` pode ser interpretado conforme mostrado na tabela a seguir.

Padrão | Descrição
------- | ----------- 
`^` | Comece a correspondência no início da cadeia de caracteres.
`(?<proto>\w+)` | Fazer a correspondência a um ou mais caracteres de palavra. Nomear esse grupo como “proto”.
`://` | Fazer a correspondência de um sinal de dois-pontos seguido por duas barras "/".
`[^/]+?` | Fazer a correspondência de uma ou mais ocorrências (mas o menor número possível) de qualquer caractere que não seja uma barra "/".
`(?<port>:\d+)?` | Fazer a correspondência de zero ou uma ocorrência de um sinal de dois-pontos seguido por um ou mais caracteres de dígito. Nomear esse grupo como “porta”.
`/` | Fazer a correspondência de uma barra "/".
 
O método [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) expande a sequência de substituição `${proto}${port}`, que concatena o valor dos dois grupos nomeados capturados no padrão de expressão regular. Essa é uma alternativa conveniente para concatenar explicitamente as cadeias de caracteres recuperadas do objeto da coleção retornado pela propriedade [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups).

O exemplo usa o método [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) com duas substituições, `${proto}` e `${port}`, para incluir os grupos capturados na cadeia de caracteres de saída. Você pode recuperar os grupos capturados do objeto [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) da correspondência em vez disso, conforme mostra o código a seguir.

```csharp
Console.WriteLine(m.Groups["proto"].Value + m.Groups["port"].Value); 
```

```vb
Console.WriteLine(m.Groups("proto").Value + m.Groups("port").Value)
```

## <a name="see-also"></a>Consulte também

[Expressões regulares do .NET](regular-expressions.md)

[Exemplos de expressões regulares](regex-examples.md)



<!--HONumber=Dec16_HO1-->


