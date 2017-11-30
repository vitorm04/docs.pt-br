---
title: EM (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 553b2037ef9b1eead3a3f4745d0cb6fdfcde27ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="in-entity-sql"></a>EM (Entity SQL)
Determina se um valor corresponde a qualquer valor em uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Qualquer expressão válida que retorna o valor para corresponder.  
  
 [ NOT ]  
 Especifica que o resultado `Boolean` de IN seja negado.  
  
 `expression`  
 Qualquer expressão válida que retorna a coleção para testar uma correspondência. Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `value`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se o valor for encontrado na coleção; nulo se o valor for nulo ou a coleção for nula; caso contrário, `false`. Usar NOT IN nega os resultados de IN.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de Entity SQL usa o operador IN para determinar se um valor corresponde a qualquer valor em uma coleção. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
