---
title: Semântica de comparação (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: da7b8f662d10376abd649e674701b43b7b740a6f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251188"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="1c286-102">Semântica de comparação (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1c286-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="1c286-103">Executar alguns dos seguintes operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] envolve a comparação de instâncias do tipo:</span><span class="sxs-lookup"><span data-stu-id="1c286-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="1c286-104">Comparação explícita</span><span class="sxs-lookup"><span data-stu-id="1c286-104">Explicit comparison</span></span>  
 <span data-ttu-id="1c286-105">Operações de igualdade:</span><span class="sxs-lookup"><span data-stu-id="1c286-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="1c286-106">!=</span><span class="sxs-lookup"><span data-stu-id="1c286-106">!=</span></span>  
  
 <span data-ttu-id="1c286-107">Ordenando operações:</span><span class="sxs-lookup"><span data-stu-id="1c286-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="1c286-108">Operações de nulidade:</span><span class="sxs-lookup"><span data-stu-id="1c286-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="1c286-109">É NULO</span><span class="sxs-lookup"><span data-stu-id="1c286-109">IS NULL</span></span>  
  
- <span data-ttu-id="1c286-110">NÃO É NULO</span><span class="sxs-lookup"><span data-stu-id="1c286-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="1c286-111">Distinção explícita</span><span class="sxs-lookup"><span data-stu-id="1c286-111">Explicit distinction</span></span>  
 <span data-ttu-id="1c286-112">Distinção de igualdade:</span><span class="sxs-lookup"><span data-stu-id="1c286-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="1c286-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="1c286-113">DISTINCT</span></span>  
  
- <span data-ttu-id="1c286-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="1c286-114">GROUP BY</span></span>  
  
 <span data-ttu-id="1c286-115">Classificação a distinção:</span><span class="sxs-lookup"><span data-stu-id="1c286-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="1c286-116">ORDENAR POR</span><span class="sxs-lookup"><span data-stu-id="1c286-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="1c286-117">Distinção implícita</span><span class="sxs-lookup"><span data-stu-id="1c286-117">Implicit distinction</span></span>  
 <span data-ttu-id="1c286-118">Definir operações e predicados (igualdade):</span><span class="sxs-lookup"><span data-stu-id="1c286-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="1c286-119">UNION</span><span class="sxs-lookup"><span data-stu-id="1c286-119">UNION</span></span>  
  
- <span data-ttu-id="1c286-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="1c286-120">INTERSECT</span></span>  
  
- <span data-ttu-id="1c286-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="1c286-121">EXCEPT</span></span>  
  
- <span data-ttu-id="1c286-122">SET</span><span class="sxs-lookup"><span data-stu-id="1c286-122">SET</span></span>  
  
- <span data-ttu-id="1c286-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="1c286-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="1c286-124">Predicados de item (igual):</span><span class="sxs-lookup"><span data-stu-id="1c286-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="1c286-125">IN</span><span class="sxs-lookup"><span data-stu-id="1c286-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="1c286-126">Combinações suportados</span><span class="sxs-lookup"><span data-stu-id="1c286-126">Supported Combinations</span></span>  
 <span data-ttu-id="1c286-127">A tabela a seguir mostra todas as combinações suportados operadores de comparação para cada tipo do tipo:</span><span class="sxs-lookup"><span data-stu-id="1c286-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="1c286-128">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="1c286-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="1c286-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="1c286-129">**!=**</span></span>|<span data-ttu-id="1c286-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="1c286-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="1c286-131">**DISTINÇÃO**</span><span class="sxs-lookup"><span data-stu-id="1c286-131">**DISTINCT**</span></span>|<span data-ttu-id="1c286-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="1c286-132">**UNION**</span></span><br /><br /> <span data-ttu-id="1c286-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="1c286-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="1c286-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="1c286-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="1c286-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="1c286-135">**SET**</span></span><br /><br /> <span data-ttu-id="1c286-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="1c286-136">**OVERLAPS**</span></span>|<span data-ttu-id="1c286-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="1c286-137">**IN**</span></span>|<span data-ttu-id="1c286-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="1c286-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="1c286-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="1c286-139">**>   >=**</span></span>|<span data-ttu-id="1c286-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="1c286-140">**ORDER BY**</span></span>|<span data-ttu-id="1c286-141">**É NULO**</span><span class="sxs-lookup"><span data-stu-id="1c286-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="1c286-142">**NÃO É NULO**</span><span class="sxs-lookup"><span data-stu-id="1c286-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="1c286-143">Tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="1c286-143">Entity type</span></span>|<span data-ttu-id="1c286-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="1c286-145">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="1c286-146">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="1c286-147">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="1c286-148">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-149">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="1c286-151">Tipo complexo</span><span class="sxs-lookup"><span data-stu-id="1c286-151">Complex type</span></span>|<span data-ttu-id="1c286-152">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-153">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-154">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-155">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-156">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-157">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-158">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="1c286-159">Linha</span><span class="sxs-lookup"><span data-stu-id="1c286-159">Row</span></span>|<span data-ttu-id="1c286-160">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="1c286-161">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="1c286-162">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="1c286-163">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-164">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-165">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="1c286-166">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="1c286-167">Tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="1c286-167">Primitive type</span></span>|<span data-ttu-id="1c286-168">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="1c286-168">Provider-specific</span></span>|<span data-ttu-id="1c286-169">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="1c286-169">Provider-specific</span></span>|<span data-ttu-id="1c286-170">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="1c286-170">Provider-specific</span></span>|<span data-ttu-id="1c286-171">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="1c286-171">Provider-specific</span></span>|<span data-ttu-id="1c286-172">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="1c286-172">Provider-specific</span></span>|<span data-ttu-id="1c286-173">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="1c286-173">Provider-specific</span></span>|<span data-ttu-id="1c286-174">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="1c286-174">Provider-specific</span></span>|  
|<span data-ttu-id="1c286-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="1c286-175">Multiset</span></span>|<span data-ttu-id="1c286-176">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-177">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-178">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-179">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-180">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-181">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-182">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="1c286-183">Ref</span><span class="sxs-lookup"><span data-stu-id="1c286-183">Ref</span></span>|<span data-ttu-id="1c286-184">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="1c286-185">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="1c286-186">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="1c286-187">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="1c286-188">Throw</span><span class="sxs-lookup"><span data-stu-id="1c286-188">Throw</span></span>|<span data-ttu-id="1c286-189">Throw</span><span class="sxs-lookup"><span data-stu-id="1c286-189">Throw</span></span>|<span data-ttu-id="1c286-190">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="1c286-191">Associação</span><span class="sxs-lookup"><span data-stu-id="1c286-191">Association</span></span><br /><br /> <span data-ttu-id="1c286-192">tipo</span><span class="sxs-lookup"><span data-stu-id="1c286-192">type</span></span>|<span data-ttu-id="1c286-193">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-194">Throw</span><span class="sxs-lookup"><span data-stu-id="1c286-194">Throw</span></span>|<span data-ttu-id="1c286-195">Throw</span><span class="sxs-lookup"><span data-stu-id="1c286-195">Throw</span></span>|<span data-ttu-id="1c286-196">Throw</span><span class="sxs-lookup"><span data-stu-id="1c286-196">Throw</span></span>|<span data-ttu-id="1c286-197">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-198">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="1c286-199">Lançamento<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="1c286-200"><sup>1</sup> As referências das instâncias de tipo de entidade fornecidas são implicitamente comparadas, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1c286-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="1c286-201">Uma instância de entidade não pode ser comparado a uma referência explícita.</span><span class="sxs-lookup"><span data-stu-id="1c286-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="1c286-202">Se isso for tentada, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="1c286-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="1c286-203">Por exemplo, a seguinte consulta irá acionar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="1c286-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="1c286-204"><sup>2</sup> As propriedades de tipos complexos são achatadas antes de serem enviadas para o armazenamento, de modo que se tornem comparáveis (desde que todas as suas propriedades sejam comparáveis).</span><span class="sxs-lookup"><span data-stu-id="1c286-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="1c286-205">Consulte também <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="1c286-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="1c286-206"><sup>3</sup> O tempo de execução do Entity Framework detecta o caso sem suporte e gera uma exceção significativa sem envolver o provedor/repositório.</span><span class="sxs-lookup"><span data-stu-id="1c286-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="1c286-207"><sup>4</sup> É feita uma tentativa de comparar todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="1c286-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="1c286-208">Se houver uma propriedade que é de um tipo não comparável, como texto, o ntext, ou imagem, uma exceção de servidor pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="1c286-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="1c286-209"><sup>5</sup> Todos os elementos individuais das referências são comparados (isso inclui o nome do conjunto de entidades e todas as propriedades de chave do tipo de entidade).</span><span class="sxs-lookup"><span data-stu-id="1c286-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c286-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c286-210">See also</span></span>

- [<span data-ttu-id="1c286-211">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1c286-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
