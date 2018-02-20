---
title: "Semântica de comparação (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e20d47e0ae97067d2dcafcf929f717598d4e3e80
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="639c4-102">Semântica de comparação (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="639c4-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="639c4-103">Executar alguns dos seguintes operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] envolve a comparação de instâncias do tipo:</span><span class="sxs-lookup"><span data-stu-id="639c4-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="639c4-104">Comparação explícita</span><span class="sxs-lookup"><span data-stu-id="639c4-104">Explicit comparison</span></span>  
 <span data-ttu-id="639c4-105">Operações de igualdade:</span><span class="sxs-lookup"><span data-stu-id="639c4-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="639c4-106">!=</span><span class="sxs-lookup"><span data-stu-id="639c4-106">!=</span></span>  
  
 <span data-ttu-id="639c4-107">Ordenando operações:</span><span class="sxs-lookup"><span data-stu-id="639c4-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="639c4-108">Operações de nulidade:</span><span class="sxs-lookup"><span data-stu-id="639c4-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="639c4-109">É NULO</span><span class="sxs-lookup"><span data-stu-id="639c4-109">IS NULL</span></span>  
  
-   <span data-ttu-id="639c4-110">NÃO É NULO</span><span class="sxs-lookup"><span data-stu-id="639c4-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="639c4-111">Distinção explícita</span><span class="sxs-lookup"><span data-stu-id="639c4-111">Explicit distinction</span></span>  
 <span data-ttu-id="639c4-112">Distinção de igualdade:</span><span class="sxs-lookup"><span data-stu-id="639c4-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="639c4-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="639c4-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="639c4-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="639c4-114">GROUP BY</span></span>  
  
 <span data-ttu-id="639c4-115">Classificação a distinção:</span><span class="sxs-lookup"><span data-stu-id="639c4-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="639c4-116">ORDENAR POR</span><span class="sxs-lookup"><span data-stu-id="639c4-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="639c4-117">Distinção implícita</span><span class="sxs-lookup"><span data-stu-id="639c4-117">Implicit distinction</span></span>  
 <span data-ttu-id="639c4-118">Definir operações e predicados (igualdade):</span><span class="sxs-lookup"><span data-stu-id="639c4-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="639c4-119">UNION</span><span class="sxs-lookup"><span data-stu-id="639c4-119">UNION</span></span>  
  
-   <span data-ttu-id="639c4-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="639c4-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="639c4-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="639c4-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="639c4-122">SET</span><span class="sxs-lookup"><span data-stu-id="639c4-122">SET</span></span>  
  
-   <span data-ttu-id="639c4-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="639c4-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="639c4-124">Predicados de item (igual):</span><span class="sxs-lookup"><span data-stu-id="639c4-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="639c4-125">IN</span><span class="sxs-lookup"><span data-stu-id="639c4-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="639c4-126">Combinações suportados</span><span class="sxs-lookup"><span data-stu-id="639c4-126">Supported Combinations</span></span>  
 <span data-ttu-id="639c4-127">A tabela a seguir mostra todas as combinações suportados operadores de comparação para cada tipo do tipo:</span><span class="sxs-lookup"><span data-stu-id="639c4-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="639c4-128">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="639c4-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="639c4-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="639c4-129">**!=**</span></span>|<span data-ttu-id="639c4-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="639c4-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="639c4-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="639c4-131">**DISTINCT**</span></span>|<span data-ttu-id="639c4-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="639c4-132">**UNION**</span></span><br /><br /> <span data-ttu-id="639c4-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="639c4-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="639c4-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="639c4-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="639c4-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="639c4-135">**SET**</span></span><br /><br /> <span data-ttu-id="639c4-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="639c4-136">**OVERLAPS**</span></span>|<span data-ttu-id="639c4-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="639c4-137">**IN**</span></span>|<span data-ttu-id="639c4-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="639c4-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="639c4-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="639c4-139">**>   >=**</span></span>|<span data-ttu-id="639c4-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="639c4-140">**ORDER BY**</span></span>|<span data-ttu-id="639c4-141">**É NULO**</span><span class="sxs-lookup"><span data-stu-id="639c4-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="639c4-142">**NÃO É NULO**</span><span class="sxs-lookup"><span data-stu-id="639c4-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="639c4-143">Tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="639c4-143">Entity type</span></span>|<span data-ttu-id="639c4-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="639c4-145">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="639c4-146">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="639c4-147">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="639c4-148">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-149">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="639c4-151">Tipo complexo</span><span class="sxs-lookup"><span data-stu-id="639c4-151">Complex type</span></span>|<span data-ttu-id="639c4-152">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-153">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-154">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-155">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-156">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-157">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-158">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="639c4-159">Row</span><span class="sxs-lookup"><span data-stu-id="639c4-159">Row</span></span>|<span data-ttu-id="639c4-160">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="639c4-161">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="639c4-162">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="639c4-163">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-164">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-165">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="639c4-166">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="639c4-167">Tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="639c4-167">Primitive type</span></span>|<span data-ttu-id="639c4-168">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="639c4-168">Provider-specific</span></span>|<span data-ttu-id="639c4-169">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="639c4-169">Provider-specific</span></span>|<span data-ttu-id="639c4-170">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="639c4-170">Provider-specific</span></span>|<span data-ttu-id="639c4-171">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="639c4-171">Provider-specific</span></span>|<span data-ttu-id="639c4-172">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="639c4-172">Provider-specific</span></span>|<span data-ttu-id="639c4-173">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="639c4-173">Provider-specific</span></span>|<span data-ttu-id="639c4-174">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="639c4-174">Provider-specific</span></span>|  
|<span data-ttu-id="639c4-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="639c4-175">Multiset</span></span>|<span data-ttu-id="639c4-176">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-177">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-178">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-179">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-180">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-181">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-182">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="639c4-183">Ref</span><span class="sxs-lookup"><span data-stu-id="639c4-183">Ref</span></span>|<span data-ttu-id="639c4-184">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="639c4-185">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="639c4-186">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="639c4-187">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="639c4-188">Throw</span><span class="sxs-lookup"><span data-stu-id="639c4-188">Throw</span></span>|<span data-ttu-id="639c4-189">Throw</span><span class="sxs-lookup"><span data-stu-id="639c4-189">Throw</span></span>|<span data-ttu-id="639c4-190">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="639c4-191">Associação</span><span class="sxs-lookup"><span data-stu-id="639c4-191">Association</span></span><br /><br /> <span data-ttu-id="639c4-192">tipo</span><span class="sxs-lookup"><span data-stu-id="639c4-192">type</span></span>|<span data-ttu-id="639c4-193">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-194">Throw</span><span class="sxs-lookup"><span data-stu-id="639c4-194">Throw</span></span>|<span data-ttu-id="639c4-195">Throw</span><span class="sxs-lookup"><span data-stu-id="639c4-195">Throw</span></span>|<span data-ttu-id="639c4-196">Throw</span><span class="sxs-lookup"><span data-stu-id="639c4-196">Throw</span></span>|<span data-ttu-id="639c4-197">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-198">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="639c4-199">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="639c4-200"><sup>1</sup>as referências das instâncias do tipo de entidade fornecido implicitamente são comparadas, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="639c4-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="639c4-201">Uma instância de entidade não pode ser comparado a uma referência explícita.</span><span class="sxs-lookup"><span data-stu-id="639c4-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="639c4-202">Se isso for tentada, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="639c4-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="639c4-203">Por exemplo, a seguinte consulta irá acionar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="639c4-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="639c4-204"><sup>2</sup>propriedades de tipos complexos são esticadas antes de serem enviados para o armazenamento, para que se tornem comparável (contanto que todas as suas propriedades são comparáveis).</span><span class="sxs-lookup"><span data-stu-id="639c4-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="639c4-205">Consulte também <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="639c4-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="639c4-206"><sup>3</sup>o Entity Framework runtime detecta o caso de suporte e lança uma exceção significativa sem envolver o provedor/armazenamento.</span><span class="sxs-lookup"><span data-stu-id="639c4-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="639c4-207"><sup>4</sup>é feita uma tentativa de comparar todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="639c4-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="639c4-208">Se houver uma propriedade que é de um tipo não comparável, como texto, o ntext, ou imagem, uma exceção de servidor pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="639c4-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="639c4-209"><sup>5</sup>todos os elementos individuais de referências são comparados (Isso inclui o nome do conjunto de entidade e todas as propriedades de chave do tipo de entidade).</span><span class="sxs-lookup"><span data-stu-id="639c4-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639c4-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="639c4-210">See Also</span></span>  
 [<span data-ttu-id="639c4-211">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="639c4-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
