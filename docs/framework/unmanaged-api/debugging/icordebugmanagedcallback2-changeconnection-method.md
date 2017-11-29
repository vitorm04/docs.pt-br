---
title: "Método ICorDebugManagedCallback2::ChangeConnection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ChangeConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c62859cb6a3e61af9670834db169410cecb6787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="506ef-102">Método ICorDebugManagedCallback2::ChangeConnection</span><span class="sxs-lookup"><span data-stu-id="506ef-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="506ef-103">Notifica o depurador que o conjunto de tarefas associadas a conexão especificada foi alterado.</span><span class="sxs-lookup"><span data-stu-id="506ef-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="506ef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="506ef-104">Syntax</span></span>  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="506ef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="506ef-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="506ef-106">[in] Um ponteiro para um objeto de "ICorDebugProcess" que representa o processo que contém a conexão que foram alteradas.</span><span class="sxs-lookup"><span data-stu-id="506ef-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="506ef-107">[in] A ID da conexão alterada.</span><span class="sxs-lookup"><span data-stu-id="506ef-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="506ef-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="506ef-108">Remarks</span></span>  
 <span data-ttu-id="506ef-109">Um `ChangeConnection` retorno de chamada será acionado em qualquer um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="506ef-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="506ef-110">Quando um depurador é anexado a um processo que contém as conexões.</span><span class="sxs-lookup"><span data-stu-id="506ef-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="506ef-111">Nesse caso, o tempo de execução será gerar e enviar uma [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) eventos e um `ChangeConnection` evento para cada conexão no processo.</span><span class="sxs-lookup"><span data-stu-id="506ef-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="506ef-112">Um `ChangeConnection` evento é gerado para cada conexão existente, independentemente se o conjunto dessa conexão de tarefas foi alterado desde sua criação.</span><span class="sxs-lookup"><span data-stu-id="506ef-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
-   <span data-ttu-id="506ef-113">Quando um host chama [: Setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) no [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="506ef-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="506ef-114">O depurador deve verificar todos os threads do processo para acompanhar as alterações de novo.</span><span class="sxs-lookup"><span data-stu-id="506ef-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="506ef-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="506ef-115">Requirements</span></span>  
 <span data-ttu-id="506ef-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="506ef-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="506ef-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="506ef-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="506ef-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="506ef-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="506ef-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="506ef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506ef-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="506ef-120">See Also</span></span>  
 [<span data-ttu-id="506ef-121">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="506ef-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="506ef-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="506ef-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
