---
title: '- Dividir (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: d7d25d8c5b91850b21e36ba8f6f668af7a7d0045
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148155"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="a005b-102">/ (Divisão) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a005b-102">/ (Divide) (Entity SQL)</span></span>

<span data-ttu-id="a005b-103">Divide um número por outro.</span><span class="sxs-lookup"><span data-stu-id="a005b-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a005b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a005b-104">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="a005b-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="a005b-105">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="a005b-106">A expressão numérica a divisão.</span><span class="sxs-lookup"><span data-stu-id="a005b-106">The numeric expression to divide.</span></span> <span data-ttu-id="a005b-107">`dividend` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="a005b-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="a005b-108">A expressão numérica para dividir pelo dividendo.</span><span class="sxs-lookup"><span data-stu-id="a005b-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="a005b-109">`divisor` é qualquer expressão válida de ambos os tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="a005b-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a005b-110">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="a005b-110">Result Types</span></span>  

 <span data-ttu-id="a005b-111">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="a005b-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a005b-112">Para obter mais informações sobre a promoção de tipos implícitas, consulte [sistema de tipos](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a005b-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a005b-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a005b-113">Example</span></span>  

 <span data-ttu-id="a005b-114">A consulta Entity SQL a seguir usa o operador/aritmética para dividir um número por outro.</span><span class="sxs-lookup"><span data-stu-id="a005b-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="a005b-115">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a005b-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a005b-116">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a005b-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a005b-117">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a005b-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a005b-118">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a005b-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="a005b-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="a005b-119">See also</span></span>

- [<span data-ttu-id="a005b-120">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a005b-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
