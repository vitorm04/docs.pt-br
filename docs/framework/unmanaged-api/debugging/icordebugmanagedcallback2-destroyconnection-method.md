---
title: Método ICorDebugManagedCallback2::DestroyConnection
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6d4acb7d1156babbd698201c5aea2810644db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415396"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="44d9a-102">Método ICorDebugManagedCallback2::DestroyConnection</span><span class="sxs-lookup"><span data-stu-id="44d9a-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="44d9a-103">Notifica o depurador a conexão especificada foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="44d9a-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d9a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44d9a-104">Syntax</span></span>  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44d9a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44d9a-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="44d9a-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo que contém a conexão foi destruído.</span><span class="sxs-lookup"><span data-stu-id="44d9a-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="44d9a-107">[in] A ID da conexão foi destruído.</span><span class="sxs-lookup"><span data-stu-id="44d9a-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44d9a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="44d9a-108">Remarks</span></span>  
 <span data-ttu-id="44d9a-109">Um `DestroyConnection` retorno de chamada será acionado quando um host chama [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) no [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="44d9a-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44d9a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44d9a-110">Requirements</span></span>  
 <span data-ttu-id="44d9a-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44d9a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d9a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44d9a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44d9a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44d9a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44d9a-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d9a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d9a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44d9a-115">See Also</span></span>  
 [<span data-ttu-id="44d9a-116">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="44d9a-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="44d9a-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="44d9a-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
