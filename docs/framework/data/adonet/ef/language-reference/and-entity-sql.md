---
title: '&amp;&amp;(E) (Entidade SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eccad616de287a39c42e986cea84dc22feec7f70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150500"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp;(E) (Entidade SQL)
Retorna `true` se as duas expressões são `true`; caso contrário, `false` ou `NULL`.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
boolean_expression AND boolean_expression
```

ou  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>Argumentos  
 `boolean_expression`  
 Qualquer expressão válida que retorna um valor booleano.  
  
## <a name="remarks"></a>Comentários  
 As ampersands duplas (&&) têm a mesma funcionalidade que o operador AND.  
  
 A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|FALSE|NULO|  
|`FALSE`|FALSE|FALSE|FALSE|  
|`NULL`|NULO|FALSE|NULO|  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity demonstra como usar o operador AND. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [Como: Executar uma consulta que retorna resultados do tipo estrutural](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Confira também

- [Referência de Entity SQL](entity-sql-reference.md)
