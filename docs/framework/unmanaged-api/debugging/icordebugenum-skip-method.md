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
ms.openlocfilehash: 1e2d7a344cabb1ab816e4fe696ebb47276397ec3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095029"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="6eb40-102">Método ICorDebugEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="6eb40-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="6eb40-103">Move o cursor para frente na enumeração pelo número especificado de itens.</span><span class="sxs-lookup"><span data-stu-id="6eb40-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb40-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6eb40-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eb40-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6eb40-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6eb40-106">[in] O número de itens por qual mover o cursor para frente.</span><span class="sxs-lookup"><span data-stu-id="6eb40-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb40-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6eb40-107">Requirements</span></span>  
 <span data-ttu-id="6eb40-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eb40-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb40-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6eb40-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6eb40-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6eb40-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6eb40-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6eb40-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6eb40-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6eb40-112">See also</span></span>

- [<span data-ttu-id="6eb40-113">Interface ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="6eb40-113">ICorDebugEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
