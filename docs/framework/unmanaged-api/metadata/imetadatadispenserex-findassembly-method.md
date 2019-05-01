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
ms.openlocfilehash: d204ec29304fe0c4596950cd17c48d0c1d2ac616
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050149"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="c8f98-102">Método IMetaDataDispenserEx::FindAssembly</span><span class="sxs-lookup"><span data-stu-id="c8f98-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="c8f98-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="c8f98-103">This method is not implemented.</span></span> <span data-ttu-id="c8f98-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c8f98-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f98-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8f98-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c8f98-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8f98-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="c8f98-107">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="c8f98-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="c8f98-108">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="c8f98-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="c8f98-109">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="c8f98-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="c8f98-110">[in] O assembly a ser localizada.</span><span class="sxs-lookup"><span data-stu-id="c8f98-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="c8f98-111">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="c8f98-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c8f98-112">[in] O tamanho, em bytes, do `szName`.</span><span class="sxs-lookup"><span data-stu-id="c8f98-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="c8f98-113">[out] O número de caracteres retornado de fato no `szName`.</span><span class="sxs-lookup"><span data-stu-id="c8f98-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f98-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8f98-114">Requirements</span></span>  
 <span data-ttu-id="c8f98-115">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8f98-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f98-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c8f98-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8f98-117">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c8f98-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8f98-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8f98-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f98-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8f98-119">See also</span></span>

- [<span data-ttu-id="c8f98-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="c8f98-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="c8f98-121">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="c8f98-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
