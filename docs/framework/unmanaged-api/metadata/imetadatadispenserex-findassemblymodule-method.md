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
ms.openlocfilehash: 64f1e2a8f05616c7ca84bc130428629b1176e985
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006175"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="ada9f-102">Método IMetaDataDispenserEx::FindAssemblyModule</span><span class="sxs-lookup"><span data-stu-id="ada9f-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="ada9f-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="ada9f-103">This method is not implemented.</span></span> <span data-ttu-id="ada9f-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ada9f-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada9f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ada9f-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ada9f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ada9f-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="ada9f-107">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="ada9f-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="ada9f-108">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="ada9f-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="ada9f-109">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="ada9f-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="ada9f-110">no O nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="ada9f-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="ada9f-111">no O assembly a ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="ada9f-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="ada9f-112">fora O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="ada9f-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ada9f-113">no O tamanho, em bytes, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="ada9f-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="ada9f-114">fora O número de caracteres realmente retornados em `szName` .</span><span class="sxs-lookup"><span data-stu-id="ada9f-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada9f-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ada9f-115">Requirements</span></span>  
 <span data-ttu-id="ada9f-116">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada9f-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada9f-117">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ada9f-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ada9f-118">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ada9f-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ada9f-119">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada9f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada9f-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="ada9f-120">See also</span></span>

- [<span data-ttu-id="ada9f-121">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="ada9f-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="ada9f-122">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="ada9f-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
