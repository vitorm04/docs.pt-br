---
title: "Método ICorDebugManagedCallback2::CreateConnection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e0037f72e51683e5b1d62ad7ecb9aa185f53370
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="c26a4-102">Método ICorDebugManagedCallback2::CreateConnection</span><span class="sxs-lookup"><span data-stu-id="c26a4-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="c26a4-103">Notifica o depurador que foi criada uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="c26a4-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c26a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c26a4-104">Syntax</span></span>  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c26a4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c26a4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="c26a4-106">[in] Um ponteiro para um objeto de "ICorDebugProcess" que representa o processo no qual a conexão foi criada</span><span class="sxs-lookup"><span data-stu-id="c26a4-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="c26a4-107">[in] A ID da conexão de novo.</span><span class="sxs-lookup"><span data-stu-id="c26a4-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="c26a4-108">[in] Um ponteiro para o nome da conexão de novo.</span><span class="sxs-lookup"><span data-stu-id="c26a4-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c26a4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c26a4-109">Remarks</span></span>  
 <span data-ttu-id="c26a4-110">Um `CreateConnection` retorno de chamada será acionado em qualquer um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="c26a4-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="c26a4-111">Quando um depurador é anexado a um processo que contém as conexões.</span><span class="sxs-lookup"><span data-stu-id="c26a4-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="c26a4-112">Nesse caso, o tempo de execução será gerar e enviar uma `CreateConnection` eventos e uma [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) evento para cada conexão no processo.</span><span class="sxs-lookup"><span data-stu-id="c26a4-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
-   <span data-ttu-id="c26a4-113">Quando um host chama [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) no [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="c26a4-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c26a4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c26a4-114">Requirements</span></span>  
 <span data-ttu-id="c26a4-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c26a4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c26a4-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c26a4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c26a4-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c26a4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c26a4-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26a4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26a4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c26a4-119">See Also</span></span>  
 [<span data-ttu-id="c26a4-120">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="c26a4-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="c26a4-121">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="c26a4-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
