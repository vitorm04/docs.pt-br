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
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795450"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="b1c7e-102">Função CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="b1c7e-102">CompareAssemblyIdentity Function</span></span>
<span data-ttu-id="b1c7e-103">Compara duas identidades de assembly para determinar se elas são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1c7e-104">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1c7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1c7e-105">Parameters</span></span>  
 `pwzAssemblyIdentity1`  
 <span data-ttu-id="b1c7e-106">no A identidade textual do primeiro assembly na comparação.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="b1c7e-107">no Um sinalizador booliano que indica a unificação especificada `pwzAssemblyIdentity1`pelo usuário para.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="b1c7e-108">no A identidade textual do segundo assembly na comparação.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="b1c7e-109">no Um sinalizador booliano que indica a unificação especificada `pwzAssemblyIdentity2`pelo usuário para.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="b1c7e-110">fora Um sinalizador booliano que indica se os dois assemblies são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="b1c7e-111">fora Uma enumeração [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) que contém informações detalhadas sobre a comparação.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1c7e-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b1c7e-112">Return Value</span></span>  
 <span data-ttu-id="b1c7e-113">`pfEquivalent`Retorna um valor booliano que indica se os dois assemblies são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="b1c7e-114">`pResult`Retorna um dos `AssemblyComparisonResult` valores para fornecer um motivo mais detalhado para o valor de `pfEquivalent`.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1c7e-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1c7e-115">Remarks</span></span>  
 <span data-ttu-id="b1c7e-116">`CompareAssemblyIdentity`verifica se `pwzAssemblyIdentity1` e `pwzAssemblyIdentity2` são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="b1c7e-117">`pfEquivalent`é definido como `true` sob uma ou mais das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="b1c7e-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="b1c7e-118">As duas identidades de assembly são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="b1c7e-119">Para assemblies com nome forte, a equivalência exige que o nome do assembly, a versão, o token de chave pública e a cultura sejam idênticos.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="b1c7e-120">Para apenas assemblies nomeados, a equivalência requer uma correspondência no nome do assembly e na cultura.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="b1c7e-121">Ambas as identidades do assembly se referem a assemblies que são executados no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="b1c7e-122">Essa condição retorna `true` mesmo que os números de versão do assembly não coincidam.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="b1c7e-123">Os dois assemblies não são assemblies gerenciados, `fUnified1` mas `fUnified2` ou foram definidos `true`como.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="b1c7e-124">O `fUnified` sinalizador indica que todos os números de versão até o número de versão do assembly com nome forte são considerados equivalentes ao assembly com nome forte.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="b1c7e-125">Por exemplo, se o valor de `pwzAssemblyIndentity1` for "MyAssembly, Version = 3.0.0.0, Culture = neutral, PublicKeyToken =...." e o valor de `fUnified1` for `true`, isso indica que todas as versões de MyAssembly da versão 0.0.0.0 para 3.0.0.0 devem ser Tratado como equivalente.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="b1c7e-126">`pwzAssemblyIndentity2` Nesse caso, se se referir ao mesmo assembly como `pwzAssemblyIndentity1`, exceto que ele tem um número de versão inferior, `pfEquivalent` será definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="b1c7e-127">Se `pwzAssemblyIdentity2` se referir a um número de `pfEquivalent` versão superior, `true` será definido como somente se `fUnified2` o `true`valor de for.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="b1c7e-128">O `pResult` parâmetro inclui informações específicas sobre por que os dois assemblies são considerados equivalentes ou não equivalentes.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="b1c7e-129">Para obter mais informações, consulte [Enumeração AssemblyComparisonResult](assemblycomparisonresult-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b1c7e-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c7e-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1c7e-130">Requirements</span></span>  
 <span data-ttu-id="b1c7e-131">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c7e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c7e-132">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b1c7e-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b1c7e-133">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1c7e-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1c7e-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c7e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c7e-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1c7e-135">See also</span></span>

- [<span data-ttu-id="b1c7e-136">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="b1c7e-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="b1c7e-137">Enumeração AssemblyComparisonResult</span><span class="sxs-lookup"><span data-stu-id="b1c7e-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
