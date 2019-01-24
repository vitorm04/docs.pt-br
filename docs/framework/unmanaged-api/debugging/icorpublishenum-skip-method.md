---
title: Método ICorPublishEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e7d4e449624f295c4011a4ccdad46226e742a8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681151"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="70bf4-102">Método ICorPublishEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="70bf4-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="70bf4-103">Move o cursor para frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="70bf4-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70bf4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70bf4-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70bf4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70bf4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="70bf4-106">[in] O número de itens por qual mover o cursor para frente.</span><span class="sxs-lookup"><span data-stu-id="70bf4-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70bf4-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70bf4-107">Requirements</span></span>  
 <span data-ttu-id="70bf4-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70bf4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70bf4-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="70bf4-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="70bf4-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70bf4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70bf4-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70bf4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bf4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70bf4-112">See also</span></span>
- [<span data-ttu-id="70bf4-113">Interface ICorPublishEnum</span><span class="sxs-lookup"><span data-stu-id="70bf4-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
