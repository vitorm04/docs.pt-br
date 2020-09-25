---
title: '- Subtrair (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 17841f336ed186dcbc50b84254048546b15297e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181031"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="7d806-102">- (Subtração) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7d806-102">- (Subtract) (Entity SQL)</span></span>

<span data-ttu-id="7d806-103">Subtrai dois números.</span><span class="sxs-lookup"><span data-stu-id="7d806-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d806-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d806-104">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d806-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="7d806-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="7d806-106">Qualquer expressão válida de qualquer dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="7d806-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7d806-107">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="7d806-107">Result Types</span></span>  

 <span data-ttu-id="7d806-108">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="7d806-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="7d806-109">Para obter mais informações sobre a promoção de tipos implícitas, consulte [sistema de tipos](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7d806-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d806-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d806-110">Example</span></span>  

 <span data-ttu-id="7d806-111">A seguinte consulta SQL Entity usa o operador - aritmético para subtrair dois números.</span><span class="sxs-lookup"><span data-stu-id="7d806-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="7d806-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7d806-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7d806-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="7d806-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7d806-114">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7d806-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7d806-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="7d806-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="7d806-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="7d806-116">See also</span></span>

- [<span data-ttu-id="7d806-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7d806-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
