---
title: "Método ICorPublishEnum::Clone"
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
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e230c7ed21b802f4e1784b8e8ec5ba6646bd8666
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="c406d-102">Método ICorPublishEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="c406d-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="c406d-103">Cria uma cópia deste [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="c406d-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c406d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c406d-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c406d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c406d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c406d-106">[out] Um ponteiro para o endereço de um `ICorPublishEnum` que é uma cópia deste objeto `ICorPublishEnum` objeto.</span><span class="sxs-lookup"><span data-stu-id="c406d-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c406d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c406d-107">Requirements</span></span>  
 <span data-ttu-id="c406d-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c406d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c406d-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c406d-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c406d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c406d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c406d-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c406d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c406d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c406d-112">See Also</span></span>  
 [<span data-ttu-id="c406d-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="c406d-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
