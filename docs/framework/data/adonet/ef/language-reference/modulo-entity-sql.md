---
title: (Módulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: a30306539d45c3718d2e948e9717997bbe2104fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250078"
---
# <a name="modulo-entity-sql"></a>(Módulo) (Entity SQL)
Retorna o resto de uma expressão dividida por outra.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 A expressão numérica a divisão. `dividend` é qualquer expressão válida de ambos os tipos de dados numéricos.  
  
 `divisor`  
 A expressão numérica para dividir pelo dividendo. `divisor` é qualquer expressão válida de ambos os tipos de dados numéricos.  
  
## <a name="result-types"></a>Tipos de resultado  
 Edm.Int32  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa os % do operador aritmético para retornar o restante de uma expressão dividida por outra. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados](../how-to-execute-a-query-that-returns-structuraltype-results.md)de estruturaistype.  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
