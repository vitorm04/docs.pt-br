---
title: '|| (OU) (Entity SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b44934aa0db73f872f0ab27a4c36c5c615855de1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="-or-entity-sql"></a>|| (OU) (Entity SQL)
Combina duas expressões de `Boolean` .  
  
## <a name="syntax"></a>Sintaxe  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Qualquer expressão válida que retorna `Boolean`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` quando uma das condições for `true`; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 OR é um operador lógico de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . É usada para combinar duas condições. Quando mais de um operador lógico é usado em uma declaração, OU de operadores são avaliados em seguida E operadores. No entanto, você pode alterar a ordem de classificação usando parênteses.  
  
 Barras verticais duplas (& #124; & #124;) têm a mesma funcionalidade que o operador OR.  
  
 A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity usa o operador OR para combinar duas expressões de `Boolean` . A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
