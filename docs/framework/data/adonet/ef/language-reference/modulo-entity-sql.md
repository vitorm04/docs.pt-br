---
title: (Módulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 543c35c56955fb0a9909fced23357444bc78197a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732590"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="ddcfa-102">(Módulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ddcfa-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="ddcfa-103">Retorna o resto de uma expressão dividida por outra.</span><span class="sxs-lookup"><span data-stu-id="ddcfa-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcfa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ddcfa-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="ddcfa-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ddcfa-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="ddcfa-106">A expressão numérica a divisão.</span><span class="sxs-lookup"><span data-stu-id="ddcfa-106">The numeric expression to divide.</span></span> <span data-ttu-id="ddcfa-107">`dividend` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="ddcfa-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="ddcfa-108">A expressão numérica para dividir pelo dividendo.</span><span class="sxs-lookup"><span data-stu-id="ddcfa-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="ddcfa-109">`divisor` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="ddcfa-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ddcfa-110">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="ddcfa-110">Result Types</span></span>  
 <span data-ttu-id="ddcfa-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="ddcfa-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcfa-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ddcfa-112">Example</span></span>  
 <span data-ttu-id="ddcfa-113">A seguinte consulta SQL Entity usa os % do operador aritmético para retornar o restante de uma expressão dividida por outra.</span><span class="sxs-lookup"><span data-stu-id="ddcfa-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="ddcfa-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ddcfa-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ddcfa-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ddcfa-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ddcfa-116">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ddcfa-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ddcfa-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="ddcfa-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="ddcfa-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddcfa-118">See also</span></span>
- [<span data-ttu-id="ddcfa-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ddcfa-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
