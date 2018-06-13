---
title: (Módulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: ad7b76c1479906e9dcd875407e75475b55d5ae16
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764535"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="3870e-102">(Módulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3870e-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="3870e-103">Retorna o resto de uma expressão dividida por outra.</span><span class="sxs-lookup"><span data-stu-id="3870e-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3870e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3870e-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="3870e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3870e-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="3870e-106">A expressão numérica a divisão.</span><span class="sxs-lookup"><span data-stu-id="3870e-106">The numeric expression to divide.</span></span> <span data-ttu-id="3870e-107">`dividend` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="3870e-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="3870e-108">A expressão numérica para dividir pelo dividendo.</span><span class="sxs-lookup"><span data-stu-id="3870e-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="3870e-109">`divisor` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="3870e-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3870e-110">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="3870e-110">Result Types</span></span>  
 <span data-ttu-id="3870e-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="3870e-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="3870e-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3870e-112">Example</span></span>  
 <span data-ttu-id="3870e-113">A seguinte consulta SQL Entity usa os % do operador aritmético para retornar o restante de uma expressão dividida por outra.</span><span class="sxs-lookup"><span data-stu-id="3870e-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="3870e-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3870e-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3870e-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="3870e-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3870e-116">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3870e-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3870e-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="3870e-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="3870e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3870e-118">See Also</span></span>  
 [<span data-ttu-id="3870e-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3870e-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
