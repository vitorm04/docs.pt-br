---
title: MULTICONJUNTO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 222be86db434b5d41c7b0536d271a3750b6afbe8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319592"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="fa6df-102">MULTICONJUNTO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fa6df-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="fa6df-103">Cria uma instância de um multiset de uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="fa6df-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="fa6df-104">Todos os valores no Construtor multiconjunto devem ser de um tipo compatível `T`.</span><span class="sxs-lookup"><span data-stu-id="fa6df-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="fa6df-105">Não são permitidos construtores vazios de multiset.</span><span class="sxs-lookup"><span data-stu-id="fa6df-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa6df-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa6df-106">Syntax</span></span>  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa6df-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="fa6df-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fa6df-108">Uma lista de valores válido.</span><span class="sxs-lookup"><span data-stu-id="fa6df-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa6df-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fa6df-109">Return Value</span></span>  
 <span data-ttu-id="fa6df-110">Uma coleção do tipo multiconjunto\<T >.</span><span class="sxs-lookup"><span data-stu-id="fa6df-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa6df-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa6df-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fa6df-112">fornece três tipos de construtores: construtores de linha, construtores de objeto e construtores de vários conjuntos (ou de coleção).</span><span class="sxs-lookup"><span data-stu-id="fa6df-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="fa6df-113">Para obter mais informações, consulte [construindo tipos](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fa6df-113">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="fa6df-114">O construtor de multiset cria uma instância de um multiset de uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="fa6df-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="fa6df-115">Todos os valores no construtor devem ser de um tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="fa6df-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="fa6df-116">Por exemplo, a expressão a seguir cria um multiset de inteiros.</span><span class="sxs-lookup"><span data-stu-id="fa6df-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> <span data-ttu-id="fa6df-117">Literais multiconjuntos aninhados só têm suporte quando um encapsulamento multiconjunto tem um único elemento multiconjunto; por exemplo, `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="fa6df-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="fa6df-118">Quando o encapsulamento multiconjunto tem vários elementos multiconjunto (por exemplo, `{{1, 2}, {3, 4}}`), literais multiconjunto aninhados não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="fa6df-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa6df-119">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fa6df-119">Example</span></span>  
 <span data-ttu-id="fa6df-120">A seguinte consulta SQL Entity usa o operador de MULTISET para criar uma instância de um multiset de uma lista de valores.</span><span class="sxs-lookup"><span data-stu-id="fa6df-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="fa6df-121">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fa6df-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fa6df-122">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="fa6df-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fa6df-123">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fa6df-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="fa6df-124">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="fa6df-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="fa6df-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa6df-125">See also</span></span>

- [<span data-ttu-id="fa6df-126">Construindo tipos</span><span class="sxs-lookup"><span data-stu-id="fa6df-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="fa6df-127">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fa6df-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
