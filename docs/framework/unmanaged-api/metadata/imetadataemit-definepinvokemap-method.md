---
title: Método IMetaDataEmit::DefinePinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: e414bc5a7d537e8d153541f05b22dd91578e8739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177747"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="70a04-102">Método IMetaDataEmit::DefinePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="70a04-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="70a04-103">Define os recursos da assinatura PInvoke do método referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="70a04-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70a04-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70a04-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="70a04-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="70a04-106">[em] O símbolo do método de destino.</span><span class="sxs-lookup"><span data-stu-id="70a04-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="70a04-107">[em] Sinalizadores usados pelo PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="70a04-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="70a04-108">[em] O nome do método de exportação de destino em um DLL não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="70a04-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="70a04-109">[em] O token para o DLL nativo alvo.</span><span class="sxs-lookup"><span data-stu-id="70a04-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70a04-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70a04-110">Requirements</span></span>  
 <span data-ttu-id="70a04-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70a04-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70a04-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70a04-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70a04-113">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70a04-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70a04-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70a04-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a04-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="70a04-115">See also</span></span>

- [<span data-ttu-id="70a04-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="70a04-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="70a04-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="70a04-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
