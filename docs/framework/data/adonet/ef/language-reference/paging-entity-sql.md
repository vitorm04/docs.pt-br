---
title: Paginação (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 25d52734c30e087629be9923a43e720f94c96d04
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249572"
---
# <a name="paging-entity-sql"></a>Paginação (Entity SQL)
A paginação física pode ser executada usando as subcláusulas [Skip](skip-entity-sql.md) e [Limit](limit-entity-sql.md) na cláusula [order by](order-by-entity-sql.md) . Para executar a físico paginação deterministically, você deve usar a SKIP e o LIMIT. Se você quiser restringir o número de linhas no resultado de uma forma não determinística, deverá usar [Top](top-entity-sql.md). A TOP e SKIP/LIMIT são mutuamente exclusivos.  
  
## <a name="top-overview"></a>Visão geral TOP  
 A cláusula SELECT pode ter uma cláusula as subjanelas TOP opcional após o modificador opcional de ALL/DISTINCT. A cláusula subpropriedades TOP especifica que apenas definir primeiro as linhas será retornado do resultado da consulta. Para obter mais informações, consulte [superior](top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Visão geral de SKIP e de LIMIT  
 A SKIP e o LIMIT são parte da cláusula ORDER BY. Se uma subpropriedades cláusula de expressão de SKIP está presente em uma cláusula ORDER BY, os resultados serão classificados de acordo com a especificação do tipo e o conjunto de resultados incluirá as fileiras a partir da linha seguinte logo após a expressão de SKIP. Por exemplo, a SKIP 5 ignorará as primeiras cinco linhas e retornará a sexta linha avançar. Se uma subcláusula de expressão LIMIT estiver presente em uma cláusula ORDER BY, a consulta será classificada de acordo com a especificação de classificação e o número de linhas resultante será restrito pela expressão LIMIT. Por exemplo, o LIMIT 5 restringirá o conjunto de resultados a instâncias ou cinco linhas. A SKIP e o LIMIT não têm que ser usados juntos; você pode usar apenas a SKIP ou apenas o LIMIT com cláusula ORDER BY. Para mais informações, consulte os seguintes tópicos:  
  
- [SKIP](skip-entity-sql.md)  
  
- [LIMIT](limit-entity-sql.md)  
  
- [ORDER BY](order-by-entity-sql.md)  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
- [Visão geral do Entity SQL](entity-sql-overview.md)
- [Como: Página por meio de resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
