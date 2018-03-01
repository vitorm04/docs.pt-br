---
title: "Método IMetaDataEmit::SetMethodImplFlags"
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
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8026ec666e853b5a0ccd98e5ba75a3e04ffea9a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="f249f-102">Método IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="f249f-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="f249f-103">Define ou atualiza a assinatura de metadados da implementação do método herdado que é referenciada por token especificado.</span><span class="sxs-lookup"><span data-stu-id="f249f-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f249f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f249f-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f249f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f249f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f249f-106">[in] O token para o método a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="f249f-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="f249f-107">[in] Uma combinação dos valores da [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração que especifica os recursos de implementação de método.</span><span class="sxs-lookup"><span data-stu-id="f249f-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f249f-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f249f-108">Requirements</span></span>  
 <span data-ttu-id="f249f-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f249f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f249f-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f249f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f249f-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f249f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f249f-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f249f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f249f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f249f-113">See Also</span></span>  
 [<span data-ttu-id="f249f-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f249f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f249f-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f249f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
