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
# <a name="padding-strings-in-net"></a><span data-ttu-id="1cbca-102">Preenchendo cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="1cbca-102">Padding Strings in .NET</span></span>
<span data-ttu-id="1cbca-103">Use um dos seguintes <xref:System.String> métodos para criar uma nova cadeia de caracteres que consiste em uma cadeia de caracteres original que é preenchida com à esquerda ou à direita de caracteres para um tamanho total especificado.</span><span class="sxs-lookup"><span data-stu-id="1cbca-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="1cbca-104">O caractere de preenchimento pode ser espaços ou um caractere especificado e, consequentemente, parece estar alinhado à direita ou à esquerda.</span><span class="sxs-lookup"><span data-stu-id="1cbca-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="1cbca-105">Nome do método</span><span class="sxs-lookup"><span data-stu-id="1cbca-105">Method name</span></span>|<span data-ttu-id="1cbca-106">Use</span><span class="sxs-lookup"><span data-stu-id="1cbca-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="1cbca-107">Acrescenta uma cadeia de caracteres com caracteres à esquerda até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="1cbca-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="1cbca-108">Acrescenta uma cadeia de caracteres com caracteres à direita até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="1cbca-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="1cbca-109">PadLeft</span><span class="sxs-lookup"><span data-stu-id="1cbca-109">PadLeft</span></span>  
 <span data-ttu-id="1cbca-110">O <xref:System.String.PadLeft%2A?displayProperty=nameWithType> método cria uma nova cadeia de caracteres concatenando caracteres suficientes preenchimento à esquerda para uma cadeia de caracteres original para atingir um tamanho total especificado.</span><span class="sxs-lookup"><span data-stu-id="1cbca-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="1cbca-111">O <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> método usa o espaço em branco como o caractere de preenchimento e o <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> método permite que você especifique seus próprios caracteres de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="1cbca-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="1cbca-112">O seguinte exemplo de código usa o <xref:System.String.PadLeft%2A> método para criar uma nova cadeia de caracteres que tem vinte caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cbca-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="1cbca-113">O exemplo exibe “`--------Hello World!`” no console.</span><span class="sxs-lookup"><span data-stu-id="1cbca-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="1cbca-114">PadRight</span><span class="sxs-lookup"><span data-stu-id="1cbca-114">PadRight</span></span>  
 <span data-ttu-id="1cbca-115">O <xref:System.String.PadRight%2A?displayProperty=nameWithType> método cria uma nova cadeia de caracteres concatenando caracteres de preenchimento suficientes para uma cadeia de caracteres original para atingir um tamanho total especificado.</span><span class="sxs-lookup"><span data-stu-id="1cbca-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="1cbca-116">O <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> método usa o espaço em branco como o caractere de preenchimento e o <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> método permite que você especifique seus próprios caracteres de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="1cbca-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="1cbca-117">O seguinte exemplo de código usa o <xref:System.String.PadRight%2A> método para criar uma nova cadeia de caracteres que tem vinte caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cbca-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="1cbca-118">O exemplo exibe “`Hello World!--------`” no console.</span><span class="sxs-lookup"><span data-stu-id="1cbca-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1cbca-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cbca-119">See Also</span></span>  
 [<span data-ttu-id="1cbca-120">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="1cbca-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
