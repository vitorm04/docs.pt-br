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
# <a name="padding-strings-in-net"></a><span data-ttu-id="b2dbd-102">Como preencher cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="b2dbd-102">Padding Strings in .NET</span></span>
<span data-ttu-id="b2dbd-103">Use um dos métodos <xref:System.String> a seguir para criar uma nova cadeia de caracteres que consista em uma cadeia de caracteres original preenchida com caracteres à esquerda ou à direita até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="b2dbd-104">O caractere de preenchimento pode ser espaços ou um caractere especificado e, consequentemente, parece estar alinhado à direita ou à esquerda.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="b2dbd-105">Nome do método</span><span class="sxs-lookup"><span data-stu-id="b2dbd-105">Method name</span></span>|<span data-ttu-id="b2dbd-106">Use</span><span class="sxs-lookup"><span data-stu-id="b2dbd-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="b2dbd-107">Acrescenta uma cadeia de caracteres com caracteres à esquerda até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="b2dbd-108">Acrescenta uma cadeia de caracteres com caracteres à direita até um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="b2dbd-109">PadLeft</span><span class="sxs-lookup"><span data-stu-id="b2dbd-109">PadLeft</span></span>  
 <span data-ttu-id="b2dbd-110">O método <xref:System.String.PadLeft%2A?displayProperty=nameWithType> cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à esquerda suficientes para uma cadeia de caracteres original atingir um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="b2dbd-111">O método <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> usa o espaço em branco como o caractere de preenchimento, e o método <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> permite que você especifique seus próprios caracteres de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="b2dbd-112">O exemplo de código a seguir usa o método <xref:System.String.PadLeft%2A> para criar uma nova cadeia de caracteres com vinte caracteres de comprimento.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="b2dbd-113">O exemplo exibe “`--------Hello World!`” no console.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="b2dbd-114">PadRight</span><span class="sxs-lookup"><span data-stu-id="b2dbd-114">PadRight</span></span>  
 <span data-ttu-id="b2dbd-115">O método <xref:System.String.PadRight%2A?displayProperty=nameWithType> cria uma nova cadeia de caracteres concatenando caracteres de preenchimento à esquerda suficientes para uma cadeia de caracteres original atingir um comprimento total especificado.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="b2dbd-116">O método <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> usa o espaço em branco como o caractere de preenchimento, e o método <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> permite que você especifique seus próprios caracteres de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="b2dbd-117">O exemplo de código a seguir usa o método <xref:System.String.PadRight%2A> para criar uma nova cadeia de caracteres com vinte caracteres de comprimento.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="b2dbd-118">O exemplo exibe “`Hello World!--------`” no console.</span><span class="sxs-lookup"><span data-stu-id="b2dbd-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b2dbd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2dbd-119">See Also</span></span>  
 [<span data-ttu-id="b2dbd-120">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="b2dbd-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
