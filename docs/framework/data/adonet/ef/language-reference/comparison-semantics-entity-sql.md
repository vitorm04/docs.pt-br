---
title: Semântica de comparação (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 6b4c4177ebd6c45e00a1ac7774e40a43e0c14a74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083329"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="77e69-102">Semântica de comparação (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="77e69-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="77e69-103">Executar alguns dos seguintes operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] envolve a comparação de instâncias do tipo:</span><span class="sxs-lookup"><span data-stu-id="77e69-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="77e69-104">Comparação explícita</span><span class="sxs-lookup"><span data-stu-id="77e69-104">Explicit comparison</span></span>  
 <span data-ttu-id="77e69-105">Operações de igualdade:</span><span class="sxs-lookup"><span data-stu-id="77e69-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="77e69-106">!=</span><span class="sxs-lookup"><span data-stu-id="77e69-106">!=</span></span>  
  
 <span data-ttu-id="77e69-107">Ordenando operações:</span><span class="sxs-lookup"><span data-stu-id="77e69-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="77e69-108">Operações de nulidade:</span><span class="sxs-lookup"><span data-stu-id="77e69-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="77e69-109">É NULO</span><span class="sxs-lookup"><span data-stu-id="77e69-109">IS NULL</span></span>  
  
-   <span data-ttu-id="77e69-110">NÃO É NULO</span><span class="sxs-lookup"><span data-stu-id="77e69-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="77e69-111">Distinção explícita</span><span class="sxs-lookup"><span data-stu-id="77e69-111">Explicit distinction</span></span>  
 <span data-ttu-id="77e69-112">Distinção de igualdade:</span><span class="sxs-lookup"><span data-stu-id="77e69-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="77e69-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="77e69-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="77e69-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="77e69-114">GROUP BY</span></span>  
  
 <span data-ttu-id="77e69-115">Classificação a distinção:</span><span class="sxs-lookup"><span data-stu-id="77e69-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="77e69-116">ORDENAR POR</span><span class="sxs-lookup"><span data-stu-id="77e69-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="77e69-117">Distinção implícita</span><span class="sxs-lookup"><span data-stu-id="77e69-117">Implicit distinction</span></span>  
 <span data-ttu-id="77e69-118">Definir operações e predicados (igualdade):</span><span class="sxs-lookup"><span data-stu-id="77e69-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="77e69-119">UNION</span><span class="sxs-lookup"><span data-stu-id="77e69-119">UNION</span></span>  
  
-   <span data-ttu-id="77e69-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="77e69-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="77e69-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="77e69-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="77e69-122">SET</span><span class="sxs-lookup"><span data-stu-id="77e69-122">SET</span></span>  
  
-   <span data-ttu-id="77e69-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="77e69-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="77e69-124">Predicados de item (igual):</span><span class="sxs-lookup"><span data-stu-id="77e69-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="77e69-125">IN</span><span class="sxs-lookup"><span data-stu-id="77e69-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="77e69-126">Combinações suportados</span><span class="sxs-lookup"><span data-stu-id="77e69-126">Supported Combinations</span></span>  
 <span data-ttu-id="77e69-127">A tabela a seguir mostra todas as combinações suportados operadores de comparação para cada tipo do tipo:</span><span class="sxs-lookup"><span data-stu-id="77e69-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="77e69-128">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="77e69-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="77e69-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="77e69-129">**!=**</span></span>|<span data-ttu-id="77e69-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="77e69-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="77e69-131">**DISTINTOS**</span><span class="sxs-lookup"><span data-stu-id="77e69-131">**DISTINCT**</span></span>|<span data-ttu-id="77e69-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="77e69-132">**UNION**</span></span><br /><br /> <span data-ttu-id="77e69-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="77e69-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="77e69-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="77e69-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="77e69-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="77e69-135">**SET**</span></span><br /><br /> <span data-ttu-id="77e69-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="77e69-136">**OVERLAPS**</span></span>|<span data-ttu-id="77e69-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="77e69-137">**IN**</span></span>|<span data-ttu-id="77e69-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="77e69-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="77e69-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="77e69-139">**>   >=**</span></span>|<span data-ttu-id="77e69-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="77e69-140">**ORDER BY**</span></span>|<span data-ttu-id="77e69-141">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="77e69-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="77e69-142">**IS NOT NULL**</span><span class="sxs-lookup"><span data-stu-id="77e69-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="77e69-143">Tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="77e69-143">Entity type</span></span>|<span data-ttu-id="77e69-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="77e69-145">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="77e69-146">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="77e69-147">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="77e69-148">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-149">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="77e69-151">Tipo complexo</span><span class="sxs-lookup"><span data-stu-id="77e69-151">Complex type</span></span>|<span data-ttu-id="77e69-152">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-153">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-154">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-155">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-156">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-157">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-158">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="77e69-159">Linha</span><span class="sxs-lookup"><span data-stu-id="77e69-159">Row</span></span>|<span data-ttu-id="77e69-160">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="77e69-161">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="77e69-162">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="77e69-163">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-164">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-165">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="77e69-166">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="77e69-167">Tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="77e69-167">Primitive type</span></span>|<span data-ttu-id="77e69-168">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="77e69-168">Provider-specific</span></span>|<span data-ttu-id="77e69-169">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="77e69-169">Provider-specific</span></span>|<span data-ttu-id="77e69-170">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="77e69-170">Provider-specific</span></span>|<span data-ttu-id="77e69-171">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="77e69-171">Provider-specific</span></span>|<span data-ttu-id="77e69-172">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="77e69-172">Provider-specific</span></span>|<span data-ttu-id="77e69-173">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="77e69-173">Provider-specific</span></span>|<span data-ttu-id="77e69-174">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="77e69-174">Provider-specific</span></span>|  
|<span data-ttu-id="77e69-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="77e69-175">Multiset</span></span>|<span data-ttu-id="77e69-176">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-177">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-178">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-179">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-180">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-181">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-182">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="77e69-183">Ref</span><span class="sxs-lookup"><span data-stu-id="77e69-183">Ref</span></span>|<span data-ttu-id="77e69-184">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="77e69-185">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="77e69-186">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="77e69-187">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="77e69-188">Throw</span><span class="sxs-lookup"><span data-stu-id="77e69-188">Throw</span></span>|<span data-ttu-id="77e69-189">Throw</span><span class="sxs-lookup"><span data-stu-id="77e69-189">Throw</span></span>|<span data-ttu-id="77e69-190">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="77e69-191">Associação</span><span class="sxs-lookup"><span data-stu-id="77e69-191">Association</span></span><br /><br /> <span data-ttu-id="77e69-192">tipo</span><span class="sxs-lookup"><span data-stu-id="77e69-192">type</span></span>|<span data-ttu-id="77e69-193">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-194">Throw</span><span class="sxs-lookup"><span data-stu-id="77e69-194">Throw</span></span>|<span data-ttu-id="77e69-195">Throw</span><span class="sxs-lookup"><span data-stu-id="77e69-195">Throw</span></span>|<span data-ttu-id="77e69-196">Throw</span><span class="sxs-lookup"><span data-stu-id="77e69-196">Throw</span></span>|<span data-ttu-id="77e69-197">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-198">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="77e69-199">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="77e69-200"><sup>1</sup>as referências das instâncias de tipo de entidade em questão são comparadas implicitamente, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="77e69-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="77e69-201">Uma instância de entidade não pode ser comparado a uma referência explícita.</span><span class="sxs-lookup"><span data-stu-id="77e69-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="77e69-202">Se isso for tentada, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="77e69-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="77e69-203">Por exemplo, a seguinte consulta irá acionar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="77e69-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="77e69-204"><sup>2</sup>propriedades de tipos complexos são aplainadas para fora antes de serem enviados para o repositório, que ficam comparáveis (desde que todas as suas propriedades são comparáveis).</span><span class="sxs-lookup"><span data-stu-id="77e69-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="77e69-205">Consulte também <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="77e69-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="77e69-206"><sup>3</sup>tempo de execução de Entity Framework detecta os casos sem suporte e lança uma exceção significativa sem envolver o provedor/armazenamento.</span><span class="sxs-lookup"><span data-stu-id="77e69-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="77e69-207"><sup>4</sup>é feita uma tentativa de comparar todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="77e69-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="77e69-208">Se houver uma propriedade que é de um tipo não comparável, como texto, o ntext, ou imagem, uma exceção de servidor pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="77e69-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="77e69-209"><sup>5</sup>todos os elementos individuais de referências são comparados (Isso inclui o nome do conjunto de entidades e todas as propriedades principais do tipo de entidade).</span><span class="sxs-lookup"><span data-stu-id="77e69-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e69-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77e69-210">See also</span></span>

- [<span data-ttu-id="77e69-211">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="77e69-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
