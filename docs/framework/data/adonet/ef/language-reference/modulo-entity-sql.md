---
title: (Módulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 4bbdbe53403cfec2568cfac320fc7ab1ad2725b0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319599"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="32ee9-102">(Módulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="32ee9-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="32ee9-103">Retorna o resto de uma expressão dividida por outra.</span><span class="sxs-lookup"><span data-stu-id="32ee9-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ee9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32ee9-104">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="32ee9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="32ee9-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="32ee9-106">A expressão numérica a divisão.</span><span class="sxs-lookup"><span data-stu-id="32ee9-106">The numeric expression to divide.</span></span> <span data-ttu-id="32ee9-107">`dividend` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="32ee9-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="32ee9-108">A expressão numérica para dividir pelo dividendo.</span><span class="sxs-lookup"><span data-stu-id="32ee9-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="32ee9-109">`divisor` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="32ee9-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="32ee9-110">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="32ee9-110">Result Types</span></span>  
 <span data-ttu-id="32ee9-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="32ee9-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="32ee9-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="32ee9-112">Example</span></span>  
 <span data-ttu-id="32ee9-113">A seguinte consulta SQL Entity usa os % do operador aritmético para retornar o restante de uma expressão dividida por outra.</span><span class="sxs-lookup"><span data-stu-id="32ee9-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="32ee9-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="32ee9-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="32ee9-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="32ee9-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="32ee9-116">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="32ee9-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="32ee9-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="32ee9-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="32ee9-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32ee9-118">See also</span></span>

- [<span data-ttu-id="32ee9-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="32ee9-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
