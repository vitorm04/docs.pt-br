---
title: Executando operações de cadeia de caracteres que não levam em conta a cultura
ms.date: 08/22/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 748b4170e9e4c0df048c542d06bcb64a56ccf677
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254639"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="e3f85-102">Executando operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="e3f85-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="e3f85-103">A maioria dos métodos do .NET Framework que executam operações de cadeia de caracteres sensíveis à cultura fornece, por padrão, sobrecargas de método que permitem que você especifique explicitamente a cultura a ser usada passando um parâmetro <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="e3f85-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="e3f85-104">Essas sobrecargas permitem que você elimine variações culturais em mapeamentos de caso e em regras de classificação, e garante resultados insensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="e3f85-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="e3f85-105">Esta seção fornece os seguintes tópicos para demonstrar como executar operações de cadeia de caracteres insensíveis à cultura usando métodos do .NET Framework que são sensíveis à cultura por padrão.</span><span class="sxs-lookup"><span data-stu-id="e3f85-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3f85-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e3f85-106">In this section</span></span>  
 [<span data-ttu-id="e3f85-107">Executando comparações de cadeias de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="e3f85-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="e3f85-108">Descreve como usar os métodos <xref:System.String.Compare%2A?displayProperty=nameWithType> e <xref:System.String.CompareTo%2A?displayProperty=nameWithType> para executar comparações de cadeia de caracteres insensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="e3f85-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="e3f85-109">Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="e3f85-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="e3f85-110">Descreve como usar os métodos <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> e <xref:System.Char.ToLower%2A?displayProperty=nameWithType> para executar alterações na capitalização insensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="e3f85-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="e3f85-111">Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções</span><span class="sxs-lookup"><span data-stu-id="e3f85-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="e3f85-112">Descreve como usar a classe <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider>, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> e <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> para executar operações insensíveis à cultura em coletas.</span><span class="sxs-lookup"><span data-stu-id="e3f85-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="e3f85-113">Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes</span><span class="sxs-lookup"><span data-stu-id="e3f85-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="e3f85-114">Descreve como usar os métodos <xref:System.Array.Sort%2A?displayProperty=nameWithType> e <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> para executar operações insensíveis à cultura em matrizes.</span><span class="sxs-lookup"><span data-stu-id="e3f85-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e3f85-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e3f85-115">Related sections</span></span>  
 [<span data-ttu-id="e3f85-116">Operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="e3f85-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="e3f85-117">Descreve por que você deve estar ciente da cultura ao executar operações em cadeias de caracteres, e fornece diretrizes para quando executar operações sensíveis à cultura e quando executar operações insensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="e3f85-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3f85-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3f85-118">See also</span></span>

- [<span data-ttu-id="e3f85-119">Classificação de tabelas de peso</span><span class="sxs-lookup"><span data-stu-id="e3f85-119">Sorting Weight Tables</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=10921)
