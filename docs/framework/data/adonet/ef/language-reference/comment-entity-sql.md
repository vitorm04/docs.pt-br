---
title: -- (Comentário) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: c10b17931c6024e2a9e947083747435d8aa54fa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605980"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="8b812-102">-- (Comentário) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8b812-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="8b812-103">consultas podem conter comentários.</span><span class="sxs-lookup"><span data-stu-id="8b812-103">queries can contain comments.</span></span> <span data-ttu-id="8b812-104">Dois traços (`--`) início de uma linha de comentário.</span><span class="sxs-lookup"><span data-stu-id="8b812-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b812-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b812-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b812-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b812-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="8b812-107">É a cadeia de caracteres que contém o texto de comentário.</span><span class="sxs-lookup"><span data-stu-id="8b812-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b812-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b812-108">Example</span></span>  
 <span data-ttu-id="8b812-109">A seguinte consulta SQL Entity demonstra como usar comentários.</span><span class="sxs-lookup"><span data-stu-id="8b812-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="8b812-110">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8b812-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8b812-111">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="8b812-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8b812-112">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8b812-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8b812-113">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="8b812-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="8b812-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b812-114">See also</span></span>

- [<span data-ttu-id="8b812-115">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8b812-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="8b812-116">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8b812-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
