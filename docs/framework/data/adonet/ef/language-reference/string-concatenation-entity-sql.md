---
title: + (Concatenação de cadeia de caracteres) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 92591448a3707ba11ad2462161050e48e0398728
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173621"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="3d6ad-102">+ (Concatenação de cadeia de caracteres) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3d6ad-102">+ (String Concatenation) (Entity SQL)</span></span>

<span data-ttu-id="3d6ad-103">Concatena duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3d6ad-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d6ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d6ad-104">Syntax</span></span>  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d6ad-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3d6ad-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="3d6ad-106">Qualquer expressão válida de tipos de dados de EDM.String.</span><span class="sxs-lookup"><span data-stu-id="3d6ad-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="3d6ad-107">As duas expressões devem ser do mesmo tipo de dados ou uma expressão deve poder ser convertida implicitamente no tipo de dados da outra expressão.</span><span class="sxs-lookup"><span data-stu-id="3d6ad-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3d6ad-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="3d6ad-108">Result Types</span></span>  

 <span data-ttu-id="3d6ad-109">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="3d6ad-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="3d6ad-110">Para obter mais informações sobre a promoção de tipos implícitas, consulte [sistema de tipos](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3d6ad-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d6ad-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d6ad-111">Example</span></span>  

 <span data-ttu-id="3d6ad-112">A seguinte consulta SQL Entity usa operador + concatena duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3d6ad-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="3d6ad-113">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3d6ad-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3d6ad-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="3d6ad-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3d6ad-115">Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3d6ad-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="3d6ad-116">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="3d6ad-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="3d6ad-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="3d6ad-117">See also</span></span>

- [<span data-ttu-id="3d6ad-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3d6ad-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3d6ad-119">CSDL (tipos de modelo conceitual)</span><span class="sxs-lookup"><span data-stu-id="3d6ad-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
