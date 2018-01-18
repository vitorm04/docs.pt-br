---
title: "Semântica de comparação (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c6d22b72e05e6293a7fd3bcf7ddfba6e116e441f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="8f750-102">Semântica de comparação (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8f750-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="8f750-103">Executar alguns dos seguintes operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] envolve a comparação de instâncias do tipo:</span><span class="sxs-lookup"><span data-stu-id="8f750-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="8f750-104">Comparação explícita</span><span class="sxs-lookup"><span data-stu-id="8f750-104">Explicit comparison</span></span>  
 <span data-ttu-id="8f750-105">Operações de igualdade:</span><span class="sxs-lookup"><span data-stu-id="8f750-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="8f750-106">!=</span><span class="sxs-lookup"><span data-stu-id="8f750-106">!=</span></span>  
  
 <span data-ttu-id="8f750-107">Ordenando operações:</span><span class="sxs-lookup"><span data-stu-id="8f750-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="8f750-108">Operações de nulidade:</span><span class="sxs-lookup"><span data-stu-id="8f750-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="8f750-109">É NULO</span><span class="sxs-lookup"><span data-stu-id="8f750-109">IS NULL</span></span>  
  
-   <span data-ttu-id="8f750-110">NÃO É NULO</span><span class="sxs-lookup"><span data-stu-id="8f750-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="8f750-111">Distinção explícita</span><span class="sxs-lookup"><span data-stu-id="8f750-111">Explicit distinction</span></span>  
 <span data-ttu-id="8f750-112">Distinção de igualdade:</span><span class="sxs-lookup"><span data-stu-id="8f750-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="8f750-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="8f750-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="8f750-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="8f750-114">GROUP BY</span></span>  
  
 <span data-ttu-id="8f750-115">Classificação a distinção:</span><span class="sxs-lookup"><span data-stu-id="8f750-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="8f750-116">ORDENAR POR</span><span class="sxs-lookup"><span data-stu-id="8f750-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="8f750-117">Distinção implícita</span><span class="sxs-lookup"><span data-stu-id="8f750-117">Implicit distinction</span></span>  
 <span data-ttu-id="8f750-118">Definir operações e predicados (igualdade):</span><span class="sxs-lookup"><span data-stu-id="8f750-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="8f750-119">UNION</span><span class="sxs-lookup"><span data-stu-id="8f750-119">UNION</span></span>  
  
-   <span data-ttu-id="8f750-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="8f750-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="8f750-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="8f750-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="8f750-122">SET</span><span class="sxs-lookup"><span data-stu-id="8f750-122">SET</span></span>  
  
-   <span data-ttu-id="8f750-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="8f750-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="8f750-124">Predicados de item (igual):</span><span class="sxs-lookup"><span data-stu-id="8f750-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="8f750-125">IN</span><span class="sxs-lookup"><span data-stu-id="8f750-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="8f750-126">Combinações suportados</span><span class="sxs-lookup"><span data-stu-id="8f750-126">Supported Combinations</span></span>  
 <span data-ttu-id="8f750-127">A tabela a seguir mostra todas as combinações suportados operadores de comparação para cada tipo do tipo:</span><span class="sxs-lookup"><span data-stu-id="8f750-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="8f750-128">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="8f750-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="8f750-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="8f750-129">**!=**</span></span>|<span data-ttu-id="8f750-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="8f750-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="8f750-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="8f750-131">**DISTINCT**</span></span>|<span data-ttu-id="8f750-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="8f750-132">**UNION**</span></span><br /><br /> <span data-ttu-id="8f750-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="8f750-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="8f750-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="8f750-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="8f750-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="8f750-135">**SET**</span></span><br /><br /> <span data-ttu-id="8f750-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="8f750-136">**OVERLAPS**</span></span>|<span data-ttu-id="8f750-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="8f750-137">**IN**</span></span>|<span data-ttu-id="8f750-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="8f750-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="8f750-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="8f750-139">**>   >=**</span></span>|<span data-ttu-id="8f750-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="8f750-140">**ORDER BY**</span></span>|<span data-ttu-id="8f750-141">**É NULO**</span><span class="sxs-lookup"><span data-stu-id="8f750-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="8f750-142">**NÃO É NULO**</span><span class="sxs-lookup"><span data-stu-id="8f750-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="8f750-143">Tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="8f750-143">Entity type</span></span>|<span data-ttu-id="8f750-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="8f750-145">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="8f750-146">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="8f750-147">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="8f750-148">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-149">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="8f750-151">Tipo complexo</span><span class="sxs-lookup"><span data-stu-id="8f750-151">Complex type</span></span>|<span data-ttu-id="8f750-152">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-153">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-154">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-155">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-156">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-157">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-158">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="8f750-159">Row</span><span class="sxs-lookup"><span data-stu-id="8f750-159">Row</span></span>|<span data-ttu-id="8f750-160">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="8f750-161">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="8f750-162">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="8f750-163">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-164">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-165">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="8f750-166">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="8f750-167">Tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="8f750-167">Primitive type</span></span>|<span data-ttu-id="8f750-168">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="8f750-168">Provider-specific</span></span>|<span data-ttu-id="8f750-169">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="8f750-169">Provider-specific</span></span>|<span data-ttu-id="8f750-170">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="8f750-170">Provider-specific</span></span>|<span data-ttu-id="8f750-171">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="8f750-171">Provider-specific</span></span>|<span data-ttu-id="8f750-172">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="8f750-172">Provider-specific</span></span>|<span data-ttu-id="8f750-173">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="8f750-173">Provider-specific</span></span>|<span data-ttu-id="8f750-174">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="8f750-174">Provider-specific</span></span>|  
|<span data-ttu-id="8f750-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="8f750-175">Multiset</span></span>|<span data-ttu-id="8f750-176">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-177">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-178">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-179">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-180">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-181">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-182">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="8f750-183">Ref</span><span class="sxs-lookup"><span data-stu-id="8f750-183">Ref</span></span>|<span data-ttu-id="8f750-184">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="8f750-185">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="8f750-186">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="8f750-187">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="8f750-188">Throw</span><span class="sxs-lookup"><span data-stu-id="8f750-188">Throw</span></span>|<span data-ttu-id="8f750-189">Throw</span><span class="sxs-lookup"><span data-stu-id="8f750-189">Throw</span></span>|<span data-ttu-id="8f750-190">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="8f750-191">Associação</span><span class="sxs-lookup"><span data-stu-id="8f750-191">Association</span></span><br /><br /> <span data-ttu-id="8f750-192">tipo</span><span class="sxs-lookup"><span data-stu-id="8f750-192">type</span></span>|<span data-ttu-id="8f750-193">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-194">Throw</span><span class="sxs-lookup"><span data-stu-id="8f750-194">Throw</span></span>|<span data-ttu-id="8f750-195">Throw</span><span class="sxs-lookup"><span data-stu-id="8f750-195">Throw</span></span>|<span data-ttu-id="8f750-196">Throw</span><span class="sxs-lookup"><span data-stu-id="8f750-196">Throw</span></span>|<span data-ttu-id="8f750-197">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-198">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="8f750-199">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="8f750-200"><sup>1</sup>as referências das instâncias do tipo de entidade fornecido implicitamente são comparadas, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8f750-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="8f750-201">Uma instância de entidade não pode ser comparado a uma referência explícita.</span><span class="sxs-lookup"><span data-stu-id="8f750-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="8f750-202">Se isso for tentada, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="8f750-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="8f750-203">Por exemplo, a seguinte consulta irá acionar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="8f750-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="8f750-204"><sup>2</sup>propriedades de tipos complexos são esticadas antes de serem enviados para o armazenamento, para que se tornem comparável (contanto que todas as suas propriedades são comparáveis).</span><span class="sxs-lookup"><span data-stu-id="8f750-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="8f750-205">Consulte também <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="8f750-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="8f750-206"><sup>3</sup>o Entity Framework runtime detecta o caso de suporte e lança uma exceção significativa sem envolver o provedor/armazenamento.</span><span class="sxs-lookup"><span data-stu-id="8f750-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="8f750-207"><sup>4</sup>é feita uma tentativa de comparar todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="8f750-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="8f750-208">Se houver uma propriedade que é de um tipo não comparável, como texto, o ntext, ou imagem, uma exceção de servidor pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="8f750-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="8f750-209"><sup>5</sup>todos os elementos individuais de referências são comparados (Isso inclui o nome do conjunto de entidade e todas as propriedades de chave do tipo de entidade).</span><span class="sxs-lookup"><span data-stu-id="8f750-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f750-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f750-210">See Also</span></span>  
 [<span data-ttu-id="8f750-211">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8f750-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
