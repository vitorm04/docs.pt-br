---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249582"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="60638-102">Parâmetros (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="60638-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="60638-103">Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host.</span><span class="sxs-lookup"><span data-stu-id="60638-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="60638-104">Cada parâmetro tem um nome e um tipo.</span><span class="sxs-lookup"><span data-stu-id="60638-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="60638-105">Os nomes de parâmetro são definidos em expressões de consulta com o símbolo arroba (@) como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="60638-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="60638-106">Isso os desambigua dos nomes das propriedades ou de outros nomes definidos na consulta.</span><span class="sxs-lookup"><span data-stu-id="60638-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="60638-107">O host linguagem que associa API fornece APIs para parâmetros de associação.</span><span class="sxs-lookup"><span data-stu-id="60638-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60638-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60638-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="60638-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60638-109">See also</span></span>

- [<span data-ttu-id="60638-110">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="60638-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="60638-111">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="60638-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
