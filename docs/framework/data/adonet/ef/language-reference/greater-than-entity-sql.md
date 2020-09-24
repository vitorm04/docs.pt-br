---
title: '>  (Maior que) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 52a9f9f645aa51402ceb8cb0a40d2040d1c0802c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147938"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="754ce-102">> (maior que) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="754ce-102">> (Greater Than) (Entity SQL)</span></span>

<span data-ttu-id="754ce-103">Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que a expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="754ce-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="754ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="754ce-104">Syntax</span></span>  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="754ce-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="754ce-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="754ce-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="754ce-106">Any valid expression.</span></span> <span data-ttu-id="754ce-107">Ambas as expressões devem ter tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="754ce-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="754ce-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="754ce-108">Result Types</span></span>  

 <span data-ttu-id="754ce-109">`true` se a expressão esquerda tem um valor maior que a expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="754ce-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="754ce-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="754ce-110">Example</span></span>  

 <span data-ttu-id="754ce-111">A consulta Entity SQL a seguir usa > operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor maior que a expressão direita.</span><span class="sxs-lookup"><span data-stu-id="754ce-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="754ce-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="754ce-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="754ce-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="754ce-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="754ce-114">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="754ce-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="754ce-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="754ce-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="754ce-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="754ce-116">See also</span></span>

- [<span data-ttu-id="754ce-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="754ce-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
