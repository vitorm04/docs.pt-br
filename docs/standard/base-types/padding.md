---
title: Como preencher cadeias de caracteres no .NET
ms.custom: 
ms.date: 03/15/2018
ms.prod: .net
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
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bf90c841c8fff21dd423fcd19613b5eb46a2c80c
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2018
---
# <a name="padding-strings-in-net"></a>Como preencher cadeias de caracteres no .NET

Use um dos métodos <xref:System.String> a seguir para criar uma nova cadeia de caracteres que consista em uma cadeia de caracteres original preenchida com caracteres à esquerda ou à direita até um comprimento total especificado. O caractere de preenchimento pode ser um espaço ou um caractere especificado. A cadeia de caracteres resultante parece estar alinhada à direita ou à esquerda. Se o tamanho da cadeia de caracteres original já for igual ou maior que o tamanho total desejado, os métodos de preenchimento retornarão a cadeia de caracteres original inalterada. Para obter mais informações, confira as seções **Retornos** das duas sobrecargas dos métodos <xref:System.String.PadLeft%2A?displayProperty=nameWithType> e <xref:System.String.PadRight%2A?displayProperty=nameWithType>.
  
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
