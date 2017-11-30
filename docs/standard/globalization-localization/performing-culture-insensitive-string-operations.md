---
title: "Executando operações de cadeia de caracteres que não levam em conta a cultura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e703e9adc531b7d1695d3e9bbed61a2c0f62ad31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="b0b1c-102">Executando operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="b0b1c-102">Performing Culture-Insensitive String Operations</span></span>
<span data-ttu-id="b0b1c-103">A maioria dos métodos do .NET Framework que executam operações de cadeia de caracteres sensíveis à cultura por padrão fornecem sobrecargas de método que permitem que você especifique explicitamente a cultura a ser usado para passar um <xref:System.Globalization.CultureInfo> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b0b1c-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="b0b1c-104">Essas sobrecargas permitem que você eliminar variações culturais no caso de mapeamentos e classificar as regras e garante resultados não levam em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="b0b1c-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="b0b1c-105">Esta seção fornece os seguintes tópicos para demonstrar como executar operações de cadeia de caracteres de cultura usando métodos do .NET Framework que são sensíveis à cultura por padrão.</span><span class="sxs-lookup"><span data-stu-id="b0b1c-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0b1c-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b0b1c-106">In This Section</span></span>  
 [<span data-ttu-id="b0b1c-107">Executando comparações de cadeias de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="b0b1c-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="b0b1c-108">Descreve como usar o <xref:System.String.Compare%2A?displayProperty=nameWithType> e <xref:System.String.CompareTo%2A?displayProperty=nameWithType> métodos para executar comparações de cadeia de caracteres de cultura.</span><span class="sxs-lookup"><span data-stu-id="b0b1c-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="b0b1c-109">Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="b0b1c-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="b0b1c-110">Descreve como usar o <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, e <xref:System.Char.ToLower%2A?displayProperty=nameWithType> métodos para realizar alterações não levam em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="b0b1c-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="b0b1c-111">Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções</span><span class="sxs-lookup"><span data-stu-id="b0b1c-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="b0b1c-112">Descreve como usar o <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> classe <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> e <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> para executar operações não levam em conta a cultura em coleções.</span><span class="sxs-lookup"><span data-stu-id="b0b1c-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="b0b1c-113">Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes</span><span class="sxs-lookup"><span data-stu-id="b0b1c-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="b0b1c-114">Descreve como usar o <xref:System.Array.Sort%2A?displayProperty=nameWithType> e <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> métodos para executar operações não levam em conta a cultura em matrizes.</span><span class="sxs-lookup"><span data-stu-id="b0b1c-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b0b1c-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b0b1c-115">Related Sections</span></span>  
 [<span data-ttu-id="b0b1c-116">Operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="b0b1c-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="b0b1c-117">Descreve por que você deve estar ciente da cultura ao executar operações em cadeias de caracteres e fornece diretrizes para quando executar operações sensíveis à cultura e quando executar operações não levam em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="b0b1c-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>
