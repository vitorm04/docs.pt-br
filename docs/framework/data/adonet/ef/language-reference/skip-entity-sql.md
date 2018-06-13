---
title: IGNORAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 3b63ca6ade93331b9d1c3ef3e8de15ed520864dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766576"
---
# <a name="skip-entity-sql"></a>IGNORAR (Entity SQL)
Você pode executar a físico paginação usando a cláusula subpropriedades de SKIP na cláusula GROUP BY. A SKIP não pode ser usada separada de cláusula GROUP BY.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 O número de itens para ignorar.  
  
## <a name="remarks"></a>Comentários  
 Se uma subpropriedades cláusula de expressão de SKIP está presente em uma cláusula GROUP BY, os resultados que serão classificados concordam a especificação do tipo e o conjunto de resultados incluirá as linhas a partir da linha seguinte logo após a expressão de SKIP. Por exemplo, a SKIP 5 ignorará as primeiras cinco linhas e retornará a sexta linha avançar.  
  
> [!NOTE]
>  Uma consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não é válido se o modificador TOP e a subpropriedades cláusula de SKIP estiverem presentes na mesma expressão de consulta. A consulta deve ser reescrita alterando a expressão TOP para a expressão de LIMIT.  
  
> [!NOTE]
>  Em [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], usar a SKIP com cláusula ORDER BY em colunas não-chave pode retornar resultados incorretos. Mais do que o número de linhas especificado podem ser ignoradas se a coluna de chave não tem dados duplicados nele. Isso é devido a como SKIP é convertido para [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]. Por exemplo, o seguinte código mais de cinco linhas podem ser ignoradas se `E.NonKeyColumn` tem valores duplicados:  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de consulta em [isso](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) exemplo usa o operador ORDER BY com Ignorar para especificar a ordem de classificação usada em objetos retornados em uma instrução SELECT.  
  
## <a name="see-also"></a>Consulte também  
 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Como: resultados da página por meio de consulta](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [Paginação](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
