---
title: '&gt; (Maior que) (Entity SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9444aec821cd9ab6a6008989de83e929ba5f6baf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="gt-greater-than-entity-sql"></a>&gt; (Maior que) (Entity SQL)
Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que a expressão da direita.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida. As duas expressões devem ter os tipos de dados implicitamente conversíveis.  
  
## <a name="result-types"></a>Tipos de resultado  
 `true` se a expressão esquerda tem um valor maior que a expressão direita; caso contrário, `false`.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa > o operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor maior que a expressão direita. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
