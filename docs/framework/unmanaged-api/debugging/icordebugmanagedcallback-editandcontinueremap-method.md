---
title: Método ICorDebugManagedCallback::EditAndContinueRemap
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e8aa71a79bee45d5a8e1f3448c781e6ba1ec605
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="cc6d6-102">Método ICorDebugManagedCallback::EditAndContinueRemap</span><span class="sxs-lookup"><span data-stu-id="cc6d6-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="cc6d6-103">Esse método foi substituído.</span><span class="sxs-lookup"><span data-stu-id="cc6d6-103">This method has been deprecated.</span></span> <span data-ttu-id="cc6d6-104">Notifica o depurador que um evento remapear foi enviado para o ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="cc6d6-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6d6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc6d6-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="cc6d6-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc6d6-106">Remarks</span></span>  
 <span data-ttu-id="cc6d6-107">O `EditAndContinueRemap` método é chamado quando a execução de código em uma versão antiga de uma função atualizada foi tentada.</span><span class="sxs-lookup"><span data-stu-id="cc6d6-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="cc6d6-108">As chamadas de tempo de execução de linguagem comum do `EditAndContinueRemap` para enviar um evento remapear o IDE.</span><span class="sxs-lookup"><span data-stu-id="cc6d6-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6d6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc6d6-109">Requirements</span></span>  
 <span data-ttu-id="cc6d6-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc6d6-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc6d6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc6d6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc6d6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc6d6-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc6d6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6d6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc6d6-114">See Also</span></span>  
 [<span data-ttu-id="cc6d6-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="cc6d6-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
