---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802839"
---

> [!WARNING]
> <span data-ttu-id="5e8cd-101">Ao usar <xref:System.Text.RegularExpressions> o para processar a entrada não confiável, passe um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5e8cd-101">When using <xref:System.Text.RegularExpressions> to process untrusted input, pass a timeout.</span></span> <span data-ttu-id="5e8cd-102">Um usuário mal-intencionado pode fornecer entrada para `RegularExpressions` causar um [ataque de negação de serviço](https://www.us-cert.gov/ncas/tips/ST04-015).</span><span class="sxs-lookup"><span data-stu-id="5e8cd-102">A malicious user can provide input to `RegularExpressions` causing a [Denial-of-Service attack](https://www.us-cert.gov/ncas/tips/ST04-015).</span></span> <span data-ttu-id="5e8cd-103">ASP.NET Core APIs do Framework que usam `RegularExpressions` passar um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5e8cd-103">ASP.NET Core framework APIs that use `RegularExpressions` pass a timeout.</span></span>
