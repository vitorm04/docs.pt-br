---
title: Função CompareAssemblyIdentity
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 652000367c19572f73296c704047830ce1c74574
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231015"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="dbb29-102">Função CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="dbb29-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="dbb29-103">Compara duas identidades de assembly para determinar se eles são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="dbb29-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbb29-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbb29-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dbb29-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbb29-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="dbb29-106">[in] A identidade textual do assembly primeiro na comparação.</span><span class="sxs-lookup"><span data-stu-id="dbb29-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="dbb29-107">[in] Um sinalizador booleano que indica a Unificação especificado pelo usuário para `pwzAssemblyIdentity1`.</span><span class="sxs-lookup"><span data-stu-id="dbb29-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="dbb29-108">[in] A identidade textual do segundo assembly na comparação.</span><span class="sxs-lookup"><span data-stu-id="dbb29-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="dbb29-109">[in] Um sinalizador booleano que indica a Unificação especificado pelo usuário para `pwzAssemblyIdentity2`.</span><span class="sxs-lookup"><span data-stu-id="dbb29-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="dbb29-110">[out] Um sinalizador booliano que indica se os dois assemblies são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="dbb29-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="dbb29-111">[out] Uma [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeração que contém informações detalhadas sobre a comparação.</span><span class="sxs-lookup"><span data-stu-id="dbb29-111">[out] An [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbb29-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dbb29-112">Return Value</span></span>  
 <span data-ttu-id="dbb29-113">`pfEquivalent` Retorna um valor booliano que indica se os dois assemblies são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="dbb29-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="dbb29-114">`pResult` Retorna um dos `AssemblyComparisonResult` valores, para fornecer um motivo mais detalhado para o valor de `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="dbb29-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbb29-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="dbb29-115">Remarks</span></span>  
 <span data-ttu-id="dbb29-116">`CompareAssemblyIdentity` verifica se `pwzAssemblyIdentity1` e `pwzAssemblyIdentity2` são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="dbb29-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="dbb29-117">`pfEquivalent` é definido como `true` em uma ou mais das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="dbb29-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
-   <span data-ttu-id="dbb29-118">As identidades de duas assembly são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="dbb29-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="dbb29-119">Para assemblies fortemente nomeados, equivalência requer o nome do assembly, versão, token de chave pública e cultura sejam idênticos.</span><span class="sxs-lookup"><span data-stu-id="dbb29-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="dbb29-120">Para assemblies de nomeados simples, a equivalência requer uma correspondência no nome do assembly e cultura.</span><span class="sxs-lookup"><span data-stu-id="dbb29-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
-   <span data-ttu-id="dbb29-121">Ambas as identidades de assembly se referem aos assemblies que são executados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dbb29-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="dbb29-122">Essa condição retorna `true` mesmo se os números de versão do assembly não coincidem.</span><span class="sxs-lookup"><span data-stu-id="dbb29-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
-   <span data-ttu-id="dbb29-123">Os dois assemblies não são assemblies gerenciados, mas `fUnified1` ou `fUnified2` foi definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="dbb29-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="dbb29-124">O `fUnified` sinalizador indica que todos os números de versão até o número de versão do assembly de nome forte são considerados equivalentes para o assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="dbb29-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="dbb29-125">Por exemplo, se o valor de `pwzAssemblyIndentity1` é "MyAssembly, versão = 3.0.0.0, culture = neutral, publicKeyToken =..." e o valor da `fUnified1` é `true`, isso indica que todas as versões de MyAssembly da versão de 0.0.0.0 à 3.0.0.0 devem ser tratados como equivalentes.</span><span class="sxs-lookup"><span data-stu-id="dbb29-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="dbb29-126">Nesse caso, se `pwzAssemblyIndentity2` refere-se ao mesmo assembly que `pwzAssemblyIndentity1`, exceto que ele tem um número de versão menor `pfEquivalent` é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="dbb29-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="dbb29-127">Se `pwzAssemblyIdentity2` refere-se a um número de versão superior `pfEquivalent` é definido como `true` somente se o valor de `fUnified2` é `true`.</span><span class="sxs-lookup"><span data-stu-id="dbb29-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="dbb29-128">O `pResult` parâmetro inclui informações específicas sobre por que os dois assemblies são considerados equivalentes ou não equivalentes.</span><span class="sxs-lookup"><span data-stu-id="dbb29-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="dbb29-129">Para obter mais informações, consulte [enumeração AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="dbb29-129">For more information, see [AssemblyComparisonResult Enumeration](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbb29-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbb29-130">Requirements</span></span>  
 <span data-ttu-id="dbb29-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbb29-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbb29-132">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="dbb29-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="dbb29-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dbb29-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dbb29-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbb29-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb29-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbb29-135">See also</span></span>

- [<span data-ttu-id="dbb29-136">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="dbb29-136">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="dbb29-137">Enumeração AssemblyComparisonResult</span><span class="sxs-lookup"><span data-stu-id="dbb29-137">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
