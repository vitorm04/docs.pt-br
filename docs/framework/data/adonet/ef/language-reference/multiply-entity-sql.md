---
title: '* (Multiplicação) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: ecb0a55e403dddc5f7e69947035c8aa1fe7560ad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="a7254-102">\* (Multiplicação) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a7254-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="a7254-103">Em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="a7254-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7254-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7254-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a7254-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a7254-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a7254-106">Qualquer expressão válida de qualquer dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="a7254-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a7254-107">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="a7254-107">Result Types</span></span>  
 <span data-ttu-id="a7254-108">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="a7254-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a7254-109">Para obter mais informações sobre a promoção de tipo implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a7254-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7254-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7254-110">Example</span></span>  
 <span data-ttu-id="a7254-111">A seguinte consulta SQL Entity usa o operador \* aritmético para multiplicar dois números.</span><span class="sxs-lookup"><span data-stu-id="a7254-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="a7254-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a7254-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a7254-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a7254-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a7254-114">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a7254-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a7254-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a7254-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="a7254-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7254-116">See Also</span></span>  
 [<span data-ttu-id="a7254-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a7254-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
