---
title: QUALQUERELEMENTO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: c0f7686f7ff3f6458637b51e29ecafe0c0ccfbc4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040317"
---
# <a name="anyelement-entity-sql"></a>QUALQUERELEMENTO (Entity SQL)
Extrai um elemento de uma coleção multivalorada.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão de consulta válida de que retornar uma coleção para extrair um elemento.  
  
## <a name="return-value"></a>Valor retornado  
 Um único elemento na coleção ou um elemento arbitrário se a coleção tem mais de uma; se a coleção estiver vazia, retorna `null`. Se `collection` for uma coleção do tipo `Collection<T>`, `ANYELEMENT(collection)` será uma expressão válida que produz uma instância do tipo `T`.  
  
## <a name="remarks"></a>Comentários  
 ANYELEMENT extrai um elemento arbitrário de uma coleção multivalorado. Por exemplo, o exemplo a seguir tenta extrair um elemento singleton do conjunto `Customers`.  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de ANYELEMENT para extrair um elemento de uma coleção multivalorado. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
- [Tipos estruturados anulável](nullable-structured-types-entity-sql.md)
