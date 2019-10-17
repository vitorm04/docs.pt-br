---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 9066f9fb68ce2c50e9523881cfa0dd930cd0b52e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319724"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Determina se uma expressão de consulta é nula.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida. Não pode ser uma coleção, tem membros da coleção, ou um tipo de registro com propriedades do tipo de coleção.  
  
 NOT  
 Nega o resultado de EDM.Boolean É de NULO.  
  
## <a name="return-value"></a>Valor retornado  
 `true` se `expression` retorna nulo; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Use `IS NULL` para determinar se o elemento de um externo joins é nulo:  
  
```sql  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Use `IS NULL` para determinar se um membro tem um valor real:  
  
```sql  
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
 A consulta [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir usa o operador IS NOT NULL para determinar se uma expressão de consulta não é nula. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
