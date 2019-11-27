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
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="c06b1-102">Método IMetaDataDispenserEx::FindAssembly</span><span class="sxs-lookup"><span data-stu-id="c06b1-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="c06b1-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="c06b1-103">This method is not implemented.</span></span> <span data-ttu-id="c06b1-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c06b1-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c06b1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c06b1-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c06b1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c06b1-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="c06b1-107">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="c06b1-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="c06b1-108">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="c06b1-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="c06b1-109">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="c06b1-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="c06b1-110">no O assembly a ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="c06b1-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="c06b1-111">fora O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="c06b1-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c06b1-112">no O tamanho, em bytes, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="c06b1-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="c06b1-113">fora O número de caracteres realmente retornados em `szName`.</span><span class="sxs-lookup"><span data-stu-id="c06b1-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c06b1-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c06b1-114">Requirements</span></span>  
 <span data-ttu-id="c06b1-115">**Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c06b1-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c06b1-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c06b1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c06b1-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c06b1-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c06b1-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c06b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c06b1-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c06b1-119">See also</span></span>

- [<span data-ttu-id="c06b1-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="c06b1-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="c06b1-121">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="c06b1-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
