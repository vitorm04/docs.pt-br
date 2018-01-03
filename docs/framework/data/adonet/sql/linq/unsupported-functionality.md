---
title: Funcionalidade sem suporte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 244d9ee7accd3686729542d0f0a15966bcde7b78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="unsupported-functionality"></a><span data-ttu-id="e8418-102">Funcionalidade sem suporte</span><span class="sxs-lookup"><span data-stu-id="e8418-102">Unsupported Functionality</span></span>
<span data-ttu-id="e8418-103">Em LINQ to SQL, a seguinte funcionalidade do SQL não pode ser expostas pela conversão do Common Language Runtime existente (CLR) e construtores do.NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e8418-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="e8418-104">Embora `LIKE` não é com a conversão direta, a funcionalidade semelhante existido na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="e8418-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="e8418-105">Para obter mais informações, consulte <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8418-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="e8418-106">LINQ to SQL limitou suporte para `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="e8418-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="e8418-107">Funcionalidade semelhante existe na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="e8418-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="e8418-108">LINQ to SQL limitou suporte para `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="e8418-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="e8418-109">Para obter mais informações, consulte [métodos de System. Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e8418-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8418-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8418-110">See Also</span></span>  
 [<span data-ttu-id="e8418-111">Funções e tipos de dados</span><span class="sxs-lookup"><span data-stu-id="e8418-111">Data Types and Functions</span></span>](data-types-and-functions.md)
