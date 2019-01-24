---
title: Funcionalidade sem suporte
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5022c9011c2aac5b3272e359f991c40236a5673f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686693"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="fd3a2-102">Funcionalidade sem suporte</span><span class="sxs-lookup"><span data-stu-id="fd3a2-102">Unsupported Functionality</span></span>
<span data-ttu-id="fd3a2-103">Em LINQ to SQL, a seguinte funcionalidade do SQL não pode ser expostas pela conversão do Common Language Runtime existente (CLR) e construtores do.NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fd3a2-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="fd3a2-104">Embora `LIKE` não é com a conversão direta, a funcionalidade semelhante existido na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="fd3a2-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="fd3a2-105">Para obter mais informações, consulte <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd3a2-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="fd3a2-106">LINQ to SQL limitou suporte para `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="fd3a2-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="fd3a2-107">Funcionalidade semelhante existe na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="fd3a2-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="fd3a2-108">LINQ to SQL limitou suporte para `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="fd3a2-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="fd3a2-109">Para obter mais informações, consulte [métodos de System. Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="fd3a2-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3a2-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd3a2-110">See also</span></span>
- [<span data-ttu-id="fd3a2-111">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="fd3a2-111">Data Types and Functions</span></span>](data-types-and-functions.md)
