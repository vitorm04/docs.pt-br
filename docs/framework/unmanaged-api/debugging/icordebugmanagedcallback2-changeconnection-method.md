---
title: Método ICorDebugManagedCallback2::ChangeConnection
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: 2c6ed14f9238d653b15d26dec9d954c05238817c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213446"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="86e9b-102">Método ICorDebugManagedCallback2::ChangeConnection</span><span class="sxs-lookup"><span data-stu-id="86e9b-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="86e9b-103">Notifica o depurador de que o conjunto de tarefas associado à conexão especificada foi alterado.</span><span class="sxs-lookup"><span data-stu-id="86e9b-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86e9b-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86e9b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86e9b-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="86e9b-106">no Um ponteiro para um objeto "ICorDebugProcess" que representa o processo que contém a conexão que foi alterada.</span><span class="sxs-lookup"><span data-stu-id="86e9b-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="86e9b-107">no A ID da conexão que foi alterada.</span><span class="sxs-lookup"><span data-stu-id="86e9b-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86e9b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="86e9b-108">Remarks</span></span>  
 <span data-ttu-id="86e9b-109">Um `ChangeConnection` retorno de chamada será acionado em qualquer um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="86e9b-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="86e9b-110">Quando um depurador é anexado a um processo que contém conexões.</span><span class="sxs-lookup"><span data-stu-id="86e9b-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="86e9b-111">Nesse caso, o tempo de execução irá gerar e distribuir um evento [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) e um `ChangeConnection` evento para cada conexão no processo.</span><span class="sxs-lookup"><span data-stu-id="86e9b-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="86e9b-112">Um `ChangeConnection` evento é gerado para cada conexão existente, independentemente de o conjunto de tarefas dessa conexão ter sido alterado desde sua criação.</span><span class="sxs-lookup"><span data-stu-id="86e9b-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="86e9b-113">Quando um host chama [ICLRDebugManager:: SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) na [API de hospedagem](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="86e9b-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
 <span data-ttu-id="86e9b-114">O depurador deve verificar todos os threads no processo para selecionar as novas alterações.</span><span class="sxs-lookup"><span data-stu-id="86e9b-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e9b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86e9b-115">Requirements</span></span>  
 <span data-ttu-id="86e9b-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86e9b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e9b-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86e9b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86e9b-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86e9b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86e9b-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e9b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e9b-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="86e9b-120">See also</span></span>

- [<span data-ttu-id="86e9b-121">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="86e9b-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="86e9b-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="86e9b-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
