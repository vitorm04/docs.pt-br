---
title: "Método IMetaDataEmit::SaveToMemory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SaveToMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 685ed69964970f505ad6f938af361c48664d2279
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="b142b-102">Método IMetaDataEmit::SaveToMemory</span><span class="sxs-lookup"><span data-stu-id="b142b-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="b142b-103">Salva todos os metadados no escopo atual para a área especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="b142b-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b142b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b142b-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b142b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b142b-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="b142b-106">[out] O endereço no qual começar a gravar metadados.</span><span class="sxs-lookup"><span data-stu-id="b142b-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="b142b-107">[in] O tamanho, em bytes, da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="b142b-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b142b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b142b-108">Requirements</span></span>  
 <span data-ttu-id="b142b-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b142b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b142b-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b142b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b142b-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b142b-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b142b-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b142b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b142b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b142b-113">See Also</span></span>  
 [<span data-ttu-id="b142b-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b142b-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b142b-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b142b-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
