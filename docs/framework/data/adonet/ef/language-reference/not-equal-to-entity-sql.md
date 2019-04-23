---
title: '!= (Não é igual a) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: f5fdbbf2892781ce44dfe73e8cd80fbe0f74cf1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310961"
---
# <a name="-not-equal-to-entity-sql"></a>!= (Não é igual a) (Entity SQL)
Compara duas expressões para determinar se a expressão da esquerda não é igual a expressão da direita. A! = (não igual a) o operador é funcionalmente equivalente ao operador <>.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida. As duas expressões devem ter os tipos de dados implicitamente conversíveis.  
  
## <a name="result-types"></a>Tipos de resultado  
 `true` se a expressão da esquerda não for igual à expressão da direita; caso contrário, `false`.  
  
## <a name="example"></a>Exemplo  
 A consulta do Entity SQL usa o operador != para comparar duas expressões para determinar se a expressão da esquerda não é igual à expressão da direita. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
