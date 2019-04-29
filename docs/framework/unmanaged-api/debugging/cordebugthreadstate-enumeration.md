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
ms.openlocfilehash: efb7f5b8e63742471123a0e0a38cebe605f3696f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61724038"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="485b9-102">Enumeração CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="485b9-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="485b9-103">Especifica o estado de um thread para depuração.</span><span class="sxs-lookup"><span data-stu-id="485b9-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="485b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="485b9-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="485b9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="485b9-105">Members</span></span>  
  
|<span data-ttu-id="485b9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="485b9-106">Member</span></span>|<span data-ttu-id="485b9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="485b9-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="485b9-108">O thread executa livremente, a menos que ocorra um evento de depuração.</span><span class="sxs-lookup"><span data-stu-id="485b9-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="485b9-109">O thread não pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="485b9-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="485b9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="485b9-110">Remarks</span></span>  
 <span data-ttu-id="485b9-111">O depurador usa o `CorDebugThreadState` enumeração para controlar a execução do thread.</span><span class="sxs-lookup"><span data-stu-id="485b9-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="485b9-112">O estado de um thread pode ser definido usando o [icordebugthread:: Setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) ou [icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="485b9-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="485b9-113">Um retorno de chamada fornecido para o [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md) habilita o bombeamento de mensagens, portanto, não é necessário um estado interrompido.</span><span class="sxs-lookup"><span data-stu-id="485b9-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="485b9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="485b9-114">Requirements</span></span>  
 <span data-ttu-id="485b9-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="485b9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="485b9-116">**Cabeçalho:** CorDebug.idl, CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="485b9-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="485b9-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="485b9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="485b9-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="485b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485b9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="485b9-119">See also</span></span>

- [<span data-ttu-id="485b9-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="485b9-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
