---
title: (Módulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 25bd34db3a627fa708e1ab9a3f0e237426487bcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175701"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="38cec-102">(Módulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="38cec-102">(Modulo) (Entity SQL)</span></span>

<span data-ttu-id="38cec-103">Retorna o resto de uma expressão dividida por outra.</span><span class="sxs-lookup"><span data-stu-id="38cec-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38cec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38cec-104">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="38cec-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="38cec-105">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="38cec-106">A expressão numérica a divisão.</span><span class="sxs-lookup"><span data-stu-id="38cec-106">The numeric expression to divide.</span></span> <span data-ttu-id="38cec-107">`dividend` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="38cec-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="38cec-108">A expressão numérica para dividir pelo dividendo.</span><span class="sxs-lookup"><span data-stu-id="38cec-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="38cec-109">`divisor` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="38cec-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="38cec-110">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="38cec-110">Result Types</span></span>  

 <span data-ttu-id="38cec-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="38cec-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="38cec-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38cec-112">Example</span></span>  

 <span data-ttu-id="38cec-113">A seguinte consulta SQL Entity usa os % do operador aritmético para retornar o restante de uma expressão dividida por outra.</span><span class="sxs-lookup"><span data-stu-id="38cec-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="38cec-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="38cec-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="38cec-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="38cec-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="38cec-116">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="38cec-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="38cec-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="38cec-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="38cec-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="38cec-118">See also</span></span>

- [<span data-ttu-id="38cec-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="38cec-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
