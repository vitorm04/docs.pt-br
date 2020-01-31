---
title: Enumeração CorDebugUserState
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: c142b9656af2031b10de239645da76835c435655
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789233"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="d8e21-102">Enumeração CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="d8e21-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="d8e21-103">Indica o estado do usuário de um thread.</span><span class="sxs-lookup"><span data-stu-id="d8e21-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8e21-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="d8e21-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d8e21-105">Members</span></span>  
  
|<span data-ttu-id="d8e21-106">Value</span><span class="sxs-lookup"><span data-stu-id="d8e21-106">Value</span></span>|<span data-ttu-id="d8e21-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8e21-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="d8e21-108">Foi solicitada uma terminação do thread.</span><span class="sxs-lookup"><span data-stu-id="d8e21-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="d8e21-109">Uma suspensão do thread foi solicitada.</span><span class="sxs-lookup"><span data-stu-id="d8e21-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="d8e21-110">O thread está sendo executado em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d8e21-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="d8e21-111">O thread não iniciou a execução.</span><span class="sxs-lookup"><span data-stu-id="d8e21-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="d8e21-112">O thread foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="d8e21-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="d8e21-113">O thread está aguardando outro thread concluir uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="d8e21-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="d8e21-114">O thread foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="d8e21-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="d8e21-115">O thread está em um ponto não seguro.</span><span class="sxs-lookup"><span data-stu-id="d8e21-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="d8e21-116">Ou seja, o thread está em um ponto na execução em que ele pode bloquear a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d8e21-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="d8e21-117">Eventos de depuração podem ser expedidos de pontos não seguros, mas suspender um thread em um ponto não seguro provavelmente causará um deadlock até que o thread seja retomado.</span><span class="sxs-lookup"><span data-stu-id="d8e21-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="d8e21-118">Os pontos seguros e inseguros são determinados pela implementação JIT (just-in-time) e pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d8e21-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="d8e21-119">O thread é do pool de threads.</span><span class="sxs-lookup"><span data-stu-id="d8e21-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8e21-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8e21-120">Remarks</span></span>  
 <span data-ttu-id="d8e21-121">O estado do usuário de um thread é o estado que o thread tem quando o depurador o examina.</span><span class="sxs-lookup"><span data-stu-id="d8e21-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="d8e21-122">Um thread pode ter uma combinação de Estados do usuário.</span><span class="sxs-lookup"><span data-stu-id="d8e21-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="d8e21-123">Use o método [ICorDebugThread:: GetUserState](icordebugthread-getuserstate-method.md) para recuperar o estado do usuário de um thread.</span><span class="sxs-lookup"><span data-stu-id="d8e21-123">Use the [ICorDebugThread::GetUserState](icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8e21-124">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d8e21-124">Requirements</span></span>  
 <span data-ttu-id="d8e21-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8e21-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8e21-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8e21-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8e21-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8e21-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8e21-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8e21-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e21-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="d8e21-129">See also</span></span>

- [<span data-ttu-id="d8e21-130">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="d8e21-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
