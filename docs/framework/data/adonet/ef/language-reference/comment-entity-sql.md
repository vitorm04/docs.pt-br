---
title: -- (Comentário) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 9ad6e38726d0802c3bc2090a4e6f11f008828ee5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197892"
---
# <a name="---comment-entity-sql"></a>-- (Comentário) (Entity SQL)

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] as consultas podem conter comentários. Dois traços (`--`) início de uma linha de comentário.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Argumentos  

 `text_of_comment`  
 É a cadeia de caracteres que contém o texto do comentário.  
  
## <a name="example"></a>Exemplo  

 A seguinte consulta SQL Entity demonstra como usar comentários. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Veja também

- [Visão geral da Entity SQL](entity-sql-overview.md)
- [Referência de Entity SQL](entity-sql-reference.md)
