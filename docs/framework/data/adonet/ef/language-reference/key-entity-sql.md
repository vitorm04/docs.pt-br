---
title: CHAVE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 14c0b5d273b26c71c9c63e8bbbcef863ac95a5f3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319707"
---
# <a name="key-entity-sql"></a><span data-ttu-id="ffaf4-102">CHAVE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ffaf4-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="ffaf4-103">Extraia a chave de uma referência ou uma expressão de entidade.</span><span class="sxs-lookup"><span data-stu-id="ffaf4-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffaf4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffaf4-104">Syntax</span></span>  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="ffaf4-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffaf4-105">Remarks</span></span>  
 <span data-ttu-id="ffaf4-106">Uma chave de entidade contém os valores chave na ordem correta de entidade ou de referência de entidade especificada.</span><span class="sxs-lookup"><span data-stu-id="ffaf4-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="ffaf4-107">Porque os vários conjuntos de entidades podem ser baseados no mesmo tipo, a mesma chave pode aparecer em cada conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="ffaf4-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="ffaf4-108">Para obter uma referência única, use `REF`.</span><span class="sxs-lookup"><span data-stu-id="ffaf4-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="ffaf4-109">O tipo de retorno de operador- de CHAVE é um tipo da linha que inclui um campo para cada tecla de entidade, na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="ffaf4-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="ffaf4-110">No exemplo a seguir, o operador- de chave é passado uma referência para a entidade de BadOrder, e retorna a parte principal da referência.</span><span class="sxs-lookup"><span data-stu-id="ffaf4-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="ffaf4-111">Nesse caso, um tipo de registro com o exatamente um campo que corresponde à propriedade de `Id` .</span><span class="sxs-lookup"><span data-stu-id="ffaf4-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="ffaf4-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ffaf4-112">Example</span></span>  
 <span data-ttu-id="ffaf4-113">A seguinte consulta SQL Entity usa o operador- de CHAVE para extrair a parte principal de uma expressão com referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="ffaf4-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="ffaf4-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ffaf4-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ffaf4-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ffaf4-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ffaf4-116">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ffaf4-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ffaf4-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="ffaf4-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a><span data-ttu-id="ffaf4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffaf4-118">See also</span></span>

- [<span data-ttu-id="ffaf4-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ffaf4-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ffaf4-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="ffaf4-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="ffaf4-121">REF</span><span class="sxs-lookup"><span data-stu-id="ffaf4-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="ffaf4-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="ffaf4-122">DEREF</span></span>](deref-entity-sql.md)
