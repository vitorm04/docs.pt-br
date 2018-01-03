---
title: "Enumeração CorDebugUserState"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUserState
helpviewer_keywords: CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57fd9df27b1911c90bd11712b67e6e64588c2b5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="89488-102">Enumeração CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="89488-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="89488-103">Indica o estado do usuário de um thread.</span><span class="sxs-lookup"><span data-stu-id="89488-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89488-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89488-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="89488-105">Membros</span><span class="sxs-lookup"><span data-stu-id="89488-105">Members</span></span>  
  
|<span data-ttu-id="89488-106">Valor</span><span class="sxs-lookup"><span data-stu-id="89488-106">Value</span></span>|<span data-ttu-id="89488-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="89488-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="89488-108">Foi solicitado o encerramento do thread.</span><span class="sxs-lookup"><span data-stu-id="89488-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="89488-109">Foi solicitada uma suspensão do thread.</span><span class="sxs-lookup"><span data-stu-id="89488-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="89488-110">O thread está em execução em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="89488-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="89488-111">O thread não iniciou a execução.</span><span class="sxs-lookup"><span data-stu-id="89488-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="89488-112">O thread foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="89488-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="89488-113">O thread está aguardando outro thread para concluir uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="89488-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="89488-114">O thread foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="89488-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="89488-115">O thread está em um ponto desprotegido.</span><span class="sxs-lookup"><span data-stu-id="89488-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="89488-116">Ou seja, o thread está em um ponto na execução de onde ele pode bloquear a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="89488-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="89488-117">Depurar eventos podem ser distribuídos de pontos não seguros, mas a suspensão de um thread em um ponto desprotegido muito provavelmente causará um deadlock até que o thread seja retomado.</span><span class="sxs-lookup"><span data-stu-id="89488-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="89488-118">Os pontos seguros e são determinados pela implementação de coleta de lixo e just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="89488-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="89488-119">É o thread do pool de threads.</span><span class="sxs-lookup"><span data-stu-id="89488-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89488-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="89488-120">Remarks</span></span>  
 <span data-ttu-id="89488-121">O estado do usuário de um thread é o estado em que o thread tem quando o depurador examina a ele.</span><span class="sxs-lookup"><span data-stu-id="89488-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="89488-122">Um thread pode ter uma combinação de estados do usuário.</span><span class="sxs-lookup"><span data-stu-id="89488-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="89488-123">Use o [Getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) método para recuperar o estado do usuário do thread.</span><span class="sxs-lookup"><span data-stu-id="89488-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89488-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89488-124">Requirements</span></span>  
 <span data-ttu-id="89488-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89488-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89488-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89488-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89488-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89488-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89488-128">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89488-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89488-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89488-129">See Also</span></span>  
 [<span data-ttu-id="89488-130">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="89488-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
