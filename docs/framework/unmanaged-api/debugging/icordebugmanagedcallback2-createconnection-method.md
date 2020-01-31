---
title: Método ICorDebugManagedCallback2::CreateConnection
ms.date: 03/30/2017
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
ms.openlocfilehash: e98748b523b948dc002f2ebc4e2e79fc7d659918
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781590"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="afd17-102">Método ICorDebugManagedCallback2::CreateConnection</span><span class="sxs-lookup"><span data-stu-id="afd17-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="afd17-103">Notifica o depurador de que uma nova conexão foi criada.</span><span class="sxs-lookup"><span data-stu-id="afd17-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afd17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="afd17-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afd17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="afd17-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="afd17-106">no Um ponteiro para um objeto "ICorDebugProcess" que representa o processo no qual a conexão foi criada</span><span class="sxs-lookup"><span data-stu-id="afd17-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="afd17-107">no A ID da nova conexão.</span><span class="sxs-lookup"><span data-stu-id="afd17-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="afd17-108">no Um ponteiro para o nome da nova conexão.</span><span class="sxs-lookup"><span data-stu-id="afd17-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afd17-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="afd17-109">Remarks</span></span>  
 <span data-ttu-id="afd17-110">Um retorno de chamada `CreateConnection` será acionado em um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="afd17-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="afd17-111">Quando um depurador é anexado a um processo que contém conexões.</span><span class="sxs-lookup"><span data-stu-id="afd17-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="afd17-112">Nesse caso, o tempo de execução irá gerar e distribuir um evento de `CreateConnection` e um evento [ICorDebugManagedCallback2:: ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) para cada conexão no processo.</span><span class="sxs-lookup"><span data-stu-id="afd17-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="afd17-113">Quando um host chama [ICLRDebugManager:: BeginConnect](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) na API de [hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="afd17-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afd17-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="afd17-114">Requirements</span></span>  
 <span data-ttu-id="afd17-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afd17-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afd17-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afd17-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afd17-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afd17-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afd17-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afd17-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd17-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="afd17-119">See also</span></span>

- [<span data-ttu-id="afd17-120">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="afd17-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="afd17-121">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="afd17-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
