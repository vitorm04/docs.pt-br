---
title: '> (Maior que) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 992e1b7cf4733266f606f8357c71d72722b04896
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127121"
---
# <a name="-greater-than-entity-sql"></a>> (Maior que) (Entity SQL)
Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que a expressão da direita.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida. As duas expressões devem ter os tipos de dados implicitamente conversíveis.  
  
## <a name="result-types"></a>Tipos de resultado  
 `true` Se a expressão esquerda tem um valor maior que a expressão direita; Caso contrário, `false`.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa > operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor maior que a expressão direita. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
