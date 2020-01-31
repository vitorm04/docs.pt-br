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
ms.openlocfilehash: d60644d54373dfb3d1d191900df71d3e5f6547a6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788288"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="055cf-102">Método ICorDebugManagedCallback2::ChangeConnection</span><span class="sxs-lookup"><span data-stu-id="055cf-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="055cf-103">Notifica o depurador de que o conjunto de tarefas associado à conexão especificada foi alterado.</span><span class="sxs-lookup"><span data-stu-id="055cf-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="055cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="055cf-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="055cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="055cf-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="055cf-106">no Um ponteiro para um objeto "ICorDebugProcess" que representa o processo que contém a conexão que foi alterada.</span><span class="sxs-lookup"><span data-stu-id="055cf-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="055cf-107">no A ID da conexão que foi alterada.</span><span class="sxs-lookup"><span data-stu-id="055cf-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="055cf-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="055cf-108">Remarks</span></span>  
 <span data-ttu-id="055cf-109">Um retorno de chamada `ChangeConnection` será acionado em um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="055cf-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="055cf-110">Quando um depurador é anexado a um processo que contém conexões.</span><span class="sxs-lookup"><span data-stu-id="055cf-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="055cf-111">Nesse caso, o tempo de execução irá gerar e distribuir um evento [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) e um `ChangeConnection` para cada conexão no processo.</span><span class="sxs-lookup"><span data-stu-id="055cf-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="055cf-112">Um evento `ChangeConnection` é gerado para cada conexão existente, independentemente de o conjunto de tarefas dessa conexão ter sido alterado desde sua criação.</span><span class="sxs-lookup"><span data-stu-id="055cf-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="055cf-113">Quando um host chama [ICLRDebugManager:: SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) na [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="055cf-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="055cf-114">O depurador deve verificar todos os threads no processo para selecionar as novas alterações.</span><span class="sxs-lookup"><span data-stu-id="055cf-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="055cf-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="055cf-115">Requirements</span></span>  
 <span data-ttu-id="055cf-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="055cf-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="055cf-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="055cf-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="055cf-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="055cf-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="055cf-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="055cf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055cf-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="055cf-120">See also</span></span>

- [<span data-ttu-id="055cf-121">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="055cf-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="055cf-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="055cf-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
