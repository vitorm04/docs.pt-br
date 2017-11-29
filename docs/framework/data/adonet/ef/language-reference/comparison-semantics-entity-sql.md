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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1fd1c21fc4f156bfe7a5abf9f76bd341e2d0f10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="13f30-102">Semântica de comparação (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="13f30-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="13f30-103">Executar alguns dos seguintes operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] envolve a comparação de instâncias do tipo:</span><span class="sxs-lookup"><span data-stu-id="13f30-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="13f30-104">Comparação explícita</span><span class="sxs-lookup"><span data-stu-id="13f30-104">Explicit comparison</span></span>  
 <span data-ttu-id="13f30-105">Operações de igualdade:</span><span class="sxs-lookup"><span data-stu-id="13f30-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="13f30-106">!=</span><span class="sxs-lookup"><span data-stu-id="13f30-106">!=</span></span>  
  
 <span data-ttu-id="13f30-107">Ordenando operações:</span><span class="sxs-lookup"><span data-stu-id="13f30-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="13f30-108">Operações de nulidade:</span><span class="sxs-lookup"><span data-stu-id="13f30-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="13f30-109">É NULO</span><span class="sxs-lookup"><span data-stu-id="13f30-109">IS NULL</span></span>  
  
-   <span data-ttu-id="13f30-110">NÃO É NULO</span><span class="sxs-lookup"><span data-stu-id="13f30-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="13f30-111">Distinção explícita</span><span class="sxs-lookup"><span data-stu-id="13f30-111">Explicit distinction</span></span>  
 <span data-ttu-id="13f30-112">Distinção de igualdade:</span><span class="sxs-lookup"><span data-stu-id="13f30-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="13f30-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="13f30-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="13f30-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="13f30-114">GROUP BY</span></span>  
  
 <span data-ttu-id="13f30-115">Classificação a distinção:</span><span class="sxs-lookup"><span data-stu-id="13f30-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="13f30-116">ORDENAR POR</span><span class="sxs-lookup"><span data-stu-id="13f30-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="13f30-117">Distinção implícita</span><span class="sxs-lookup"><span data-stu-id="13f30-117">Implicit distinction</span></span>  
 <span data-ttu-id="13f30-118">Definir operações e predicados (igualdade):</span><span class="sxs-lookup"><span data-stu-id="13f30-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="13f30-119">UNION</span><span class="sxs-lookup"><span data-stu-id="13f30-119">UNION</span></span>  
  
-   <span data-ttu-id="13f30-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="13f30-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="13f30-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="13f30-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="13f30-122">SET</span><span class="sxs-lookup"><span data-stu-id="13f30-122">SET</span></span>  
  
-   <span data-ttu-id="13f30-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="13f30-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="13f30-124">Predicados de item (igual):</span><span class="sxs-lookup"><span data-stu-id="13f30-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="13f30-125">IN</span><span class="sxs-lookup"><span data-stu-id="13f30-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="13f30-126">Combinações suportados</span><span class="sxs-lookup"><span data-stu-id="13f30-126">Supported Combinations</span></span>  
 <span data-ttu-id="13f30-127">A tabela a seguir mostra todas as combinações suportados operadores de comparação para cada tipo do tipo:</span><span class="sxs-lookup"><span data-stu-id="13f30-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="13f30-128">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="13f30-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="13f30-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="13f30-129">**!=**</span></span>|<span data-ttu-id="13f30-130">**AGRUPAR POR**</span><span class="sxs-lookup"><span data-stu-id="13f30-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="13f30-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="13f30-131">**DISTINCT**</span></span>|<span data-ttu-id="13f30-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="13f30-132">**UNION**</span></span><br /><br /> <span data-ttu-id="13f30-133">**SE CRUZAM**</span><span class="sxs-lookup"><span data-stu-id="13f30-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="13f30-134">**EXCETO**</span><span class="sxs-lookup"><span data-stu-id="13f30-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="13f30-135">**DEFINIR**</span><span class="sxs-lookup"><span data-stu-id="13f30-135">**SET**</span></span><br /><br /> <span data-ttu-id="13f30-136">**SOBREPOSIÇÕES**</span><span class="sxs-lookup"><span data-stu-id="13f30-136">**OVERLAPS**</span></span>|<span data-ttu-id="13f30-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="13f30-137">**IN**</span></span>|<span data-ttu-id="13f30-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="13f30-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="13f30-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="13f30-139">**>   >=**</span></span>|<span data-ttu-id="13f30-140">**ORDENAR POR**</span><span class="sxs-lookup"><span data-stu-id="13f30-140">**ORDER BY**</span></span>|<span data-ttu-id="13f30-141">**É NULO**</span><span class="sxs-lookup"><span data-stu-id="13f30-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="13f30-142">**NÃO É NULO**</span><span class="sxs-lookup"><span data-stu-id="13f30-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="13f30-143">Tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="13f30-143">Entity type</span></span>|<span data-ttu-id="13f30-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="13f30-145">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="13f30-146">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="13f30-147">Todas as propriedades<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="13f30-148">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-149">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="13f30-151">Tipo complexo</span><span class="sxs-lookup"><span data-stu-id="13f30-151">Complex type</span></span>|<span data-ttu-id="13f30-152">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-153">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-154">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-155">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-156">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-157">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-158">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="13f30-159">Row</span><span class="sxs-lookup"><span data-stu-id="13f30-159">Row</span></span>|<span data-ttu-id="13f30-160">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="13f30-161">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="13f30-162">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="13f30-163">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-164">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-165">Todas as propriedades<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="13f30-166">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="13f30-167">Tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="13f30-167">Primitive type</span></span>|<span data-ttu-id="13f30-168">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="13f30-168">Provider-specific</span></span>|<span data-ttu-id="13f30-169">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="13f30-169">Provider-specific</span></span>|<span data-ttu-id="13f30-170">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="13f30-170">Provider-specific</span></span>|<span data-ttu-id="13f30-171">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="13f30-171">Provider-specific</span></span>|<span data-ttu-id="13f30-172">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="13f30-172">Provider-specific</span></span>|<span data-ttu-id="13f30-173">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="13f30-173">Provider-specific</span></span>|<span data-ttu-id="13f30-174">Específica do provedor</span><span class="sxs-lookup"><span data-stu-id="13f30-174">Provider-specific</span></span>|  
|<span data-ttu-id="13f30-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="13f30-175">Multiset</span></span>|<span data-ttu-id="13f30-176">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-177">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-178">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-179">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-180">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-181">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-182">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="13f30-183">Ref</span><span class="sxs-lookup"><span data-stu-id="13f30-183">Ref</span></span>|<span data-ttu-id="13f30-184">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="13f30-185">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="13f30-186">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="13f30-187">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="13f30-188">Throw</span><span class="sxs-lookup"><span data-stu-id="13f30-188">Throw</span></span>|<span data-ttu-id="13f30-189">Throw</span><span class="sxs-lookup"><span data-stu-id="13f30-189">Throw</span></span>|<span data-ttu-id="13f30-190">Sim<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="13f30-191">Associação</span><span class="sxs-lookup"><span data-stu-id="13f30-191">Association</span></span><br /><br /> <span data-ttu-id="13f30-192">tipo</span><span class="sxs-lookup"><span data-stu-id="13f30-192">type</span></span>|<span data-ttu-id="13f30-193">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-194">Throw</span><span class="sxs-lookup"><span data-stu-id="13f30-194">Throw</span></span>|<span data-ttu-id="13f30-195">Throw</span><span class="sxs-lookup"><span data-stu-id="13f30-195">Throw</span></span>|<span data-ttu-id="13f30-196">Throw</span><span class="sxs-lookup"><span data-stu-id="13f30-196">Throw</span></span>|<span data-ttu-id="13f30-197">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-198">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="13f30-199">Lançar<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="13f30-200"><sup>1</sup>as referências das instâncias do tipo de entidade fornecido implicitamente são comparadas, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="13f30-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="13f30-201">Uma instância de entidade não pode ser comparado a uma referência explícita.</span><span class="sxs-lookup"><span data-stu-id="13f30-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="13f30-202">Se isso for tentada, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="13f30-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="13f30-203">Por exemplo, a seguinte consulta irá acionar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="13f30-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="13f30-204"><sup>2</sup>propriedades de tipos complexos são esticadas antes de serem enviados para o armazenamento, para que se tornem comparável (contanto que todas as suas propriedades são comparáveis).</span><span class="sxs-lookup"><span data-stu-id="13f30-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="13f30-205">Consulte também <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="13f30-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="13f30-206"><sup>3</sup>o Entity Framework runtime detecta o caso de suporte e lança uma exceção significativa sem envolver o provedor/armazenamento.</span><span class="sxs-lookup"><span data-stu-id="13f30-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="13f30-207"><sup>4</sup>é feita uma tentativa de comparar todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="13f30-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="13f30-208">Se houver uma propriedade que é de um tipo não comparável, como texto, o ntext, ou imagem, uma exceção de servidor pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="13f30-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="13f30-209"><sup>5</sup>todos os elementos individuais de referências são comparados (Isso inclui o nome do conjunto de entidade e todas as propriedades de chave do tipo de entidade).</span><span class="sxs-lookup"><span data-stu-id="13f30-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f30-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13f30-210">See Also</span></span>  
 [<span data-ttu-id="13f30-211">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="13f30-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
