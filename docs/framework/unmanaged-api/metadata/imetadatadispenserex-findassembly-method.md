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
ms.openlocfilehash: 2d974b7368dd01062d2d310d076dce05e102eb81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442282"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="8e8d3-102">Método IMetaDataDispenserEx::FindAssembly</span><span class="sxs-lookup"><span data-stu-id="8e8d3-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="8e8d3-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-103">This method is not implemented.</span></span> <span data-ttu-id="8e8d3-104">If called, it returns E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e8d3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e8d3-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8e8d3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e8d3-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="8e8d3-107">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="8e8d3-108">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="8e8d3-109">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="8e8d3-110">[in] The assembly to be found.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="8e8d3-111">[out] The simple name of the assembly.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8e8d3-112">[in] The size, in bytes, of `szName`.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="8e8d3-113">[out] The number of characters actually returned in `szName`.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e8d3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e8d3-114">Requirements</span></span>  
 <span data-ttu-id="8e8d3-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e8d3-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e8d3-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8e8d3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e8d3-117">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e8d3-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e8d3-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e8d3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e8d3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e8d3-119">See also</span></span>

- [<span data-ttu-id="8e8d3-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="8e8d3-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="8e8d3-121">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="8e8d3-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
