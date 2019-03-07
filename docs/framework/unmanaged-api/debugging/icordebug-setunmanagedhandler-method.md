---
title: Método ICorDebug::SetUnmanagedHandler
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49567bc354ddad56311268bef0a367b8896f2ab8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475665"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="e3ae7-102">Método ICorDebug::SetUnmanagedHandler</span><span class="sxs-lookup"><span data-stu-id="e3ae7-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="e3ae7-103">Especifica o objeto de manipulador de eventos para eventos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e3ae7-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ae7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3ae7-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3ae7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3ae7-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="e3ae7-106">[in] Um ponteiro para um [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objeto que representa o manipulador de eventos para eventos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e3ae7-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3ae7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3ae7-107">Remarks</span></span>  
 <span data-ttu-id="e3ae7-108">O manipulador de eventos do objeto para não gerenciado eventos devem ser definidos após uma chamada para [icordebug:: Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) e antes de qualquer chamada para [icordebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) ou [icordebug:: DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="e3ae7-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="e3ae7-109">No entanto, para fins de herdado, você não deve definir o objeto de manipulador de eventos para eventos não gerenciados até que o primeiro evento de depuração nativa seja gerado.</span><span class="sxs-lookup"><span data-stu-id="e3ae7-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="e3ae7-110">Especificamente, se `ICorDebug::CreateProcess` definiu o sinalizador CREATE_SUSPENDED, depuração nativa não podem ser expedidos eventos até que o thread principal seja retomado.</span><span class="sxs-lookup"><span data-stu-id="e3ae7-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3ae7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3ae7-111">Requirements</span></span>  
 <span data-ttu-id="e3ae7-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3ae7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3ae7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3ae7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3ae7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3ae7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3ae7-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ae7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ae7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3ae7-116">See also</span></span>
- [<span data-ttu-id="e3ae7-117">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="e3ae7-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
