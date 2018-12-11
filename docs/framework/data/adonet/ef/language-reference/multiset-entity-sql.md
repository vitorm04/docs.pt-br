---
title: MULTICONJUNTO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 64069e1bf2af61748a9e23a469dcdbc74fa9fac7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128980"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="4b6d7-102">MULTICONJUNTO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4b6d7-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="4b6d7-103">Cria uma instância de um multiset de uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="4b6d7-104">Todos os valores no construtor de MULTISET devem ser de um tipo compatível `T`.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="4b6d7-105">Não são permitidos construtores vazios de multiset.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b6d7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b6d7-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b6d7-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="4b6d7-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4b6d7-108">Uma lista de valores válido.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b6d7-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4b6d7-109">Return Value</span></span>  
 <span data-ttu-id="4b6d7-110">Uma coleção do tipo MULTISET\<T >.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b6d7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b6d7-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="4b6d7-112">fornece três tipos dos construtores: construtores, construtores de objeto e construtores de multiset (ou a coleção) de linha.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="4b6d7-113">Para obter mais informações, consulte [construindo tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4b6d7-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="4b6d7-114">O construtor de multiset cria uma instância de um multiset de uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="4b6d7-115">Todos os valores no construtor devem ser de um tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="4b6d7-116">Por exemplo, a expressão a seguir cria um multiset de inteiros.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="4b6d7-117">Literais aninhados de multiset são suportados apenas quando um multiset de automática tem um único elemento de multiset; Por exemplo, `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="4b6d7-118">Quando o multiset de automática tem vários elementos de multiset (por exemplo, `{{1, 2}, {3, 4}}`), não há suporte para literais de multiset aninhados.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b6d7-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4b6d7-119">Example</span></span>  
 <span data-ttu-id="4b6d7-120">A seguinte consulta SQL Entity usa o operador de MULTISET para criar uma instância de um multiset de uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="4b6d7-121">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4b6d7-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4b6d7-122">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="4b6d7-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4b6d7-123">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4b6d7-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4b6d7-124">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="4b6d7-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="4b6d7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b6d7-125">See Also</span></span>  
 [<span data-ttu-id="4b6d7-126">Construindo tipos</span><span class="sxs-lookup"><span data-stu-id="4b6d7-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="4b6d7-127">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4b6d7-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
