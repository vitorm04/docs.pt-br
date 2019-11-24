---
title: Método IMetaDataDispenserEx::FindAssemblyModule
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
ms.openlocfilehash: e73c95d8c720ed3263d6a66c48bdb5b5582eb686
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442184"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="2a5ee-102">Método IMetaDataDispenserEx::FindAssemblyModule</span><span class="sxs-lookup"><span data-stu-id="2a5ee-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="2a5ee-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-103">This method is not implemented.</span></span> <span data-ttu-id="2a5ee-104">If called, it returns E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a5ee-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a5ee-105">Syntax</span></span>  
  
```cpp  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a5ee-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a5ee-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="2a5ee-107">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="2a5ee-108">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="2a5ee-109">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="2a5ee-110">[in] The name of the module.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="2a5ee-111">[in] The assembly to be found.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="2a5ee-112">[out] The simple name of the assembly.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2a5ee-113">[in] The size, in bytes, of `szName`.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="2a5ee-114">[out] The number of characters actually returned in `szName`.</span><span class="sxs-lookup"><span data-stu-id="2a5ee-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a5ee-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a5ee-115">Requirements</span></span>  
 <span data-ttu-id="2a5ee-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a5ee-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a5ee-117">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2a5ee-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a5ee-118">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a5ee-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a5ee-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a5ee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a5ee-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a5ee-120">See also</span></span>

- [<span data-ttu-id="2a5ee-121">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="2a5ee-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="2a5ee-122">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="2a5ee-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
