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
ms.openlocfilehash: a3093f33f2220b22b7b4b373f6d79a341abf8c9c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501931"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="e7c0d-102">Método ICorDebugManagedCallback2::DestroyConnection</span><span class="sxs-lookup"><span data-stu-id="e7c0d-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="e7c0d-103">Notifica o depurador de que a conexão especificada foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="e7c0d-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7c0d-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7c0d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7c0d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e7c0d-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo que contém a conexão que foi destruída.</span><span class="sxs-lookup"><span data-stu-id="e7c0d-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="e7c0d-107">no A ID da conexão que foi destruída.</span><span class="sxs-lookup"><span data-stu-id="e7c0d-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7c0d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7c0d-108">Remarks</span></span>  
 <span data-ttu-id="e7c0d-109">Um `DestroyConnection` retorno de chamada será acionado quando um host chamar [ICLRDebugManager:: EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) na [API de hospedagem](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="e7c0d-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7c0d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7c0d-110">Requirements</span></span>  
 <span data-ttu-id="e7c0d-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7c0d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7c0d-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7c0d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7c0d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7c0d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7c0d-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7c0d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c0d-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="e7c0d-115">See also</span></span>

- [<span data-ttu-id="e7c0d-116">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="e7c0d-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="e7c0d-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="e7c0d-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
