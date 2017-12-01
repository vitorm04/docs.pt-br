---
title: Preenchendo cadeias de caracteres no .NET
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
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a>Preenchendo cadeias de caracteres no .NET
Use um dos seguintes <xref:System.String> métodos para criar uma nova cadeia de caracteres que consiste em uma cadeia de caracteres original que é preenchida com à esquerda ou à direita de caracteres para um tamanho total especificado. O caractere de preenchimento pode ser espaços ou um caractere especificado e, consequentemente, parece estar alinhado à direita ou à esquerda.  
  
|Nome do método|Use|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Acrescenta uma cadeia de caracteres com caracteres à esquerda até um comprimento total especificado.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Acrescenta uma cadeia de caracteres com caracteres à direita até um comprimento total especificado.|  
  
## <a name="padleft"></a>PadLeft  
 O <xref:System.String.PadLeft%2A?displayProperty=nameWithType> método cria uma nova cadeia de caracteres concatenando caracteres suficientes preenchimento à esquerda para uma cadeia de caracteres original para atingir um tamanho total especificado. O <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> método usa o espaço em branco como o caractere de preenchimento e o <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> método permite que você especifique seus próprios caracteres de preenchimento.  
  
 O seguinte exemplo de código usa o <xref:System.String.PadLeft%2A> método para criar uma nova cadeia de caracteres que tem vinte caracteres. O exemplo exibe “`--------Hello World!`” no console.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 O <xref:System.String.PadRight%2A?displayProperty=nameWithType> método cria uma nova cadeia de caracteres concatenando caracteres de preenchimento suficientes para uma cadeia de caracteres original para atingir um tamanho total especificado. O <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> método usa o espaço em branco como o caractere de preenchimento e o <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> método permite que você especifique seus próprios caracteres de preenchimento.  
  
 O seguinte exemplo de código usa o <xref:System.String.PadRight%2A> método para criar uma nova cadeia de caracteres que tem vinte caracteres. O exemplo exibe “`Hello World!--------`” no console.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Operações básicas de cadeias de caracteres](../../../docs/standard/base-types/basic-string-operations.md)
