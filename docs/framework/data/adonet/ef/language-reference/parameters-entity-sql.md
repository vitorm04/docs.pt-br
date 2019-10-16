---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 8fbca4f10a7c2c3dbaffff978a536b87d31a8df4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319424"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="fc3b8-102">Parâmetros (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fc3b8-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="fc3b8-103">Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host.</span><span class="sxs-lookup"><span data-stu-id="fc3b8-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="fc3b8-104">Cada parâmetro tem um nome e um tipo.</span><span class="sxs-lookup"><span data-stu-id="fc3b8-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="fc3b8-105">Os nomes de parâmetro são definidos em expressões de consulta com o símbolo arroba (@) como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="fc3b8-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="fc3b8-106">Isso os desambigua dos nomes das propriedades ou de outros nomes definidos na consulta.</span><span class="sxs-lookup"><span data-stu-id="fc3b8-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="fc3b8-107">O host linguagem que associa API fornece APIs para parâmetros de associação.</span><span class="sxs-lookup"><span data-stu-id="fc3b8-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc3b8-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc3b8-108">Example</span></span>  
  
```sql  
SELECT c   
      FROM LOB.Customers AS c   
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc3b8-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc3b8-109">See also</span></span>

- [<span data-ttu-id="fc3b8-110">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fc3b8-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fc3b8-111">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fc3b8-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
