---
title: Método ICorPublishEnum::Clone
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12d9e468027e88cc74900364459f83d7e5125a9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="2ecfb-102">Método ICorPublishEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="2ecfb-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="2ecfb-103">Cria uma cópia deste [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="2ecfb-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ecfb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ecfb-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ecfb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ecfb-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2ecfb-106">[out] Um ponteiro para o endereço de um `ICorPublishEnum` que é uma cópia deste objeto `ICorPublishEnum` objeto.</span><span class="sxs-lookup"><span data-stu-id="2ecfb-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ecfb-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ecfb-107">Requirements</span></span>  
 <span data-ttu-id="2ecfb-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ecfb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ecfb-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2ecfb-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2ecfb-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ecfb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ecfb-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ecfb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ecfb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ecfb-112">See Also</span></span>  
 [<span data-ttu-id="2ecfb-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="2ecfb-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
