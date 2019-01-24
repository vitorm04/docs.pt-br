---
title: '- (Divisão) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 42fc5e2a9f9f159a8a60973dbed6540b3188fba6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745227"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="043d7-102">/ (Divisão) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="043d7-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="043d7-103">Divide um número por outro.</span><span class="sxs-lookup"><span data-stu-id="043d7-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="043d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="043d7-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="043d7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="043d7-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="043d7-106">A expressão numérica a divisão.</span><span class="sxs-lookup"><span data-stu-id="043d7-106">The numeric expression to divide.</span></span> <span data-ttu-id="043d7-107">`dividend` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="043d7-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="043d7-108">A expressão numérica para dividir pelo dividendo.</span><span class="sxs-lookup"><span data-stu-id="043d7-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="043d7-109">`divisor` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="043d7-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="043d7-110">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="043d7-110">Result Types</span></span>  
 <span data-ttu-id="043d7-111">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="043d7-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="043d7-112">Para obter mais informações sobre a promoção de tipos implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="043d7-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="043d7-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="043d7-113">Example</span></span>  
 <span data-ttu-id="043d7-114">A seguinte consulta SQL Entity usa o / aritmético operador dividir um número por outro.</span><span class="sxs-lookup"><span data-stu-id="043d7-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="043d7-115">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="043d7-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="043d7-116">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="043d7-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="043d7-117">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="043d7-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="043d7-118">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="043d7-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="043d7-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="043d7-119">See also</span></span>
- [<span data-ttu-id="043d7-120">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="043d7-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
