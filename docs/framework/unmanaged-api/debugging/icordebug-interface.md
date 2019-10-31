---
title: Interface ICorDebug
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: ee6bcbc9f3377735ed289d52afddb6efa755b16d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134069"
---
# <a name="icordebug-interface"></a><span data-ttu-id="c4c19-102">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="c4c19-102">ICorDebug Interface</span></span>
<span data-ttu-id="c4c19-103">Fornece métodos que permitem aos desenvolvedores depurar aplicativos no ambiente Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c4c19-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4c19-104">Não há suporte para depuração de modo misto (código gerenciado e nativo) no Windows 95, Windows 98 ou Windows ME ou em plataformas não x86 (como IA64 e AMD64).</span><span class="sxs-lookup"><span data-stu-id="c4c19-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4c19-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c4c19-105">Methods</span></span>  
  
|<span data-ttu-id="c4c19-106">Método</span><span class="sxs-lookup"><span data-stu-id="c4c19-106">Method</span></span>|<span data-ttu-id="c4c19-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4c19-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4c19-108">Método CanLaunchOrAttach</span><span class="sxs-lookup"><span data-stu-id="c4c19-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="c4c19-109">Determina se é possível iniciar um novo processo ou anexá-lo ao processo fornecido no contexto da máquina atual e da configuração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c4c19-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="c4c19-110">Método CreateProcess</span><span class="sxs-lookup"><span data-stu-id="c4c19-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="c4c19-111">Inicia um processo e seu thread principal sob o controle do depurador.</span><span class="sxs-lookup"><span data-stu-id="c4c19-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="c4c19-112">Método DebugActiveProcess</span><span class="sxs-lookup"><span data-stu-id="c4c19-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="c4c19-113">Anexa o depurador a um processo existente.</span><span class="sxs-lookup"><span data-stu-id="c4c19-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="c4c19-114">Método EnumerateProcesses</span><span class="sxs-lookup"><span data-stu-id="c4c19-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="c4c19-115">Obtém um enumerador para os processos que estão sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="c4c19-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="c4c19-116">Método GetProcess</span><span class="sxs-lookup"><span data-stu-id="c4c19-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="c4c19-117">Retorna o objeto "ICorDebugProcess" com a ID de processo fornecida.</span><span class="sxs-lookup"><span data-stu-id="c4c19-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="c4c19-118">Método Initialize</span><span class="sxs-lookup"><span data-stu-id="c4c19-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="c4c19-119">Inicializa o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="c4c19-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="c4c19-120">Método SetManagedHandler</span><span class="sxs-lookup"><span data-stu-id="c4c19-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="c4c19-121">Especifica o objeto manipulador de eventos para eventos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c4c19-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="c4c19-122">Método SetUnmanagedHandler</span><span class="sxs-lookup"><span data-stu-id="c4c19-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="c4c19-123">Especifica o objeto do manipulador de eventos para eventos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c4c19-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="c4c19-124">Método Terminate</span><span class="sxs-lookup"><span data-stu-id="c4c19-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="c4c19-125">Encerra o objeto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="c4c19-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4c19-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4c19-126">Remarks</span></span>  
 <span data-ttu-id="c4c19-127">`ICorDebug` representa um loop de processamento de eventos para um processo do depurador.</span><span class="sxs-lookup"><span data-stu-id="c4c19-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="c4c19-128">O depurador deve aguardar o retorno de chamada [ICorDebugManagedCallback:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) de todos os processos que estão sendo depurados antes de liberar essa interface.</span><span class="sxs-lookup"><span data-stu-id="c4c19-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="c4c19-129">O objeto `ICorDebug` é o objeto inicial para controlar toda a depuração gerenciada adicional.</span><span class="sxs-lookup"><span data-stu-id="c4c19-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="c4c19-130">No .NET Framework versões 1,0 e 1,1, esse objeto era um objeto `CoClass` criado a partir de COM.</span><span class="sxs-lookup"><span data-stu-id="c4c19-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="c4c19-131">No .NET Framework versão 2,0, esse objeto não é mais um objeto `CoClass`.</span><span class="sxs-lookup"><span data-stu-id="c4c19-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="c4c19-132">Ele deve ser criado pela função [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) , que tem mais reconhecimento de versão.</span><span class="sxs-lookup"><span data-stu-id="c4c19-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="c4c19-133">Essa nova função de criação permite que os clientes obtenham uma implementação específica do `ICorDebug`, que também emula uma versão específica da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="c4c19-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4c19-134">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="c4c19-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4c19-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4c19-135">Requirements</span></span>  
 <span data-ttu-id="c4c19-136">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4c19-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c19-137">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4c19-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4c19-138">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4c19-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4c19-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c19-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c19-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4c19-140">See also</span></span>

- [<span data-ttu-id="c4c19-141">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c4c19-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
