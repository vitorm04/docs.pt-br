---
title: "Método IMetaDataDispenserEx::FindAssemblyModule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssemblyModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 482bc9b9a89d876e7ac09fcb4edcd190adc168f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="b41fc-102">Método IMetaDataDispenserEx::FindAssemblyModule</span><span class="sxs-lookup"><span data-stu-id="b41fc-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="b41fc-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="b41fc-103">This method is not implemented.</span></span> <span data-ttu-id="b41fc-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="b41fc-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b41fc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b41fc-105">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="b41fc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b41fc-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="b41fc-107">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="b41fc-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="b41fc-108">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="b41fc-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="b41fc-109">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="b41fc-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="b41fc-110">[in] O nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="b41fc-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="b41fc-111">[in] O assembly a ser localizado.</span><span class="sxs-lookup"><span data-stu-id="b41fc-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="b41fc-112">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="b41fc-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b41fc-113">[in] O tamanho, em bytes, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="b41fc-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="b41fc-114">[out] O número de caracteres de fato retornadas em `szName`.</span><span class="sxs-lookup"><span data-stu-id="b41fc-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b41fc-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b41fc-115">Requirements</span></span>  
 <span data-ttu-id="b41fc-116">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b41fc-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b41fc-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b41fc-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b41fc-118">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b41fc-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b41fc-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b41fc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41fc-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b41fc-120">See Also</span></span>  
 [<span data-ttu-id="b41fc-121">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="b41fc-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="b41fc-122">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="b41fc-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
