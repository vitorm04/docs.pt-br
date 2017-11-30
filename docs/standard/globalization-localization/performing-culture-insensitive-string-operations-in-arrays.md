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
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="8f8fc-102">Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes</span><span class="sxs-lookup"><span data-stu-id="8f8fc-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="8f8fc-103">Sobrecargas do <xref:System.Array.Sort%2A?displayProperty=nameWithType> e <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> os métodos executam sensíveis à cultura classifica por padrão usando o <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8f8fc-104">Sensíveis à cultura retornado por esses métodos podem variar com a cultura devido a diferenças em ordens de classificação.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="8f8fc-105">Para eliminar o comportamento de sensíveis à cultura, use uma das sobrecargas do método que aceita um `comparer` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="8f8fc-106">O `comparer` parâmetro especifica o <xref:System.Collections.IComparer> implementação para usar ao comparar os elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="8f8fc-107">Para o parâmetro, especifique uma classe de comparador invariável personalizado que usa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f8fc-108">Um exemplo de uma classe personalizada comparador invariável é fornecido no subtópico "Usando a classe SortedList" o [executando operações de cadeia de caracteres de cultura em coleções](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="8f8fc-109">**Observação** passando **CultureInfo. InvariantCulture** para uma comparação método realizar uma comparação sem diferenciação de cultura.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="8f8fc-110">No entanto, ele não causa uma comparação não linguística, por exemplo, para caminhos de arquivos, chaves do registro e variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="8f8fc-111">Não oferece suporte a decisões de segurança com base no resultado da comparação.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="8f8fc-112">Para obter uma comparação não linguística ou suporte para decisões de segurança com base no resultado, o aplicativo deve usar um método de comparação que aceita um <xref:System.StringComparison> valor.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="8f8fc-113">O aplicativo deve passar <xref:System.StringComparison.Ordinal>.</span><span class="sxs-lookup"><span data-stu-id="8f8fc-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8fc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f8fc-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="8f8fc-115">Executando operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="8f8fc-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
