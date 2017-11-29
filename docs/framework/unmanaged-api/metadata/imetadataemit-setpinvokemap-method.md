---
title: "Método IMetaDataEmit::SetPinvokeMap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a10482b12f9a34b0f247779f22c7cc70f871324a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="a2781-102">Método IMetaDataEmit::SetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="a2781-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="a2781-103">Define ou altera os recursos de assinatura de PInvoke do método, conforme definido por uma chamada anterior ao [Definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="a2781-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2781-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2781-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2781-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2781-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a2781-106">[in] O `mdToken` para mapeamento de quais informações se aplicam.</span><span class="sxs-lookup"><span data-stu-id="a2781-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="a2781-107">[in] Sinalizadores usados pelo PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="a2781-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="a2781-108">Esse é um bitmask de `CorPinvokeMap` valores.</span><span class="sxs-lookup"><span data-stu-id="a2781-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="a2781-109">[in] O nome do destino de exportação na DLL nativa.</span><span class="sxs-lookup"><span data-stu-id="a2781-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="a2781-110">[in] O `mdModuleRef` token para o destino não gerenciado DLL.</span><span class="sxs-lookup"><span data-stu-id="a2781-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2781-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2781-111">Requirements</span></span>  
 <span data-ttu-id="a2781-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2781-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2781-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2781-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2781-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a2781-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2781-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2781-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2781-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2781-116">See Also</span></span>  
 [<span data-ttu-id="a2781-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a2781-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a2781-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a2781-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
