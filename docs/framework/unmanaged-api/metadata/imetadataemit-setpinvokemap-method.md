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
ms.openlocfilehash: 4c68754bc44fe035fd8e7143c52895928beae395
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175584"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="77c65-102">Método IMetaDataEmit::SetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="77c65-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="77c65-103">Define ou altera recursos da assinatura PInvoke de um método, conforme definido por uma chamada anterior ao [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="77c65-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77c65-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77c65-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77c65-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="77c65-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="77c65-106">[em] A `mdToken` informação de mapeamento a que se aplica.</span><span class="sxs-lookup"><span data-stu-id="77c65-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="77c65-107">[em] Sinalizadores usados pelo PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="77c65-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="77c65-108">Isto é uma `CorPinvokeMap` pequena máscara de valores.</span><span class="sxs-lookup"><span data-stu-id="77c65-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="77c65-109">[em] O nome da exportação alvo na DLL nativa.</span><span class="sxs-lookup"><span data-stu-id="77c65-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="77c65-110">[em] O `mdModuleRef` token para o dll alvo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="77c65-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77c65-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77c65-111">Requirements</span></span>  
 <span data-ttu-id="77c65-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77c65-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77c65-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="77c65-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77c65-114">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77c65-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77c65-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77c65-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c65-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="77c65-116">See also</span></span>

- [<span data-ttu-id="77c65-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="77c65-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="77c65-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="77c65-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
