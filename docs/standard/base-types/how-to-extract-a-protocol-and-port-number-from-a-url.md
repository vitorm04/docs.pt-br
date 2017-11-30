---
title: "Como extrair um protocolo e um número de porta de uma URL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10ab05ac8b24c0658be2f27809137c6b0bd4834f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>Como extrair um protocolo e um número de porta de uma URL
O exemplo a seguir extrai um protocolo e um número da porta de uma URL.  
  
## <a name="example"></a>Exemplo  
 O exemplo usa o <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> método para retornar o protocolo seguido por dois-pontos seguido pelo número da porta.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 O padrão de expressão regular `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` pode ser interpretado conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`^`|Comece a correspondência no início da cadeia de caracteres.|  
|`(?<proto>\w+)`|Corresponde a um ou mais caracteres de palavra. Este grupo `proto`.|  
|`://`|Fazer a correspondência de um sinal de dois-pontos seguido por duas barras "/".|  
|`[^/]+?`|Fazer a correspondência de uma ou mais ocorrências (mas o menor número possível) de qualquer caractere que não seja uma barra "/".|  
|`(?<port>:\d+)?`|Fazer a correspondência de zero ou uma ocorrência de um sinal de dois-pontos seguido por um ou mais caracteres de dígito. Este grupo `port`.|  
|`/`|Fazer a correspondência de uma barra "/".|  
  
 O <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> método expande o `${proto}${port}` sequência de substituição, que concatena o valor dos dois grupos nomeados capturados no padrão de expressão regular. É uma alternativa conveniente para concatenar explicitamente as cadeias de caracteres recuperadas do objeto de coleção retornado pelo <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> propriedade.  
  
 O exemplo usa o <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> método com duas substituições, `${proto}` e `${port}`, para incluir os grupos capturados na cadeia de saída. Você pode recuperar os grupos capturados a correspondência de <xref:System.Text.RegularExpressions.GroupCollection> em vez disso, como mostra o seguinte código do objeto.  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Expressões regulares do .NET](../../../docs/standard/base-types/regular-expressions.md)
