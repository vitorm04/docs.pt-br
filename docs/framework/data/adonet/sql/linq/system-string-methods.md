---
title: "Métodos de System.String"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3cfddba1bfa7bf7cefba917be0026b1c366f3513
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="systemstring-methods"></a><span data-ttu-id="c6dcd-102">Métodos de System.String</span><span class="sxs-lookup"><span data-stu-id="c6dcd-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c6dcd-103"> não oferece suporte aos seguintes métodos de <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="c6dcd-103"> does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="c6dcd-104">Métodos sem suporte de System.String em geral</span><span class="sxs-lookup"><span data-stu-id="c6dcd-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="c6dcd-105">Métodos sem suporte de <xref:System.String> geralmente:</span><span class="sxs-lookup"><span data-stu-id="c6dcd-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
-   <span data-ttu-id="c6dcd-106">Sobrecargas de reconhecimento de cultura (métodos que usam um `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).</span><span class="sxs-lookup"><span data-stu-id="c6dcd-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
-   <span data-ttu-id="c6dcd-107">Métodos que usam ou gerenciar uma matriz de `char` .</span><span class="sxs-lookup"><span data-stu-id="c6dcd-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="c6dcd-108">Métodos sem suporte estático de System.String</span><span class="sxs-lookup"><span data-stu-id="c6dcd-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="c6dcd-109">Métodos sem suporte estático de System.String</span><span class="sxs-lookup"><span data-stu-id="c6dcd-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="c6dcd-110">Métodos sem suporte de não estático de System.String</span><span class="sxs-lookup"><span data-stu-id="c6dcd-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="c6dcd-111">Métodos sem suporte de não estático de System.String</span><span class="sxs-lookup"><span data-stu-id="c6dcd-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="c6dcd-112">Diferenças do .NET</span><span class="sxs-lookup"><span data-stu-id="c6dcd-112">Differences from .NET</span></span>  
  
-   <span data-ttu-id="c6dcd-113">Consultas não esclarecem os agrupamentos do SQL Server que podem ser aplicado no servidor, e portanto fornecerão comparações que levam confidenciais, sem diferenciação de maiúsculas e minúsculas por padrão.</span><span class="sxs-lookup"><span data-stu-id="c6dcd-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="c6dcd-114">Esse comportamento difere de opção, semântica maiúsculas de minúsculas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6dcd-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="c6dcd-115">Quando `LastIndexOf` retorna 0, a cadeia de caracteres é `NULL` ou a posição encontrada é 0.</span><span class="sxs-lookup"><span data-stu-id="c6dcd-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
-   <span data-ttu-id="c6dcd-116">Os resultados inesperados podem ser retornados de concatenação ou outras operações em cadeias de caracteres de comprimento fixo (`CHAR`, `NCHAR`), porque esses tipos têm automaticamente o preenchimento aplicado ao base de dados.</span><span class="sxs-lookup"><span data-stu-id="c6dcd-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
-   <span data-ttu-id="c6dcd-117">Porque muitos métodos, como `Replace`, `ToLower`, `ToUpper`, e o indexador de caracteres, não têm nenhuma conversão válido para `TEXT` ou colunas e XML de `NTEXT` , `SqlExceptions` ocorre se traduzido normalmente.</span><span class="sxs-lookup"><span data-stu-id="c6dcd-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="c6dcd-118">Esse comportamento é considerado aceitável para esses tipos.</span><span class="sxs-lookup"><span data-stu-id="c6dcd-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="c6dcd-119">No entanto, todas as operações de cadeia de caracteres devem corresponder a semântica do Common Language Runtime (CLR) para `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, e `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="c6dcd-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6dcd-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6dcd-120">See Also</span></span>  
 [<span data-ttu-id="c6dcd-121">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="c6dcd-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
