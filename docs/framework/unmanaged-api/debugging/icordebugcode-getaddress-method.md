---
title: Método ICorDebugCode::GetAddress
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dda5883d8a1de11fa282e8b8e0fafe924f2d8b7a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494500"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="8a0d2-102">Método ICorDebugCode::GetAddress</span><span class="sxs-lookup"><span data-stu-id="8a0d2-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="8a0d2-103">Obtém o endereço virtual relativo (RVA) ou o segmento de código que representa essa interface "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="8a0d2-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a0d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a0d2-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a0d2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a0d2-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="8a0d2-106">[out] Um ponteiro para o RVA do segmento de código.</span><span class="sxs-lookup"><span data-stu-id="8a0d2-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a0d2-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a0d2-107">Requirements</span></span>  
 <span data-ttu-id="8a0d2-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a0d2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a0d2-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a0d2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a0d2-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a0d2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a0d2-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a0d2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a0d2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a0d2-112">See also</span></span>

