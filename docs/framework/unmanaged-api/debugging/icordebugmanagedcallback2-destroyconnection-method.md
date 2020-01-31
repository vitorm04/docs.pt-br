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
ms.openlocfilehash: 4f6940f863504a9aedd9539e121c7b3791f746b9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788300"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="2ced2-102">Método ICorDebugManagedCallback2::DestroyConnection</span><span class="sxs-lookup"><span data-stu-id="2ced2-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="2ced2-103">Notifica o depurador de que a conexão especificada foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="2ced2-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ced2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ced2-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ced2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ced2-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="2ced2-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo que contém a conexão que foi destruída.</span><span class="sxs-lookup"><span data-stu-id="2ced2-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="2ced2-107">no A ID da conexão que foi destruída.</span><span class="sxs-lookup"><span data-stu-id="2ced2-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ced2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ced2-108">Remarks</span></span>  
 <span data-ttu-id="2ced2-109">Um retorno de chamada `DestroyConnection` será acionado quando um host chamar [ICLRDebugManager:: EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) na [API de hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="2ced2-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ced2-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2ced2-110">Requirements</span></span>  
 <span data-ttu-id="2ced2-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ced2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ced2-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ced2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ced2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ced2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ced2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ced2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ced2-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="2ced2-115">See also</span></span>

- [<span data-ttu-id="2ced2-116">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="2ced2-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="2ced2-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="2ced2-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
