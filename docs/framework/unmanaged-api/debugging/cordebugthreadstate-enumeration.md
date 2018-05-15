---
title: Enumeração CorDebugThreadState
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba8bca6d14308284c869b923853f7e27e045bca5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="b6165-102">Enumeração CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="b6165-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="b6165-103">Especifica o estado de um thread para depuração.</span><span class="sxs-lookup"><span data-stu-id="b6165-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6165-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6165-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="b6165-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b6165-105">Members</span></span>  
  
|<span data-ttu-id="b6165-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b6165-106">Member</span></span>|<span data-ttu-id="b6165-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6165-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="b6165-108">O thread é executado livremente, a menos que ocorra um evento de depuração.</span><span class="sxs-lookup"><span data-stu-id="b6165-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="b6165-109">Não é possível executar o thread.</span><span class="sxs-lookup"><span data-stu-id="b6165-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6165-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6165-110">Remarks</span></span>  
 <span data-ttu-id="b6165-111">O depurador usa o `CorDebugThreadState` enumeração para controlar a execução do thread.</span><span class="sxs-lookup"><span data-stu-id="b6165-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="b6165-112">O estado de um thread pode ser definido usando o [: Setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) ou [: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b6165-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="b6165-113">Um retorno de chamada fornecido para o [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md) permite bombeamento de mensagens, dispensando a um estado interrompido.</span><span class="sxs-lookup"><span data-stu-id="b6165-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6165-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6165-114">Requirements</span></span>  
 <span data-ttu-id="b6165-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6165-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6165-116">**Cabeçalho:** CorDebug.idl, CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="b6165-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="b6165-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6165-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6165-118">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6165-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6165-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6165-119">See Also</span></span>  
 [<span data-ttu-id="b6165-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="b6165-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
