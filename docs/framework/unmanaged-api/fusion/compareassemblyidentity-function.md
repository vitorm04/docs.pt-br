---
title: "Função CompareAssemblyIdentity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: CompareAssemblyIdentity
helpviewer_keywords: CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 266868a65a0db75b57d46d92a469b4b6ceaa88e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="73724-102">Função CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="73724-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="73724-103">Compara duas identidades de assembly para determinar se eles são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="73724-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73724-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73724-104">Syntax</span></span>  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73724-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73724-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="73724-106">[in] A identidade textual do primeiro conjunto na comparação.</span><span class="sxs-lookup"><span data-stu-id="73724-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="73724-107">[in] Um sinalizador booleano que indica a união de usuário especificado para `pwzAssemblyIdentity1`.</span><span class="sxs-lookup"><span data-stu-id="73724-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="73724-108">[in] A identidade textual do segundo assembly na comparação.</span><span class="sxs-lookup"><span data-stu-id="73724-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="73724-109">[in] Um sinalizador booleano que indica a união de usuário especificado para `pwzAssemblyIdentity2`.</span><span class="sxs-lookup"><span data-stu-id="73724-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="73724-110">[out] Um sinalizador booliano que indica se os dois assemblies são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="73724-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="73724-111">[out] Um [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeração que contém informações detalhadas sobre a comparação.</span><span class="sxs-lookup"><span data-stu-id="73724-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73724-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="73724-112">Return Value</span></span>  
 <span data-ttu-id="73724-113">`pfEquivalent`Retorna um valor booliano que indica se os dois assemblies são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="73724-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="73724-114">`pResult`Retorna um do `AssemblyComparisonResult` valores, para fornecer um motivo mais detalhado para o valor de `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="73724-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73724-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="73724-115">Remarks</span></span>  
 <span data-ttu-id="73724-116">`CompareAssemblyIdentity`verifica se `pwzAssemblyIdentity1` e `pwzAssemblyIdentity2` são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="73724-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="73724-117">`pfEquivalent`é definido como `true` em uma ou mais das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="73724-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="73724-118">As identidades de duas assembly são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="73724-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="73724-119">Para assemblies de nomeados forte, equivalência requer o nome do assembly, versão, token de chave pública e a cultura a ser idênticos.</span><span class="sxs-lookup"><span data-stu-id="73724-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="73724-120">Para assemblies nomeados simplesmente, equivalência requer uma correspondência no nome do assembly e cultura.</span><span class="sxs-lookup"><span data-stu-id="73724-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="73724-121">Ambas as identidades de assembly, consulte assemblies que são executados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="73724-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="73724-122">Essa condição retornará `true` mesmo se os números de versão do assembly não coincidem.</span><span class="sxs-lookup"><span data-stu-id="73724-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="73724-123">Os dois assemblies não são assemblies gerenciados, mas `fUnified1` ou `fUnified2` foi definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="73724-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="73724-124">O `fUnified` sinalizador indica que todos os números de versão até o número de versão do assembly de nome forte são considerados equivalentes para o assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="73724-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="73724-125">Por exemplo, se o valor de `pwzAssemblyIndentity1` é "MyAssembly, versão = 3.0.0.0, culture = neutral, publicKeyToken =..." e o valor de `fUnified1` é `true`, isso indica que todas as versões do MyAssembly da versão 0.0.0.0 para 3.0.0.0 devem ser tratados como equivalentes.</span><span class="sxs-lookup"><span data-stu-id="73724-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="73724-126">Nesse caso, se `pwzAssemblyIndentity2` refere-se ao mesmo assembly como `pwzAssemblyIndentity1`, exceto que ele tem um número de versão inferior, `pfEquivalent` é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="73724-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="73724-127">Se `pwzAssemblyIdentity2` refere-se a um número de versão superior, `pfEquivalent` é definido como `true` somente se o valor de `fUnified2` é `true`.</span><span class="sxs-lookup"><span data-stu-id="73724-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="73724-128">O `pResult` parâmetro inclui informações específicas sobre por que os dois assemblies são considerados equivalente ou não equivalente.</span><span class="sxs-lookup"><span data-stu-id="73724-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="73724-129">Para obter mais informações, consulte [enumeração AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="73724-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73724-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73724-130">Requirements</span></span>  
 <span data-ttu-id="73724-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73724-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73724-132">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="73724-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="73724-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="73724-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73724-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73724-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73724-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73724-135">See Also</span></span>  
 [<span data-ttu-id="73724-136">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="73724-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="73724-137">Enumeração AssemblyComparisonResult</span><span class="sxs-lookup"><span data-stu-id="73724-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
