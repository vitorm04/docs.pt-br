---
title: "Método ICorDebugThread2::InterceptCurrentException"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9aaf02ed27ba87f39e5168854254191388d17019
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="b422b-102">Método ICorDebugThread2::InterceptCurrentException</span><span class="sxs-lookup"><span data-stu-id="b422b-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="b422b-103">Permite que um depurador interceptar a exceção atual neste thread.</span><span class="sxs-lookup"><span data-stu-id="b422b-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b422b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b422b-104">Syntax</span></span>  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b422b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b422b-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="b422b-106">[in] Um ponteiro para um ICorDebugFrame que representa o quadro de pilha ativa.</span><span class="sxs-lookup"><span data-stu-id="b422b-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b422b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b422b-107">Remarks</span></span>  
 <span data-ttu-id="b422b-108">O `InterceptCurrentException` método pode ser chamado entre um retorno de chamada de exceção ([Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) ou [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) e a chamada associada a [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="b422b-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b422b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b422b-109">Requirements</span></span>  
 <span data-ttu-id="b422b-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b422b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b422b-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b422b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b422b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b422b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b422b-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b422b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
