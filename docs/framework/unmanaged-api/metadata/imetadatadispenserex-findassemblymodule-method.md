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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d1d97e443be884f45187a2811ddfce106249515
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183125"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="de225-102">Método IMetaDataDispenserEx::FindAssemblyModule</span><span class="sxs-lookup"><span data-stu-id="de225-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="de225-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="de225-103">This method is not implemented.</span></span> <span data-ttu-id="de225-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="de225-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de225-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de225-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="de225-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de225-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="de225-107">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="de225-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="de225-108">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="de225-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="de225-109">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="de225-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="de225-110">[in] O nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="de225-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="de225-111">[in] O assembly a ser localizada.</span><span class="sxs-lookup"><span data-stu-id="de225-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="de225-112">[out] O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="de225-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="de225-113">[in] O tamanho, em bytes, do `szName`.</span><span class="sxs-lookup"><span data-stu-id="de225-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="de225-114">[out] O número de caracteres retornado de fato no `szName`.</span><span class="sxs-lookup"><span data-stu-id="de225-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de225-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de225-115">Requirements</span></span>  
 <span data-ttu-id="de225-116">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de225-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de225-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de225-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de225-118">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="de225-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="de225-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="de225-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="de225-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de225-120">See also</span></span>

- [<span data-ttu-id="de225-121">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="de225-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="de225-122">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="de225-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
