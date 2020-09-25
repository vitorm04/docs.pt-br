---
title: CONVERSÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 5591f1947963dde45d34ad2342485af476765709
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198002"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="e1825-102">CONVERSÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e1825-102">CAST (Entity SQL)</span></span>

<span data-ttu-id="e1825-103">Converte uma expressão de um tipo de dados para outro.</span><span class="sxs-lookup"><span data-stu-id="e1825-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1825-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1825-104">Syntax</span></span>  
  
```csharp
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1825-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e1825-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e1825-106">Qualquer expressão válida que seja conversível para `data_type`.</span><span class="sxs-lookup"><span data-stu-id="e1825-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="e1825-107">O tipo de dados fornecido pelo sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="e1825-107">The target system-supplied data type.</span></span> <span data-ttu-id="e1825-108">Deve ser um tipo primitivo (escalar).</span><span class="sxs-lookup"><span data-stu-id="e1825-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="e1825-109">O `data_type` usado depende do espaço da consulta.</span><span class="sxs-lookup"><span data-stu-id="e1825-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="e1825-110">Se uma consulta é executada com o <xref:System.Data.EntityClient.EntityCommand>, o tipo de dados será um tipo definido no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="e1825-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="e1825-111">Para obter mais informações, consulte [especificação CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span><span class="sxs-lookup"><span data-stu-id="e1825-111">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span> <span data-ttu-id="e1825-112">Se uma consulta é executada com o <xref:System.Data.Objects.ObjectQuery%601>, o tipo de dados será um tipo CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="e1825-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1825-113">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="e1825-113">Return Value</span></span>  

 <span data-ttu-id="e1825-114">Retorna o mesmo valor que `data_type`.</span><span class="sxs-lookup"><span data-stu-id="e1825-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1825-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1825-115">Remarks</span></span>  

 <span data-ttu-id="e1825-116">A expressão de conversão tem semântica semelhante à expressão CONVERT do Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="e1825-116">The cast expression has similar semantics to the Transact-SQL CONVERT expression.</span></span> <span data-ttu-id="e1825-117">A expressão cast é usada para converter um valor de um tipo em um valor de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="e1825-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```csharp
CAST( e as T )  
```  
  
 <span data-ttu-id="e1825-118">Se e for de algum tipo S, e S for conversível para T, a expressão anterior será uma expressão cast válida.</span><span class="sxs-lookup"><span data-stu-id="e1825-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="e1825-119">T deve ser um tipo primitivo (escalar).</span><span class="sxs-lookup"><span data-stu-id="e1825-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="e1825-120">Os valores para as facetas de precisão de escala podem opcionalmente ser fornecidos ao converter para `Edm.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e1825-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="e1825-121">Se não forem fornecidos explicitamente, os valores padrão para precisão e escala serão 18 e 0, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e1825-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="e1825-122">Especificamente, as seguintes sobrecargas têm suporte para `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="e1825-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="e1825-123">O uso de uma expressão cast é considerado uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="e1825-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="e1825-124">Conversões explícitas podem truncar dados ou perder precisão.</span><span class="sxs-lookup"><span data-stu-id="e1825-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1825-125">CAST tem suporte somente em tipos primitivos e tipos de membro de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e1825-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1825-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1825-126">Example</span></span>  

 <span data-ttu-id="e1825-127">A consulta a seguir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador cast para converter uma expressão de um tipo de dados para outro.</span><span class="sxs-lookup"><span data-stu-id="e1825-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="e1825-128">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e1825-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e1825-129">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="e1825-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e1825-130">Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e1825-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="e1825-131">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="e1825-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="e1825-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="e1825-132">See also</span></span>

- [<span data-ttu-id="e1825-133">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e1825-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
