---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760228"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="e80de-102">Parâmetros (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e80de-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="e80de-103">Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host.</span><span class="sxs-lookup"><span data-stu-id="e80de-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="e80de-104">Cada parâmetro tem um nome e um tipo.</span><span class="sxs-lookup"><span data-stu-id="e80de-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="e80de-105">Nomes de parâmetro são definidos em expressões de consulta com o com (@) símbolo como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="e80de-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="e80de-106">Isso disambiguates os nomes das propriedades ou outros nomes que são definidos na consulta.</span><span class="sxs-lookup"><span data-stu-id="e80de-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="e80de-107">O host linguagem que associa API fornece APIs para parâmetros de associação.</span><span class="sxs-lookup"><span data-stu-id="e80de-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e80de-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e80de-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="e80de-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e80de-109">See also</span></span>

- [<span data-ttu-id="e80de-110">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e80de-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e80de-111">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e80de-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
