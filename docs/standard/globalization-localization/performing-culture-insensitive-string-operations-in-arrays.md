---
title: "Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b4e040ed379cdbf43fbe8b2c4379fdd4dc781f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes
Sobrecargas do <xref:System.Array.Sort%2A?displayProperty=nameWithType> e <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> os métodos executam sensíveis à cultura classifica por padrão usando o <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriedade. Sensíveis à cultura retornado por esses métodos podem variar com a cultura devido a diferenças em ordens de classificação. Para eliminar o comportamento de sensíveis à cultura, use uma das sobrecargas do método que aceita um `comparer` parâmetro. O `comparer` parâmetro especifica o <xref:System.Collections.IComparer> implementação para usar ao comparar os elementos na matriz. Para o parâmetro, especifique uma classe de comparador invariável personalizado que usa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Um exemplo de uma classe personalizada comparador invariável é fornecido no subtópico "Usando a classe SortedList" o [executando operações de cadeia de caracteres de cultura em coleções](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tópico.  
  
 **Observação** passando **CultureInfo. InvariantCulture** para uma comparação método realizar uma comparação sem diferenciação de cultura. No entanto, ele não causa uma comparação não linguística, por exemplo, para caminhos de arquivos, chaves do registro e variáveis de ambiente. Não oferece suporte a decisões de segurança com base no resultado da comparação. Para obter uma comparação não linguística ou suporte para decisões de segurança com base no resultado, o aplicativo deve usar um método de comparação que aceita um <xref:System.StringComparison> valor. O aplicativo deve passar <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [Executando operações de cadeia de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
