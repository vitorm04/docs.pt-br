---
title: Método IMetaDataDispenserEx::FindAssembly
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85ebddf4ef96be2a583e54082e4d4405b30adf46
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777774"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="97e9c-102">Método IMetaDataDispenserEx::FindAssembly</span><span class="sxs-lookup"><span data-stu-id="97e9c-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="97e9c-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="97e9c-103">This method is not implemented.</span></span> <span data-ttu-id="97e9c-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="97e9c-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e9c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97e9c-105">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97e9c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="97e9c-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="97e9c-107">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="97e9c-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="97e9c-108">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="97e9c-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="97e9c-109">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="97e9c-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="97e9c-110">[in] O assembly a ser localizada.</span><span class="sxs-lookup"><span data-stu-id="97e9c-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="97e9c-111">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="97e9c-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="97e9c-112">[in] O tamanho, em bytes, do `szName`.</span><span class="sxs-lookup"><span data-stu-id="97e9c-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="97e9c-113">[out] O número de caracteres retornado de fato no `szName`.</span><span class="sxs-lookup"><span data-stu-id="97e9c-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e9c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97e9c-114">Requirements</span></span>  
 <span data-ttu-id="97e9c-115">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97e9c-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e9c-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="97e9c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97e9c-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="97e9c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97e9c-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97e9c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e9c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97e9c-119">See also</span></span>

- [<span data-ttu-id="97e9c-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="97e9c-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="97e9c-121">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="97e9c-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
