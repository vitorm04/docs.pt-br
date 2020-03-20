---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: e1bb633f7f7c7908a5f424991f20a5cd89aee5aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150008"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="33a31-102">Parâmetros (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="33a31-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="33a31-103">Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host.</span><span class="sxs-lookup"><span data-stu-id="33a31-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="33a31-104">Cada parâmetro tem um nome e um tipo.</span><span class="sxs-lookup"><span data-stu-id="33a31-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="33a31-105">Os nomes dos parâmetros são definidos em expressões de consulta com o símbolo at (@) como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="33a31-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="33a31-106">Isso os desambiguatiza dos nomes das propriedades ou outros nomes que são definidos na consulta.</span><span class="sxs-lookup"><span data-stu-id="33a31-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="33a31-107">O host linguagem que associa API fornece APIs para parâmetros de associação.</span><span class="sxs-lookup"><span data-stu-id="33a31-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33a31-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33a31-108">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="33a31-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="33a31-109">See also</span></span>

- [<span data-ttu-id="33a31-110">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="33a31-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="33a31-111">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="33a31-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
