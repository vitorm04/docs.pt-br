---
title: + (adicionar)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: fb557ad6e10901d38a87c8acad56bc3fe51d47a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199876"
---
# <a name="-add"></a><span data-ttu-id="e61aa-102">+ (Adicionar)</span><span class="sxs-lookup"><span data-stu-id="e61aa-102">+ (Add)</span></span>
<span data-ttu-id="e61aa-103">Adiciona dois números.</span><span class="sxs-lookup"><span data-stu-id="e61aa-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e61aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e61aa-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e61aa-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e61aa-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e61aa-106">Qualquer expressão válida de qualquer dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="e61aa-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e61aa-107">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="e61aa-107">Result Types</span></span>  
 <span data-ttu-id="e61aa-108">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="e61aa-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="e61aa-109">Para obter mais informações sobre a promoção de tipos implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e61aa-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e61aa-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e61aa-110">Remarks</span></span>  
 <span data-ttu-id="e61aa-111">Para tipos de EDM.String, a adição é concatenação.</span><span class="sxs-lookup"><span data-stu-id="e61aa-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e61aa-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e61aa-112">Example</span></span>  
 <span data-ttu-id="e61aa-113">A seguinte consulta SQL Entity usa operador + aritmético para adicionar dois números.</span><span class="sxs-lookup"><span data-stu-id="e61aa-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="e61aa-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e61aa-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e61aa-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="e61aa-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e61aa-116">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e61aa-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e61aa-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="e61aa-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="e61aa-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e61aa-118">See also</span></span>

- [<span data-ttu-id="e61aa-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e61aa-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e61aa-120">Tipos de modelo conceituais (CSDL)</span><span class="sxs-lookup"><span data-stu-id="e61aa-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
