---
title: Paginação (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 946e7da12481eb7dac880d6ce8a56b546bdcd822
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="paging-entity-sql"></a>Paginação (Entity SQL)
Paginação física pode ser executada usando o [ignorar](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) e [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) subcláusulas no [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula. Para executar a físico paginação deterministically, você deve usar a SKIP e o LIMIT. Se você quiser restringir o número de linhas no resultado de uma maneira não determinsitic, você deve usar [superior](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md). A TOP e SKIP/LIMIT são mutuamente exclusivos.  
  
## <a name="top-overview"></a>Visão geral TOP  
 A cláusula SELECT pode ter uma cláusula as subjanelas TOP opcional após o modificador opcional de ALL/DISTINCT. A cláusula subpropriedades TOP especifica que apenas definir primeiro as linhas será retornado do resultado da consulta. Para obter mais informações, consulte [superior](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Visão geral de SKIP e de LIMIT  
 A SKIP e o LIMIT são parte da cláusula ORDER BY. Se uma subpropriedades cláusula de expressão de SKIP está presente em uma cláusula ORDER BY, os resultados serão classificados de acordo com a especificação do tipo e o conjunto de resultados incluirá as fileiras a partir da linha seguinte logo após a expressão de SKIP. Por exemplo, a SKIP 5 ignorará as primeiras cinco linhas e retornará a sexta linha avançar. Se uma subcláusula de expressão LIMIT estiver presente em uma cláusula ORDER BY, a consulta será classificada de acordo com a especificação de classificação e o número de linhas resultante será restrito pela expressão LIMIT. Por exemplo, o LIMIT 5 restringirá o conjunto de resultados a instâncias ou cinco linhas. A SKIP e o LIMIT não têm que ser usados juntos; você pode usar apenas a SKIP ou apenas o LIMIT com cláusula ORDER BY. Para mais informações, consulte os seguintes tópicos:  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Como: resultados da página por meio de consulta](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
