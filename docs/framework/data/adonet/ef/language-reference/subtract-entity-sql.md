---
title: '- (Subtração) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 2e4c08788ea57000e189c8371f0494641931184b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797651"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="a5cc6-102">- (Subtração) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a5cc6-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="a5cc6-103">Subtrai dois números.</span><span class="sxs-lookup"><span data-stu-id="a5cc6-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5cc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5cc6-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5cc6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a5cc6-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a5cc6-106">Qualquer expressão válida de qualquer dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="a5cc6-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a5cc6-107">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="a5cc6-107">Result Types</span></span>  
 <span data-ttu-id="a5cc6-108">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="a5cc6-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a5cc6-109">Para obter mais informações sobre a promoção de tipos implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a5cc6-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5cc6-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5cc6-110">Example</span></span>  
 <span data-ttu-id="a5cc6-111">A seguinte consulta SQL Entity usa o operador - aritmético para subtrair dois números.</span><span class="sxs-lookup"><span data-stu-id="a5cc6-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="a5cc6-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a5cc6-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a5cc6-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a5cc6-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a5cc6-114">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a5cc6-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a5cc6-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a5cc6-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="a5cc6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5cc6-116">See also</span></span>

- [<span data-ttu-id="a5cc6-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a5cc6-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
