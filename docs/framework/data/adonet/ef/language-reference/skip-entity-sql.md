---
title: IGNORAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: e8ef529ea8d2be2ef8eb3a2eb606e7ca8bf13f0a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147869"
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
  
 O [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consultar em [como: Página por meio de resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) usa o operador ORDER BY com SKIP especificar ordem de classificação usado em objetos retornados em uma instrução SELECT.  
  
## <a name="see-also"></a>Consulte também

- [ORDENAR POR](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Como: Paginar os resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Paginação](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
