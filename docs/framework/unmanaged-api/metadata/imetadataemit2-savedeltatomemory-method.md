---
title: "Método IMetaDataEmit2::SaveDeltaToMemory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f4243840ac64a14b4f4e6c86787fdf238507635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="18207-102">Método IMetaDataEmit2::SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="18207-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="18207-103">Salva as alterações da sessão atual edit-and-continue na memória.</span><span class="sxs-lookup"><span data-stu-id="18207-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18207-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18207-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18207-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18207-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="18207-106">[out] O endereço no qual começar a gravar o delta de metadados.</span><span class="sxs-lookup"><span data-stu-id="18207-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="18207-107">[in] O tamanho das alterações.</span><span class="sxs-lookup"><span data-stu-id="18207-107">[in] The size of the changes.</span></span> <span data-ttu-id="18207-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) para determinar o tamanho.</span><span class="sxs-lookup"><span data-stu-id="18207-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18207-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18207-109">Requirements</span></span>  
 <span data-ttu-id="18207-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18207-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18207-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18207-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18207-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="18207-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18207-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18207-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18207-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18207-114">See Also</span></span>  
 [<span data-ttu-id="18207-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="18207-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="18207-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="18207-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
