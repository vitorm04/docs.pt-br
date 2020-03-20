---
title: Semântica de comparação (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150448"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="19c9c-102">Semântica de comparação (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="19c9c-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="19c9c-103">Executar alguns dos seguintes operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] envolve a comparação de instâncias do tipo:</span><span class="sxs-lookup"><span data-stu-id="19c9c-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="19c9c-104">Comparação explícita</span><span class="sxs-lookup"><span data-stu-id="19c9c-104">Explicit comparison</span></span>  
 <span data-ttu-id="19c9c-105">Operações de igualdade:</span><span class="sxs-lookup"><span data-stu-id="19c9c-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="19c9c-106">!=</span><span class="sxs-lookup"><span data-stu-id="19c9c-106">!=</span></span>  
  
 <span data-ttu-id="19c9c-107">Ordenando operações:</span><span class="sxs-lookup"><span data-stu-id="19c9c-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="19c9c-108">Operações de nulidade:</span><span class="sxs-lookup"><span data-stu-id="19c9c-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="19c9c-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="19c9c-109">IS NULL</span></span>  
  
- <span data-ttu-id="19c9c-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="19c9c-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="19c9c-111">Distinção explícita</span><span class="sxs-lookup"><span data-stu-id="19c9c-111">Explicit distinction</span></span>  
 <span data-ttu-id="19c9c-112">Distinção de igualdade:</span><span class="sxs-lookup"><span data-stu-id="19c9c-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="19c9c-113">DISTINTO</span><span class="sxs-lookup"><span data-stu-id="19c9c-113">DISTINCT</span></span>  
  
- <span data-ttu-id="19c9c-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="19c9c-114">GROUP BY</span></span>  
  
 <span data-ttu-id="19c9c-115">Classificação a distinção:</span><span class="sxs-lookup"><span data-stu-id="19c9c-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="19c9c-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="19c9c-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="19c9c-117">Distinção implícita</span><span class="sxs-lookup"><span data-stu-id="19c9c-117">Implicit distinction</span></span>  
 <span data-ttu-id="19c9c-118">Definir operações e predicados (igualdade):</span><span class="sxs-lookup"><span data-stu-id="19c9c-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="19c9c-119">UNION</span><span class="sxs-lookup"><span data-stu-id="19c9c-119">UNION</span></span>  
  
- <span data-ttu-id="19c9c-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="19c9c-120">INTERSECT</span></span>  
  
- <span data-ttu-id="19c9c-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="19c9c-121">EXCEPT</span></span>  
  
- <span data-ttu-id="19c9c-122">SET</span><span class="sxs-lookup"><span data-stu-id="19c9c-122">SET</span></span>  
  
- <span data-ttu-id="19c9c-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="19c9c-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="19c9c-124">Predicados de item (igual):</span><span class="sxs-lookup"><span data-stu-id="19c9c-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="19c9c-125">IN</span><span class="sxs-lookup"><span data-stu-id="19c9c-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="19c9c-126">Combinações com suporte</span><span class="sxs-lookup"><span data-stu-id="19c9c-126">Supported Combinations</span></span>  
 <span data-ttu-id="19c9c-127">A tabela a seguir mostra todas as combinações suportados operadores de comparação para cada tipo do tipo:</span><span class="sxs-lookup"><span data-stu-id="19c9c-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="19c9c-128">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="19c9c-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="19c9c-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="19c9c-129">**!=**</span></span>|<span data-ttu-id="19c9c-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="19c9c-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="19c9c-131">**Distintas**</span><span class="sxs-lookup"><span data-stu-id="19c9c-131">**DISTINCT**</span></span>|<span data-ttu-id="19c9c-132">**União**</span><span class="sxs-lookup"><span data-stu-id="19c9c-132">**UNION**</span></span><br /><br /> <span data-ttu-id="19c9c-133">**Intersect**</span><span class="sxs-lookup"><span data-stu-id="19c9c-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="19c9c-134">**Exceto**</span><span class="sxs-lookup"><span data-stu-id="19c9c-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="19c9c-135">**Definir**</span><span class="sxs-lookup"><span data-stu-id="19c9c-135">**SET**</span></span><br /><br /> <span data-ttu-id="19c9c-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="19c9c-136">**OVERLAPS**</span></span>|<span data-ttu-id="19c9c-137">**Em**</span><span class="sxs-lookup"><span data-stu-id="19c9c-137">**IN**</span></span>|<span data-ttu-id="19c9c-138">**< <=**</span><span class="sxs-lookup"><span data-stu-id="19c9c-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="19c9c-139">**> >=**</span><span class="sxs-lookup"><span data-stu-id="19c9c-139">**>   >=**</span></span>|<span data-ttu-id="19c9c-140">**ORDEM POR**</span><span class="sxs-lookup"><span data-stu-id="19c9c-140">**ORDER BY**</span></span>|<span data-ttu-id="19c9c-141">**É NULO**</span><span class="sxs-lookup"><span data-stu-id="19c9c-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="19c9c-142">**NÃO É NULO**</span><span class="sxs-lookup"><span data-stu-id="19c9c-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="19c9c-143">Tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="19c9c-143">Entity type</span></span>|<span data-ttu-id="19c9c-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="19c9c-145">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="19c9c-146">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="19c9c-147">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="19c9c-148">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-149">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="19c9c-151">Tipo complexo</span><span class="sxs-lookup"><span data-stu-id="19c9c-151">Complex type</span></span>|<span data-ttu-id="19c9c-152">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-153">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-154">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-155">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-156">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-157">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-158">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="19c9c-159">Linha</span><span class="sxs-lookup"><span data-stu-id="19c9c-159">Row</span></span>|<span data-ttu-id="19c9c-160">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="19c9c-161">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="19c9c-162">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="19c9c-163">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-164">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-165">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="19c9c-166">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="19c9c-167">Tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="19c9c-167">Primitive type</span></span>|<span data-ttu-id="19c9c-168">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="19c9c-168">Provider-specific</span></span>|<span data-ttu-id="19c9c-169">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="19c9c-169">Provider-specific</span></span>|<span data-ttu-id="19c9c-170">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="19c9c-170">Provider-specific</span></span>|<span data-ttu-id="19c9c-171">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="19c9c-171">Provider-specific</span></span>|<span data-ttu-id="19c9c-172">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="19c9c-172">Provider-specific</span></span>|<span data-ttu-id="19c9c-173">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="19c9c-173">Provider-specific</span></span>|<span data-ttu-id="19c9c-174">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="19c9c-174">Provider-specific</span></span>|  
|<span data-ttu-id="19c9c-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="19c9c-175">Multiset</span></span>|<span data-ttu-id="19c9c-176">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-177">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-178">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-179">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-180">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-181">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-182">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="19c9c-183">Ref</span><span class="sxs-lookup"><span data-stu-id="19c9c-183">Ref</span></span>|<span data-ttu-id="19c9c-184">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="19c9c-185">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="19c9c-186">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="19c9c-187">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="19c9c-188">Throw</span><span class="sxs-lookup"><span data-stu-id="19c9c-188">Throw</span></span>|<span data-ttu-id="19c9c-189">Throw</span><span class="sxs-lookup"><span data-stu-id="19c9c-189">Throw</span></span>|<span data-ttu-id="19c9c-190">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="19c9c-191">Associação</span><span class="sxs-lookup"><span data-stu-id="19c9c-191">Association</span></span><br /><br /> <span data-ttu-id="19c9c-192">type</span><span class="sxs-lookup"><span data-stu-id="19c9c-192">type</span></span>|<span data-ttu-id="19c9c-193">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-194">Throw</span><span class="sxs-lookup"><span data-stu-id="19c9c-194">Throw</span></span>|<span data-ttu-id="19c9c-195">Throw</span><span class="sxs-lookup"><span data-stu-id="19c9c-195">Throw</span></span>|<span data-ttu-id="19c9c-196">Throw</span><span class="sxs-lookup"><span data-stu-id="19c9c-196">Throw</span></span>|<span data-ttu-id="19c9c-197">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-198">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="19c9c-199">Lance<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="19c9c-200"><sup>1</sup> As referências das instâncias de tipo de entidade dadas são implicitamente comparadas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="19c9c-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="19c9c-201">Uma instância de entidade não pode ser comparado a uma referência explícita.</span><span class="sxs-lookup"><span data-stu-id="19c9c-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="19c9c-202">Se isso for tentada, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="19c9c-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="19c9c-203">Por exemplo, a seguinte consulta irá acionar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="19c9c-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="19c9c-204"><sup>2</sup> Propriedades de tipos complexos são achatadas antes de serem enviadas para a loja, de modo que se tornam comparáveis (desde que todas as suas propriedades sejam comparáveis).</span><span class="sxs-lookup"><span data-stu-id="19c9c-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="19c9c-205">Veja também <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="19c9c-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="19c9c-206"><sup>3</sup> O tempo de execução do Entity Framework detecta o caso sem suporte e lança uma exceção significativa sem engajar o provedor/loja.</span><span class="sxs-lookup"><span data-stu-id="19c9c-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="19c9c-207"><sup>4</sup> Uma tentativa é feita para comparar todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="19c9c-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="19c9c-208">Se houver uma propriedade que é de um tipo não comparável, como texto, o ntext, ou imagem, uma exceção de servidor pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="19c9c-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="19c9c-209"><sup>5</sup> Todos os elementos individuais das referências são comparados (isso inclui o nome do conjunto da entidade e todas as propriedades-chave do tipo entidade).</span><span class="sxs-lookup"><span data-stu-id="19c9c-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c9c-210">Confira também</span><span class="sxs-lookup"><span data-stu-id="19c9c-210">See also</span></span>

- [<span data-ttu-id="19c9c-211">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="19c9c-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
