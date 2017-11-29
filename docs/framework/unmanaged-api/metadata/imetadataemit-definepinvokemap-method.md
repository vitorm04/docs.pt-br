---
title: "Método IMetaDataEmit::DefinePinvokeMap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefinePinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c15c6039f116597ee4f2c0f83bed4c5550b30a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="f58e8-102">Método IMetaDataEmit::DefinePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="f58e8-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="f58e8-103">Define os recursos da assinatura de PInvoke do método referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="f58e8-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f58e8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f58e8-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f58e8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f58e8-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f58e8-106">[in] O token para o método de destino.</span><span class="sxs-lookup"><span data-stu-id="f58e8-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="f58e8-107">[in] Sinalizadores usados pelo PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="f58e8-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="f58e8-108">[in] O nome do destino de exportação de método em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="f58e8-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="f58e8-109">[in] O token para o destino de DLL nativa.</span><span class="sxs-lookup"><span data-stu-id="f58e8-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f58e8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f58e8-110">Requirements</span></span>  
 <span data-ttu-id="f58e8-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f58e8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f58e8-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f58e8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f58e8-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f58e8-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f58e8-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f58e8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58e8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f58e8-115">See Also</span></span>  
 [<span data-ttu-id="f58e8-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f58e8-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f58e8-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f58e8-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
