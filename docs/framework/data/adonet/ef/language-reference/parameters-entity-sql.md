---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: c8bdb54e52b4c0d189f3bff72bdb24785c1a9c27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765068"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="da6fa-102">Parâmetros (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="da6fa-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="da6fa-103">Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host.</span><span class="sxs-lookup"><span data-stu-id="da6fa-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="da6fa-104">Cada parâmetro tem um nome e um tipo.</span><span class="sxs-lookup"><span data-stu-id="da6fa-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="da6fa-105">Nomes de parâmetro são definidos em expressões de consulta com o em (@) símbolo como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="da6fa-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="da6fa-106">Isso remove a ambiguidade dos-los de nomes de propriedades ou outros nomes que são definidos na consulta.</span><span class="sxs-lookup"><span data-stu-id="da6fa-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="da6fa-107">O host linguagem que associa API fornece APIs para parâmetros de associação.</span><span class="sxs-lookup"><span data-stu-id="da6fa-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da6fa-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="da6fa-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="da6fa-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da6fa-109">See Also</span></span>  
 [<span data-ttu-id="da6fa-110">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="da6fa-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="da6fa-111">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="da6fa-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
