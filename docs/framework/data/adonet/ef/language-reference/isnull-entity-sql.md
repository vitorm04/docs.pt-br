---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 894d3ab91623aa4246bf7735fb1b7d04e066825a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072630"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Determina se uma expressão de consulta é nula.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida. Não pode ser uma coleção, tem membros da coleção, ou um tipo de registro com propriedades do tipo de coleção.  
  
 NOT  
 Nega o resultado de EDM.Boolean É de NULO.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Se `expression` retorna nulo; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Use `IS NULL` para determinar se o elemento de um externo joins é nulo:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Use `IS NULL` para determinar se um membro tem um valor real:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 A tabela a seguir mostra o comportamento de `IS NULL` sobre alguns padrões. Todas as exceções são geradas do lado do cliente antes que o provedor obtenha chamado:  
  
|Padrão|Comportamento|  
|-------------|--------------|  
|o zero É NULO|Retorna `true`.|  
|O DELEITE zero (COMO EntityType) É NULO|Retorna `true`.|  
|O DELEITE zero (COMO ComplexType) É NULO|Gerencie um erro.|  
|O DELEITE zero (COMO RowType) É NULO|Gerencie um erro.|  
|EntityType É NULO|Retorna `true` ou `false`.|  
|ComplexType É NULO|Gerencie um erro.|  
|RowType É NULO|Gerencie um erro.|  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consulta usa o operador IS NOT NULL para determinar se uma expressão de consulta não é nula. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
