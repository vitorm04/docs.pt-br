---
title: QUALQUERELEMENTO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 11d1dd4b09ff07519f3435d313de72c5b9a3edf4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="anyelement-entity-sql"></a>QUALQUERELEMENTO (Entity SQL)
Extrai um elemento de uma coleção multivalorada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida de que retornar uma coleção para extrair um elemento.  
  
## <a name="return-value"></a>Valor de retorno  
 Um único elemento na coleção ou um elemento arbitrário se a coleção tem mais de uma; se a coleção estiver vazia, retorna `null`. Se `collection` é uma coleção de tipo `Collection<T>`, em seguida, `ANYELEMENT(collection)` é uma expressão que produz uma instância do tipo `T`.  
  
## <a name="remarks"></a>Comentários  
 ANYELEMENT extrai um elemento arbitrário de uma coleção multivalorado. Por exemplo, o exemplo a seguir tenta extrair um elemento singleton do conjunto `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de ANYELEMENT para extrair um elemento de uma coleção multivalorado. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Tipos estruturados anulável](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
