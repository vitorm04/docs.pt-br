---
title: '- (Divisão) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: ca63835a3be23137a1a40d6d6597083ae2128ac7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094886"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="2b2a5-102">/ (Divisão) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2b2a5-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="2b2a5-103">Divide um número por outro.</span><span class="sxs-lookup"><span data-stu-id="2b2a5-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b2a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b2a5-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b2a5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2b2a5-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="2b2a5-106">A expressão numérica a divisão.</span><span class="sxs-lookup"><span data-stu-id="2b2a5-106">The numeric expression to divide.</span></span> `dividend` <span data-ttu-id="2b2a5-107">é qualquer expressão válida de qualquer um dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="2b2a5-107">is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="2b2a5-108">A expressão numérica para dividir pelo dividendo.</span><span class="sxs-lookup"><span data-stu-id="2b2a5-108">The numeric expression to divide the dividend by.</span></span> `divisor` <span data-ttu-id="2b2a5-109">é qualquer expressão válida de qualquer um dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="2b2a5-109">is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2b2a5-110">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="2b2a5-110">Result Types</span></span>  
 <span data-ttu-id="2b2a5-111">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="2b2a5-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="2b2a5-112">Para obter mais informações sobre a promoção de tipos implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2b2a5-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b2a5-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b2a5-113">Example</span></span>  
 <span data-ttu-id="2b2a5-114">A seguinte consulta SQL Entity usa o / aritmético operador dividir um número por outro.</span><span class="sxs-lookup"><span data-stu-id="2b2a5-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="2b2a5-115">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2b2a5-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b2a5-116">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2b2a5-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="2b2a5-117">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2b2a5-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="2b2a5-118">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="2b2a5-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="2b2a5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b2a5-119">See also</span></span>

- [<span data-ttu-id="2b2a5-120">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2b2a5-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
