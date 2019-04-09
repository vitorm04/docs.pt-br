---
title: Interface ICorDebugManagedCallback2
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1ecfea208f87f53f15fcc4cdafb58341c293e43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096082"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="cdac3-102">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="cdac3-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="cdac3-103">Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs).</span><span class="sxs-lookup"><span data-stu-id="cdac3-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> `ICorDebugManagedCallback2` <span data-ttu-id="cdac3-104">é uma extensão lógica do [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="cdac3-104">is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cdac3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="cdac3-105">Methods</span></span>  
  
|<span data-ttu-id="cdac3-106">Método</span><span class="sxs-lookup"><span data-stu-id="cdac3-106">Method</span></span>|<span data-ttu-id="cdac3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdac3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cdac3-108">Método ChangeConnection</span><span class="sxs-lookup"><span data-stu-id="cdac3-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="cdac3-109">Notifica o depurador que o conjunto de tarefas associadas com a conexão especificada foi alterado.</span><span class="sxs-lookup"><span data-stu-id="cdac3-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="cdac3-110">Método CreateConnection</span><span class="sxs-lookup"><span data-stu-id="cdac3-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="cdac3-111">Notifica o depurador que foi criada uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="cdac3-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="cdac3-112">Método DestroyConnection</span><span class="sxs-lookup"><span data-stu-id="cdac3-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="cdac3-113">Notifica o depurador para que a conexão especificada foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="cdac3-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="cdac3-114">Método Exception</span><span class="sxs-lookup"><span data-stu-id="cdac3-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="cdac3-115">Notifica o depurador que uma pesquisa por um manipulador de exceção foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="cdac3-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="cdac3-116">Método ExceptionUnwind</span><span class="sxs-lookup"><span data-stu-id="cdac3-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="cdac3-117">Fornece uma notificação de status durante o processo de desenrolamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="cdac3-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="cdac3-118">Método FunctionRemapComplete</span><span class="sxs-lookup"><span data-stu-id="cdac3-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="cdac3-119">Notifica o depurador para que a execução de código mudou para uma nova versão de uma função editada.</span><span class="sxs-lookup"><span data-stu-id="cdac3-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="cdac3-120">Método FunctionRemapOpportunity</span><span class="sxs-lookup"><span data-stu-id="cdac3-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="cdac3-121">Notifica o depurador para que a execução de código atingiu um ponto de sequência em uma versão mais antiga de uma função editada.</span><span class="sxs-lookup"><span data-stu-id="cdac3-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="cdac3-122">Método MDANotification</span><span class="sxs-lookup"><span data-stu-id="cdac3-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="cdac3-123">Fornece notificação de que a execução de código encontrou uma mensagem MDA (Assistente) depuração gerenciada.</span><span class="sxs-lookup"><span data-stu-id="cdac3-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdac3-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdac3-124">Remarks</span></span>  
 <span data-ttu-id="cdac3-125">O `ICorDebugManagedCallback2` interface estende o `ICorDebugManagedCallback` interface para lidar com novos eventos de depuração introduzidos no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="cdac3-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="cdac3-126">Um depurador deve implementar `ICorDebugManagedCallback2` se ele está depurando aplicativos do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="cdac3-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="cdac3-127">Uma instância do `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` é passado como o objeto de retorno de chamada para [icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="cdac3-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdac3-128">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="cdac3-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdac3-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cdac3-129">Requirements</span></span>  
 <span data-ttu-id="cdac3-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdac3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdac3-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdac3-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdac3-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdac3-132">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cdac3-133">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cdac3-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cdac3-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdac3-134">See also</span></span>

- [<span data-ttu-id="cdac3-135">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="cdac3-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cdac3-136">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cdac3-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cdac3-137">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="cdac3-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
