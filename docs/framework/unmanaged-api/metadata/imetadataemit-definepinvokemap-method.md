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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f1d62c55df410d284fe050b805cf465718ab112
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576142"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="7bb6f-102">Método IMetaDataEmit::DefinePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="7bb6f-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="7bb6f-103">Define os recursos da assinatura do método referenciada pelo token especificado PInvoke.</span><span class="sxs-lookup"><span data-stu-id="7bb6f-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb6f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bb6f-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bb6f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bb6f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7bb6f-106">[in] O token para o método de destino.</span><span class="sxs-lookup"><span data-stu-id="7bb6f-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="7bb6f-107">[in] Sinalizadores usados por PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="7bb6f-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="7bb6f-108">[in] O nome do destino de exportação de método em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="7bb6f-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="7bb6f-109">[in] O token para o destino de DLL nativa.</span><span class="sxs-lookup"><span data-stu-id="7bb6f-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb6f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bb6f-110">Requirements</span></span>  
 <span data-ttu-id="7bb6f-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb6f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb6f-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7bb6f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bb6f-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7bb6f-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb6f-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb6f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb6f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bb6f-115">See also</span></span>
- [<span data-ttu-id="7bb6f-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7bb6f-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7bb6f-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7bb6f-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
