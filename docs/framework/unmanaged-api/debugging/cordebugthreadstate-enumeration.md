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
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133700"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="535a2-102">Enumeração CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="535a2-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="535a2-103">Especifica o estado de um thread para depuração.</span><span class="sxs-lookup"><span data-stu-id="535a2-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="535a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="535a2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="535a2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="535a2-105">Members</span></span>  
  
|<span data-ttu-id="535a2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="535a2-106">Member</span></span>|<span data-ttu-id="535a2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="535a2-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="535a2-108">O thread é executado livremente, a menos que ocorra um evento de depuração.</span><span class="sxs-lookup"><span data-stu-id="535a2-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="535a2-109">Não é possível executar o thread.</span><span class="sxs-lookup"><span data-stu-id="535a2-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="535a2-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="535a2-110">Remarks</span></span>  
 <span data-ttu-id="535a2-111">O depurador usa a enumeração `CorDebugThreadState` para controlar a execução de um thread.</span><span class="sxs-lookup"><span data-stu-id="535a2-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="535a2-112">O estado de um thread pode ser definido usando o método [ICorDebugThread:: SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) ou [ICorDebugController:: SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="535a2-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="535a2-113">Um retorno de chamada fornecido à [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md) permite bombeamento de mensagens, portanto, um estado interrompido não é necessário.</span><span class="sxs-lookup"><span data-stu-id="535a2-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="535a2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="535a2-114">Requirements</span></span>  
 <span data-ttu-id="535a2-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="535a2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="535a2-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="535a2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="535a2-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="535a2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="535a2-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="535a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535a2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="535a2-119">See also</span></span>

- [<span data-ttu-id="535a2-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="535a2-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
