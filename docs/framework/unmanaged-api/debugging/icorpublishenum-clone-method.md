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
ms.openlocfilehash: fdc8c274cd6949977b3e0ad5df8e1e14692ad167
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563581"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="d3d2a-102">Método ICorPublishEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="d3d2a-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="d3d2a-103">Cria uma cópia deste [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="d3d2a-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d2a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3d2a-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3d2a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d3d2a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d3d2a-106">[out] Um ponteiro para o endereço de um `ICorPublishEnum` que é uma cópia deste objeto `ICorPublishEnum` objeto.</span><span class="sxs-lookup"><span data-stu-id="d3d2a-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3d2a-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3d2a-107">Requirements</span></span>  
 <span data-ttu-id="d3d2a-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d2a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d2a-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d3d2a-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d3d2a-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3d2a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3d2a-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d2a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d2a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3d2a-112">See also</span></span>
- [<span data-ttu-id="d3d2a-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="d3d2a-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
