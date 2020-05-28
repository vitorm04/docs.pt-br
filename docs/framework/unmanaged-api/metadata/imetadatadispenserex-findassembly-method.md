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
ms.openlocfilehash: 50aebb09924b93a622e5b7d84e65e41ee91f6018
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006188"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="c06c4-102">Método IMetaDataDispenserEx::FindAssembly</span><span class="sxs-lookup"><span data-stu-id="c06c4-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="c06c4-103">Este método não está implementado.</span><span class="sxs-lookup"><span data-stu-id="c06c4-103">This method is not implemented.</span></span> <span data-ttu-id="c06c4-104">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c06c4-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c06c4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c06c4-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c06c4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c06c4-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="c06c4-107">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="c06c4-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="c06c4-108">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="c06c4-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="c06c4-109">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="c06c4-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="c06c4-110">no O assembly a ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="c06c4-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="c06c4-111">fora O nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="c06c4-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c06c4-112">no O tamanho, em bytes, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="c06c4-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="c06c4-113">fora O número de caracteres realmente retornados em `szName` .</span><span class="sxs-lookup"><span data-stu-id="c06c4-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c06c4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c06c4-114">Requirements</span></span>  
 <span data-ttu-id="c06c4-115">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c06c4-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c06c4-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c06c4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c06c4-117">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c06c4-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c06c4-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c06c4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c06c4-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="c06c4-119">See also</span></span>

- [<span data-ttu-id="c06c4-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="c06c4-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="c06c4-121">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="c06c4-121">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
