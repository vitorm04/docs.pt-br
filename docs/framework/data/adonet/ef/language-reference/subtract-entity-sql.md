---
title: '- Subtrair (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 17841f336ed186dcbc50b84254048546b15297e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181031"
---
# <a name="--subtract-entity-sql"></a>- (Subtração) (Entity SQL)

Subtrai dois números.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a>Argumentos  

 `expression`  
 Qualquer expressão válida de qualquer dos tipos de dados numéricos.  
  
## <a name="result-types"></a>Tipos de resultado  

 O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos. Para obter mais informações sobre a promoção de tipos implícitas, consulte [sistema de tipos](type-system-entity-sql.md).  
  
## <a name="example"></a>Exemplo  

 A seguinte consulta SQL Entity usa o operador - aritmético para subtrair dois números. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a>Veja também

- [Referência de Entity SQL](entity-sql-reference.md)
