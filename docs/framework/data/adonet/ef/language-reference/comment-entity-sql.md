---
title: "-- (Comentário) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1ed1c70687b1a4aec542aff5046b237fa4710fa4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="85d21-102">-- (Comentário) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="85d21-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="85d21-103">consultas podem conter comentários.</span><span class="sxs-lookup"><span data-stu-id="85d21-103"> queries can contain comments.</span></span> <span data-ttu-id="85d21-104">Dois traços (`--`) início de uma linha de comentário.</span><span class="sxs-lookup"><span data-stu-id="85d21-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d21-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85d21-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="85d21-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="85d21-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="85d21-107">É a cadeia de caracteres que contém o texto de comentário.</span><span class="sxs-lookup"><span data-stu-id="85d21-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85d21-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85d21-108">Example</span></span>  
 <span data-ttu-id="85d21-109">A seguinte consulta SQL Entity demonstra como usar comentários.</span><span class="sxs-lookup"><span data-stu-id="85d21-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="85d21-110">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="85d21-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="85d21-111">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="85d21-111">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="85d21-112">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="85d21-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="85d21-113">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="85d21-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="85d21-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85d21-114">See Also</span></span>  
 [<span data-ttu-id="85d21-115">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="85d21-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="85d21-116">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="85d21-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
