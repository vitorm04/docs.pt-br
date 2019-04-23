---
title: QUALQUERELEMENTO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: ff79417008b7807fbf206d4bcb65b4e5ea1cc576
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296128"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="1bc84-102">QUALQUERELEMENTO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1bc84-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="1bc84-103">Extrai um elemento de uma coleção multivalorada.</span><span class="sxs-lookup"><span data-stu-id="1bc84-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bc84-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="1bc84-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1bc84-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1bc84-106">Qualquer expressão de consulta válida de que retornar uma coleção para extrair um elemento.</span><span class="sxs-lookup"><span data-stu-id="1bc84-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bc84-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1bc84-107">Return Value</span></span>  
 <span data-ttu-id="1bc84-108">Um único elemento na coleção ou um elemento arbitrário se a coleção tem mais de uma; se a coleção estiver vazia, retorna `null`.</span><span class="sxs-lookup"><span data-stu-id="1bc84-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="1bc84-109">Se `collection` é uma coleção do tipo `Collection<T>`, em seguida, `ANYELEMENT(collection)` é uma expressão válida que produzir uma instância do tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="1bc84-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bc84-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bc84-110">Remarks</span></span>  
 <span data-ttu-id="1bc84-111">ANYELEMENT extrai um elemento arbitrário de uma coleção multivalorado.</span><span class="sxs-lookup"><span data-stu-id="1bc84-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="1bc84-112">Por exemplo, o exemplo a seguir tenta extrair um elemento singleton do conjunto `Customers`.</span><span class="sxs-lookup"><span data-stu-id="1bc84-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="1bc84-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bc84-113">Example</span></span>  
 <span data-ttu-id="1bc84-114">A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de ANYELEMENT para extrair um elemento de uma coleção multivalorado.</span><span class="sxs-lookup"><span data-stu-id="1bc84-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="1bc84-115">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1bc84-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1bc84-116">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="1bc84-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1bc84-117">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1bc84-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1bc84-118">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="1bc84-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="1bc84-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bc84-119">See also</span></span>

- [<span data-ttu-id="1bc84-120">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1bc84-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="1bc84-121">Tipos estruturados anulável</span><span class="sxs-lookup"><span data-stu-id="1bc84-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
