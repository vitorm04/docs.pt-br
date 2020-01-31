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
ms.openlocfilehash: 69a8aabd1d79bb9bb4248259c99124ce50677600
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789238"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="d269d-102">Enumeração CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="d269d-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="d269d-103">Especifica o estado de um thread para depuração.</span><span class="sxs-lookup"><span data-stu-id="d269d-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d269d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d269d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="d269d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d269d-105">Members</span></span>  
  
|<span data-ttu-id="d269d-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d269d-106">Member</span></span>|<span data-ttu-id="d269d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d269d-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="d269d-108">O thread é executado livremente, a menos que ocorra um evento de depuração.</span><span class="sxs-lookup"><span data-stu-id="d269d-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="d269d-109">Não é possível executar o thread.</span><span class="sxs-lookup"><span data-stu-id="d269d-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d269d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d269d-110">Remarks</span></span>  
 <span data-ttu-id="d269d-111">O depurador usa a enumeração `CorDebugThreadState` para controlar a execução de um thread.</span><span class="sxs-lookup"><span data-stu-id="d269d-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="d269d-112">O estado de um thread pode ser definido usando o método [ICorDebugThread:: SetDebugState](icordebugthread-setdebugstate-method.md) ou [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d269d-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="d269d-113">Um retorno de chamada fornecido à [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md) permite bombeamento de mensagens, portanto, um estado interrompido não é necessário.</span><span class="sxs-lookup"><span data-stu-id="d269d-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d269d-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d269d-114">Requirements</span></span>  
 <span data-ttu-id="d269d-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d269d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d269d-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d269d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d269d-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d269d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d269d-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d269d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d269d-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="d269d-119">See also</span></span>

- [<span data-ttu-id="d269d-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="d269d-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
