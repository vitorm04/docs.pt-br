---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 759452902461e1a460b69774bb33f92bbd532ed0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177508"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="68bf7-102">Parâmetros (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="68bf7-102">Parameters (Entity SQL)</span></span>

<span data-ttu-id="68bf7-103">Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host.</span><span class="sxs-lookup"><span data-stu-id="68bf7-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="68bf7-104">Cada parâmetro tem um nome e um tipo.</span><span class="sxs-lookup"><span data-stu-id="68bf7-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="68bf7-105">Os nomes de parâmetro são definidos em expressões de consulta com o símbolo arroba (@) como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="68bf7-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="68bf7-106">Isso os desambigua dos nomes das propriedades ou de outros nomes definidos na consulta.</span><span class="sxs-lookup"><span data-stu-id="68bf7-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="68bf7-107">O host linguagem que associa API fornece APIs para parâmetros de associação.</span><span class="sxs-lookup"><span data-stu-id="68bf7-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68bf7-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68bf7-108">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="68bf7-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="68bf7-109">See also</span></span>

- [<span data-ttu-id="68bf7-110">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="68bf7-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="68bf7-111">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="68bf7-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
