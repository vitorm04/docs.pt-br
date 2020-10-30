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
ms.openlocfilehash: 0f7e8dde395feb548e6808547a223a3fa8855561
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063905"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="e9c20-102">Executando operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="e9c20-102">Performing culture-insensitive string operations</span></span>

<span data-ttu-id="e9c20-103">A maioria dos métodos .NET que executam operações de cadeia de caracteres de cultura, por padrão, fornece sobrecargas de método que permitem especificar explicitamente a cultura a ser usada passando um <xref:System.Globalization.CultureInfo> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e9c20-103">Most .NET methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="e9c20-104">Essas sobrecargas permitem que você elimine variações culturais em mapeamentos de caso e em regras de classificação, e garante resultados insensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="e9c20-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="e9c20-105">Esta seção fornece os seguintes artigos para demonstrar como executar operações de cadeia de caracteres que não diferenciam culturas usando métodos .NET que são sensíveis à cultura por padrão.</span><span class="sxs-lookup"><span data-stu-id="e9c20-105">This section provides the following articles to demonstrate how to perform culture-insensitive string operations using .NET methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9c20-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e9c20-106">In this section</span></span>  
 [<span data-ttu-id="e9c20-107">Executando comparações de cadeias de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="e9c20-107">Performing Culture-Insensitive String Comparisons</span></span>](performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="e9c20-108">Descreve como usar os métodos <xref:System.String.Compare%2A?displayProperty=nameWithType> e <xref:System.String.CompareTo%2A?displayProperty=nameWithType> para executar comparações de cadeia de caracteres insensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="e9c20-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="e9c20-109">Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="e9c20-109">Performing Culture-Insensitive Case Changes</span></span>](performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="e9c20-110">Descreve como usar os métodos <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> e <xref:System.Char.ToLower%2A?displayProperty=nameWithType> para executar alterações na capitalização insensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="e9c20-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="e9c20-111">Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções</span><span class="sxs-lookup"><span data-stu-id="e9c20-111">Performing Culture-Insensitive String Operations in Collections</span></span>](performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="e9c20-112">Descreve como usar a classe <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider>, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> e <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> para executar operações insensíveis à cultura em coletas.</span><span class="sxs-lookup"><span data-stu-id="e9c20-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="e9c20-113">Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes</span><span class="sxs-lookup"><span data-stu-id="e9c20-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="e9c20-114">Descreve como usar os métodos <xref:System.Array.Sort%2A?displayProperty=nameWithType> e <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> para executar operações insensíveis à cultura em matrizes.</span><span class="sxs-lookup"><span data-stu-id="e9c20-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9c20-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e9c20-115">Related sections</span></span>  
 [<span data-ttu-id="e9c20-116">Operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="e9c20-116">Culture-Insensitive String Operations</span></span>](culture-insensitive-string-operations.md)  
 <span data-ttu-id="e9c20-117">Descreve por que você deve estar ciente da cultura ao executar operações em cadeias de caracteres, e fornece diretrizes para quando executar operações sensíveis à cultura e quando executar operações insensíveis à cultura.</span><span class="sxs-lookup"><span data-stu-id="e9c20-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9c20-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9c20-118">See also</span></span>

- [<span data-ttu-id="e9c20-119">Classificação de tabelas de peso (para .NET em sistemas Windows)</span><span class="sxs-lookup"><span data-stu-id="e9c20-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="e9c20-120">Tabela do elemento de ordenação Unicode padrão (para .NET Core em Linux e macOS)</span><span class="sxs-lookup"><span data-stu-id="e9c20-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
