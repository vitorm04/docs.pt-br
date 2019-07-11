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
ms.openlocfilehash: d672cf2375a5354c48608b3e4156867ba406992a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765022"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="f924d-102">Método ICorPublishEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="f924d-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="f924d-103">Cria uma cópia deste [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="f924d-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f924d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f924d-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f924d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f924d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="f924d-106">[out] Um ponteiro para o endereço de um `ICorPublishEnum` que é uma cópia deste objeto `ICorPublishEnum` objeto.</span><span class="sxs-lookup"><span data-stu-id="f924d-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f924d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f924d-107">Requirements</span></span>  
 <span data-ttu-id="f924d-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f924d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f924d-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f924d-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f924d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f924d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f924d-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f924d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f924d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f924d-112">See also</span></span>

- [<span data-ttu-id="f924d-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="f924d-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
