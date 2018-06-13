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
ms.openlocfilehash: 0b4caf27fe45ce0a85b7e1800827a1e5cd0893ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445232"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="33ffe-102">Método IMetaDataDispenserEx::FindAssembly</span><span class="sxs-lookup"><span data-stu-id="33ffe-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="33ffe-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="33ffe-103">This method is not implemented.</span></span> <span data-ttu-id="33ffe-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="33ffe-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ffe-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33ffe-105">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="33ffe-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="33ffe-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="33ffe-107">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="33ffe-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="33ffe-108">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="33ffe-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="33ffe-109">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="33ffe-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="33ffe-110">[in] O assembly a ser localizado.</span><span class="sxs-lookup"><span data-stu-id="33ffe-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="33ffe-111">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="33ffe-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="33ffe-112">[in] O tamanho, em bytes, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="33ffe-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="33ffe-113">[out] O número de caracteres de fato retornadas em `szName`.</span><span class="sxs-lookup"><span data-stu-id="33ffe-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33ffe-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33ffe-114">Requirements</span></span>  
 <span data-ttu-id="33ffe-115">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33ffe-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ffe-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="33ffe-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33ffe-117">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="33ffe-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33ffe-118">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33ffe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ffe-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33ffe-119">See Also</span></span>  
 [<span data-ttu-id="33ffe-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="33ffe-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="33ffe-121">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="33ffe-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
