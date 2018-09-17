---
title: 'Exemplo de expressão regular: Alterando formatos de data'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c26608115a22a5402d671c5f5e51c75442a0a5
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45668867"
---
# <a name="regular-expression-example-changing-date-formats"></a>Exemplo de expressão regular: Alterando formatos de data
O exemplo de código a seguir usa o método <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> para substituir datas com o formato *mm*/*dd*/*aa* por datas com o formato *dd*-*mm*-*aa*.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 O código a seguir mostra como o método `MDYToDMY` pode ser chamado em um aplicativo.  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a>Comentários  
 O padrão de expressão regular `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` é interpretado conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\b`|Começa a correspondência em um limite de palavra.|  
|`(?<month>\d{1,2})`|Corresponder a um ou dois dígitos decimais. Este é o grupo capturado do `month`.|  
|`/`|Corresponde à barra.|  
|`(?<day>\d{1,2})`|Corresponder a um ou dois dígitos decimais. Este é o grupo capturado do `day`.|  
|`/`|Corresponde à barra.|  
|`(?<year>\d{2,4})`|Corresponder de dois a quatro dígitos decimais. Este é o grupo capturado do `year`.|  
|`\b`|Termina a correspondência em um limite de palavra.|  
  
 O padrão `${day}-${month}-${year}` define a cadeia de caracteres de substituição conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`$(day)`|Adicionar a cadeia de caracteres capturada pelo grupo de captura `day`.|  
|`-`|Adicionar um hífen.|  
|`$(month)`|Adicionar a cadeia de caracteres capturada pelo grupo de captura `month`.|  
|`-`|Adicionar um hífen.|  
|`$(year)`|Adicionar a cadeia de caracteres capturada pelo grupo de captura `year`.|  
  
## <a name="see-also"></a>Consulte também

- [Expressões regulares do .NET](../../../docs/standard/base-types/regular-expressions.md)
