---
title: Método IMetaDataEmit::SetPinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 0d34c7a2992a2779b96ec87f1a0175d8fcbce34a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007787"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="7251d-102">Método IMetaDataEmit::SetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="7251d-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="7251d-103">Define ou altera recursos da assinatura do PInvoke de um método, conforme definido por uma chamada anterior para [IMetaDataEmit::D efinepinvokemap](imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="7251d-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7251d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7251d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7251d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7251d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7251d-106">no O `mdToken` ao qual as informações de mapeamento se aplicam.</span><span class="sxs-lookup"><span data-stu-id="7251d-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="7251d-107">no Sinalizadores usados pelo PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="7251d-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="7251d-108">Esta é uma bitmask de `CorPinvokeMap` valores.</span><span class="sxs-lookup"><span data-stu-id="7251d-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="7251d-109">no O nome da exportação de destino na DLL nativa.</span><span class="sxs-lookup"><span data-stu-id="7251d-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="7251d-110">no O `mdModuleRef` token para a dll não gerenciada de destino.</span><span class="sxs-lookup"><span data-stu-id="7251d-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7251d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7251d-111">Requirements</span></span>  
 <span data-ttu-id="7251d-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7251d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7251d-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7251d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7251d-114">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7251d-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7251d-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7251d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7251d-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="7251d-116">See also</span></span>

- [<span data-ttu-id="7251d-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7251d-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7251d-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7251d-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
