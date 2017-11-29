---
title: Interface1 ICorDebugThread2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2
helpviewer_keywords: ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d3a554d075adb56294e4693b234ce22735fb982
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="71e2b-102">Interface1 ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="71e2b-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="71e2b-103">Serve como uma extensão lógica para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="71e2b-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71e2b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="71e2b-104">Methods</span></span>  
  
|<span data-ttu-id="71e2b-105">Método</span><span class="sxs-lookup"><span data-stu-id="71e2b-105">Method</span></span>|<span data-ttu-id="71e2b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="71e2b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71e2b-107">Método GetActiveFunctions</span><span class="sxs-lookup"><span data-stu-id="71e2b-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="71e2b-108">Obtém uma matriz de instâncias COR_ACTIVE_FUNCTION que contêm dados sobre as funções ativas em quadros do thread.</span><span class="sxs-lookup"><span data-stu-id="71e2b-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="71e2b-109">Método GetConnectionID</span><span class="sxs-lookup"><span data-stu-id="71e2b-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="71e2b-110">Obtém um identificador de conexão para este `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="71e2b-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="71e2b-111">Método GetTaskID</span><span class="sxs-lookup"><span data-stu-id="71e2b-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="71e2b-112">Obtém um identificador de tarefas para este `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="71e2b-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="71e2b-113">Método GetVolatileOSThreadID</span><span class="sxs-lookup"><span data-stu-id="71e2b-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="71e2b-114">Obtém o identificador de thread do sistema operacional para este `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="71e2b-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="71e2b-115">Método InterceptCurrentException</span><span class="sxs-lookup"><span data-stu-id="71e2b-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="71e2b-116">Permite que um depurador interceptar a exceção atual em um thread.</span><span class="sxs-lookup"><span data-stu-id="71e2b-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71e2b-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="71e2b-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71e2b-118">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="71e2b-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71e2b-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71e2b-119">Requirements</span></span>  
 <span data-ttu-id="71e2b-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71e2b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71e2b-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71e2b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71e2b-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71e2b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71e2b-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71e2b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e2b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71e2b-124">See Also</span></span>  
 [<span data-ttu-id="71e2b-125">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="71e2b-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
