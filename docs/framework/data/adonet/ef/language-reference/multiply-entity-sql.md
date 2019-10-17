---
title: '* Multiplicar (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 7006f5143e8cc18156f748ae7664f3787c9ff5c9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319607"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="f6297-102">\* (Multiplicação) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f6297-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="f6297-103">Em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="f6297-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6297-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6297-104">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6297-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f6297-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f6297-106">Qualquer expressão válida de qualquer dos tipos de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="f6297-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f6297-107">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="f6297-107">Result Types</span></span>  
 <span data-ttu-id="f6297-108">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="f6297-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="f6297-109">Para obter mais informações sobre a promoção de tipos implícitas, consulte [sistema de tipos](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f6297-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6297-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6297-110">Example</span></span>  
 <span data-ttu-id="f6297-111">A seguinte consulta SQL Entity usa o operador \* aritmético para multiplicar dois números.</span><span class="sxs-lookup"><span data-stu-id="f6297-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="f6297-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f6297-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f6297-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="f6297-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f6297-114">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f6297-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f6297-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="f6297-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="f6297-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6297-116">See also</span></span>

- [<span data-ttu-id="f6297-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f6297-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
