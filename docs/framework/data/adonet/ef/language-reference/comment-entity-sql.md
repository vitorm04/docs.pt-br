---
title: -- (Comentário) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 4b3c801999d520a775c1a7026c945c027145b59d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764158"
---
# <a name="---comment-entity-sql"></a>-- (Comentário) (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] consultas podem conter comentários. Dois traços (`--`) início de uma linha de comentário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a>Arguments  
 `text_of_comment`  
 É a cadeia de caracteres que contém o texto de comentário.  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta SQL Entity demonstra como usar comentários. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
