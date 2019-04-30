---
title: Método ICorDebugThread2::InterceptCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b883a5c6dd0cff119ff09747d32c607ac7ec60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968292"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="d07b2-102">Método ICorDebugThread2::InterceptCurrentException</span><span class="sxs-lookup"><span data-stu-id="d07b2-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="d07b2-103">Permite que um depurador interceptar a exceção atual nesse thread.</span><span class="sxs-lookup"><span data-stu-id="d07b2-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d07b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d07b2-104">Syntax</span></span>  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d07b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d07b2-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="d07b2-106">[in] Um ponteiro para um ICorDebugFrame que representa o quadro de pilhas ativas.</span><span class="sxs-lookup"><span data-stu-id="d07b2-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d07b2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d07b2-107">Remarks</span></span>  
 <span data-ttu-id="d07b2-108">O `InterceptCurrentException` método pode ser chamado entre um retorno de chamada de exceção ([icordebugmanagedcallback:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) e a chamada associada para [Icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="d07b2-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d07b2-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d07b2-109">Requirements</span></span>  
 <span data-ttu-id="d07b2-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d07b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d07b2-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d07b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d07b2-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d07b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d07b2-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d07b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
