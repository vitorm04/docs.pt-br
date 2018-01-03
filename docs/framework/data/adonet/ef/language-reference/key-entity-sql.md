---
title: CHAVE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3be9c51e48e21d76c4425401000cbfdd55f5f538
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="key-entity-sql"></a><span data-ttu-id="f25a3-102">CHAVE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f25a3-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="f25a3-103">Extraia a chave de uma referência ou uma expressão de entidade.</span><span class="sxs-lookup"><span data-stu-id="f25a3-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f25a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f25a3-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="f25a3-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="f25a3-105">Remarks</span></span>  
 <span data-ttu-id="f25a3-106">Uma chave de entidade contém os valores chave na ordem correta de entidade ou de referência de entidade especificada.</span><span class="sxs-lookup"><span data-stu-id="f25a3-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="f25a3-107">Porque os vários conjuntos de entidades podem ser baseados no mesmo tipo, a mesma chave pode aparecer em cada conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="f25a3-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="f25a3-108">Para obter uma referência única, use `REF`.</span><span class="sxs-lookup"><span data-stu-id="f25a3-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="f25a3-109">O tipo de retorno de operador- de CHAVE é um tipo da linha que inclui um campo para cada tecla de entidade, na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="f25a3-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="f25a3-110">No exemplo a seguir, o operador- de chave é passado uma referência para a entidade de BadOrder, e retorna a parte principal da referência.</span><span class="sxs-lookup"><span data-stu-id="f25a3-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="f25a3-111">Nesse caso, um tipo de registro com o exatamente um campo que corresponde à propriedade de `Id` .</span><span class="sxs-lookup"><span data-stu-id="f25a3-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="f25a3-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f25a3-112">Example</span></span>  
 <span data-ttu-id="f25a3-113">A seguinte consulta SQL Entity usa o operador- de CHAVE para extrair a parte principal de uma expressão com referência de tipo.</span><span class="sxs-lookup"><span data-stu-id="f25a3-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="f25a3-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f25a3-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f25a3-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="f25a3-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f25a3-116">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f25a3-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="f25a3-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="f25a3-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="f25a3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f25a3-118">See Also</span></span>  
 [<span data-ttu-id="f25a3-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f25a3-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f25a3-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="f25a3-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="f25a3-121">REF</span><span class="sxs-lookup"><span data-stu-id="f25a3-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="f25a3-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="f25a3-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
