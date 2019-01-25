---
title: Método ICorDebugEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a886d8ab8f2d59bb9c9b0b3ff00fd89f7c931ff8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692815"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="e51bf-102">Método ICorDebugEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="e51bf-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="e51bf-103">Move o cursor para frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="e51bf-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e51bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e51bf-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e51bf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e51bf-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e51bf-106">[in] O número de itens por qual mover o cursor para frente.</span><span class="sxs-lookup"><span data-stu-id="e51bf-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e51bf-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e51bf-107">Requirements</span></span>  
 <span data-ttu-id="e51bf-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e51bf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e51bf-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e51bf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e51bf-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e51bf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e51bf-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e51bf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51bf-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e51bf-112">See also</span></span>
- [<span data-ttu-id="e51bf-113">Interface1 ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="e51bf-113">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
