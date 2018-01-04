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
ms.workload: dotnet
ms.openlocfilehash: bd42c54990fd8aad1b9e6325d59ac7ccc5d6a3fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="cb566-102">Método IMetaDataEmit::DefinePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="cb566-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="cb566-103">Define os recursos da assinatura de PInvoke do método referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="cb566-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb566-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb566-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb566-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb566-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="cb566-106">[in] O token para o método de destino.</span><span class="sxs-lookup"><span data-stu-id="cb566-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="cb566-107">[in] Sinalizadores usados pelo PInvoke para fazer o mapeamento.</span><span class="sxs-lookup"><span data-stu-id="cb566-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="cb566-108">[in] O nome do destino de exportação de método em uma DLL não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="cb566-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="cb566-109">[in] O token para o destino de DLL nativa.</span><span class="sxs-lookup"><span data-stu-id="cb566-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb566-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb566-110">Requirements</span></span>  
 <span data-ttu-id="cb566-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb566-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb566-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb566-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb566-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cb566-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb566-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb566-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb566-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb566-115">See Also</span></span>  
 [<span data-ttu-id="cb566-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="cb566-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="cb566-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="cb566-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
