---
title: Interface ICorDebug
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug
helpviewer_keywords: ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ed0b3a8b42157f6a4fcbc6b4a05a416da736147
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebug-interface"></a><span data-ttu-id="1d98b-102">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1d98b-102">ICorDebug Interface</span></span>
<span data-ttu-id="1d98b-103">Fornece métodos que permitem aos desenvolvedores depurar aplicativos no ambiente do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1d98b-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d98b-104">Não há suporte para a depuração (código gerenciado e nativo) de modo misto no Windows 95, Windows 98 ou Windows ME ou em plataformas x86 não (como IA64 e AMD64).</span><span class="sxs-lookup"><span data-stu-id="1d98b-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d98b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1d98b-105">Methods</span></span>  
  
|<span data-ttu-id="1d98b-106">Método</span><span class="sxs-lookup"><span data-stu-id="1d98b-106">Method</span></span>|<span data-ttu-id="1d98b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d98b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d98b-108">Método CanLaunchOrAttach</span><span class="sxs-lookup"><span data-stu-id="1d98b-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="1d98b-109">Determina se iniciar um novo processo ou anexar ao processo determinado é possíveis dentro do contexto da configuração do computador e o tempo de execução atual.</span><span class="sxs-lookup"><span data-stu-id="1d98b-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="1d98b-110">Método CreateProcess</span><span class="sxs-lookup"><span data-stu-id="1d98b-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="1d98b-111">Inicia um processo e o thread principal sob o controle do depurador.</span><span class="sxs-lookup"><span data-stu-id="1d98b-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="1d98b-112">Método DebugActiveProcess</span><span class="sxs-lookup"><span data-stu-id="1d98b-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="1d98b-113">Anexa o depurador a um processo existente.</span><span class="sxs-lookup"><span data-stu-id="1d98b-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="1d98b-114">Método EnumerateProcesses</span><span class="sxs-lookup"><span data-stu-id="1d98b-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="1d98b-115">Obtém um enumerador para os processos que estão sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="1d98b-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="1d98b-116">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="1d98b-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="1d98b-117">Retorna o objeto "ICorDebugProcess" com a ID de processo especificado.</span><span class="sxs-lookup"><span data-stu-id="1d98b-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="1d98b-118">Método Initialize</span><span class="sxs-lookup"><span data-stu-id="1d98b-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="1d98b-119">Inicializa o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="1d98b-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="1d98b-120">Método SetManagedHandler</span><span class="sxs-lookup"><span data-stu-id="1d98b-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="1d98b-121">Especifica o objeto do manipulador de eventos para eventos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="1d98b-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="1d98b-122">Método SetUnmanagedHandler</span><span class="sxs-lookup"><span data-stu-id="1d98b-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="1d98b-123">Especifica o objeto do manipulador de eventos para eventos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="1d98b-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="1d98b-124">Método Terminate</span><span class="sxs-lookup"><span data-stu-id="1d98b-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="1d98b-125">Encerra o `ICorDebug` objeto.</span><span class="sxs-lookup"><span data-stu-id="1d98b-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d98b-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d98b-126">Remarks</span></span>  
 <span data-ttu-id="1d98b-127">`ICorDebug`representa um loop de processamento de eventos para um processo do depurador.</span><span class="sxs-lookup"><span data-stu-id="1d98b-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="1d98b-128">O depurador deve aguardar o [: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) retorno de chamada de todos os processos que está sendo depurado antes de liberar esta interface.</span><span class="sxs-lookup"><span data-stu-id="1d98b-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="1d98b-129">O `ICorDebug` é o objeto inicial para controlar a depuração gerenciada tudo mais.</span><span class="sxs-lookup"><span data-stu-id="1d98b-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="1d98b-130">Nas versões do .NET Framework 1.0 e 1.1, este objeto foi uma `CoClass` objeto criado pela COM.</span><span class="sxs-lookup"><span data-stu-id="1d98b-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="1d98b-131">No .NET Framework versão 2.0, esse objeto não é mais um `CoClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="1d98b-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="1d98b-132">Ele deve ser criado pelo [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) função, que tem mais suporte a versão.</span><span class="sxs-lookup"><span data-stu-id="1d98b-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="1d98b-133">Essa nova função de criação permite que os clientes obter uma implementação específica de `ICorDebug`, que emula também uma versão específica da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="1d98b-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d98b-134">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="1d98b-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d98b-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d98b-135">Requirements</span></span>  
 <span data-ttu-id="1d98b-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d98b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d98b-137">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d98b-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d98b-138">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d98b-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d98b-139">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d98b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d98b-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d98b-140">See Also</span></span>  
 [<span data-ttu-id="1d98b-141">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1d98b-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
