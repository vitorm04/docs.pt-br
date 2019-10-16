---
title: + (Concatenação de cadeia de caracteres) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 9c078e193eeecd4d331c5e3c04c66dee2c4a1daa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319307"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="687a2-102">+ (Concatenação de cadeia de caracteres) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="687a2-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="687a2-103">Concatena duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="687a2-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="687a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="687a2-104">Syntax</span></span>  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="687a2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="687a2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="687a2-106">Qualquer expressão válida de tipos de dados de EDM.String.</span><span class="sxs-lookup"><span data-stu-id="687a2-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="687a2-107">As duas expressões devem ser do mesmo tipo de dados, ou uma expressão deve poder ser convertido implicitamente para o tipo de dados de outra expressão.</span><span class="sxs-lookup"><span data-stu-id="687a2-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="687a2-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="687a2-108">Result Types</span></span>  
 <span data-ttu-id="687a2-109">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="687a2-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="687a2-110">Para obter mais informações sobre a promoção de tipos implícitas, consulte [sistema de tipos](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="687a2-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="687a2-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="687a2-111">Example</span></span>  
 <span data-ttu-id="687a2-112">A seguinte consulta SQL Entity usa operador + concatena duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="687a2-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="687a2-113">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="687a2-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="687a2-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="687a2-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="687a2-115">Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="687a2-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="687a2-116">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="687a2-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="687a2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="687a2-117">See also</span></span>

- [<span data-ttu-id="687a2-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="687a2-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="687a2-119">CSDL (tipos de modelo conceitual)</span><span class="sxs-lookup"><span data-stu-id="687a2-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
