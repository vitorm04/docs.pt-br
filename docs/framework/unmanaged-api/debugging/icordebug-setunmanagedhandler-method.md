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
ms.openlocfilehash: 36d314211d95dff6648753f5d550a2cfd402a918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134040"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="262aa-102">Método ICorDebug::SetUnmanagedHandler</span><span class="sxs-lookup"><span data-stu-id="262aa-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="262aa-103">Especifica o objeto do manipulador de eventos para eventos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="262aa-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="262aa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="262aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="262aa-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="262aa-106">no Um ponteiro para um objeto [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) que representa o manipulador de eventos para eventos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="262aa-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="262aa-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="262aa-107">Remarks</span></span>  
 <span data-ttu-id="262aa-108">O objeto manipulador de eventos para eventos não gerenciados deve ser definido após uma chamada para [ICorDebug:: Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) e antes de qualquer chamada para [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) ou [ICorDebug::D ebugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="262aa-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="262aa-109">No entanto, para fins herdados, não é necessário definir o objeto manipulador de eventos para eventos não gerenciados até que o primeiro evento de depuração nativa seja gerado.</span><span class="sxs-lookup"><span data-stu-id="262aa-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="262aa-110">Especificamente, se `ICorDebug::CreateProcess` tiver definido o sinalizador CREATE_SUSPENDED, os eventos de depuração nativos não poderão ser expedidos até que o thread principal seja retomado.</span><span class="sxs-lookup"><span data-stu-id="262aa-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="262aa-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="262aa-111">Requirements</span></span>  
 <span data-ttu-id="262aa-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="262aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="262aa-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="262aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="262aa-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="262aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="262aa-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="262aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262aa-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="262aa-116">See also</span></span>

- [<span data-ttu-id="262aa-117">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="262aa-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
