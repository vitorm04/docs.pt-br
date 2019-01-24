---
title: Método ICorDebugController::IsRunning
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd54792e37523ea5bf0c2e7a4082ee00c30d00ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496285"
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="b68f5-102">Método ICorDebugController::IsRunning</span><span class="sxs-lookup"><span data-stu-id="b68f5-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="b68f5-103">Obtém um valor que indica se os threads no processo estão atualmente em execução livremente.</span><span class="sxs-lookup"><span data-stu-id="b68f5-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b68f5-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b68f5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b68f5-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="b68f5-106">[out] Um ponteiro para um valor que é `true` se os threads no processo em execução livremente; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b68f5-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b68f5-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b68f5-107">Requirements</span></span>  
 <span data-ttu-id="b68f5-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b68f5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68f5-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b68f5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b68f5-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b68f5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b68f5-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68f5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68f5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b68f5-112">See also</span></span>

