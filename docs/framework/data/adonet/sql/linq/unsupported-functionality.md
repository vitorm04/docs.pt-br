---
title: Funcionalidade sem suporte
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 18a1a8f33a9360b4299648bcd329f4c5f2e7de88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097867"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="128b7-102">Funcionalidade sem suporte</span><span class="sxs-lookup"><span data-stu-id="128b7-102">Unsupported Functionality</span></span>
<span data-ttu-id="128b7-103">Em LINQ to SQL, a seguinte funcionalidade do SQL não pode ser expostas pela conversão do Common Language Runtime existente (CLR) e construtores do.NET Framework:</span><span class="sxs-lookup"><span data-stu-id="128b7-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="128b7-104">Embora `LIKE` não é com a conversão direta, a funcionalidade semelhante existido na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="128b7-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="128b7-105">Para obter mais informações, consulte <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="128b7-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="128b7-106">LINQ to SQL limitou suporte para `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="128b7-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="128b7-107">Funcionalidade semelhante existe na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="128b7-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="128b7-108">LINQ to SQL limitou suporte para `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="128b7-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="128b7-109">Para obter mais informações, consulte [métodos de System. Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="128b7-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128b7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="128b7-110">See also</span></span>

- [<span data-ttu-id="128b7-111">Tipos de dados e funções</span><span class="sxs-lookup"><span data-stu-id="128b7-111">Data Types and Functions</span></span>](data-types-and-functions.md)
