---
title: + (Concatenação de cadeia de caracteres) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 1826d1267f0ee5ad8320cf1d1ab36f87adf765a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="9a603-102">+ (Concatenação de cadeia de caracteres) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9a603-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="9a603-103">Concatena duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9a603-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a603-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a603-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a603-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9a603-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9a603-106">Qualquer expressão válida de tipos de dados de EDM.String.</span><span class="sxs-lookup"><span data-stu-id="9a603-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="9a603-107">As duas expressões devem ser do mesmo tipo de dados, ou uma expressão deve poder ser convertido implicitamente para o tipo de dados de outra expressão.</span><span class="sxs-lookup"><span data-stu-id="9a603-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9a603-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="9a603-108">Result Types</span></span>  
 <span data-ttu-id="9a603-109">O tipo de dados que resulta da promoção de tipos implícito dos dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="9a603-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="9a603-110">Para obter mais informações sobre a promoção de tipo implícito, consulte [sistema de tipo](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9a603-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a603-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a603-111">Example</span></span>  
 <span data-ttu-id="9a603-112">A seguinte consulta SQL Entity usa operador + concatena duas cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9a603-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="9a603-113">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9a603-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9a603-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="9a603-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9a603-115">Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9a603-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="9a603-116">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="9a603-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="9a603-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a603-117">See Also</span></span>  
 [<span data-ttu-id="9a603-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9a603-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="9a603-119">Tipos de modelo conceitual (CSDL)</span><span class="sxs-lookup"><span data-stu-id="9a603-119">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
