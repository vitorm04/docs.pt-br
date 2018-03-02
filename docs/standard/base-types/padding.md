---
title: Como preencher cadeias de caracteres no .NET
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea903c1f950e7c226e043c1fa7276a66126b2512
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="padding-strings-in-net"></a>Como preencher cadeias de caracteres no .NET
Use um dos métodos <xref:System.String> a seguir para criar uma nova cadeia de caracteres que consista em uma cadeia de caracteres original preenchida com caracteres à esquerda ou à direita até um comprimento total especificado. O caractere de preenchimento pode ser espaços ou um caractere especificado e, consequentemente, parece estar alinhado à direita ou à esquerda.  
  
|Nome do método|Use|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Acrescenta uma cadeia de caracteres com caracteres à esquerda até um comprimento total especificado.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Acrescenta uma cadeia de caracteres com caracteres à direita até um comprimento total especificado.|  
  
## <a name="padleft"></a>PadLeft  
 O método <xref:System.String.PadLeft%2A?displayProperty=nameWithType> cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à esquerda suficientes para uma cadeia de caracteres original atingir um comprimento total especificado. O método <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> usa o espaço em branco como o caractere de preenchimento, e o método <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> permite que você especifique seus próprios caracteres de preenchimento.  
  
 O exemplo de código a seguir usa o método <xref:System.String.PadLeft%2A> para criar uma nova cadeia de caracteres com vinte caracteres de comprimento. O exemplo exibe “`--------Hello World!`” no console.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 O método <xref:System.String.PadRight%2A?displayProperty=nameWithType> cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à esquerda suficientes para uma cadeia de caracteres original atingir um comprimento total especificado. O método <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> usa o espaço em branco como o caractere de preenchimento, e o método <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> permite que você especifique seus próprios caracteres de preenchimento.  
  
 O exemplo de código a seguir usa o método <xref:System.String.PadRight%2A> para criar uma nova cadeia de caracteres com vinte caracteres de comprimento. O exemplo exibe “`Hello World!--------`” no console.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Operações básicas de cadeias de caracteres](../../../docs/standard/base-types/basic-string-operations.md)
