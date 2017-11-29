---
title: "Método ICorDebugManagedCallback::EditAndContinueRemap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EditAndContinueRemap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e45cf5376f0c8b4fbe76f56e3adcce22b1ef5c88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="df892-102">Método ICorDebugManagedCallback::EditAndContinueRemap</span><span class="sxs-lookup"><span data-stu-id="df892-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="df892-103">Esse método foi substituído.</span><span class="sxs-lookup"><span data-stu-id="df892-103">This method has been deprecated.</span></span> <span data-ttu-id="df892-104">Notifica o depurador que um evento remapear foi enviado para o ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="df892-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df892-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df892-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="df892-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="df892-106">Remarks</span></span>  
 <span data-ttu-id="df892-107">O `EditAndContinueRemap` método é chamado quando a execução de código em uma versão antiga de uma função atualizada foi tentada.</span><span class="sxs-lookup"><span data-stu-id="df892-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="df892-108">As chamadas de tempo de execução de linguagem comum do `EditAndContinueRemap` para enviar um evento remapear o IDE.</span><span class="sxs-lookup"><span data-stu-id="df892-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df892-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df892-109">Requirements</span></span>  
 <span data-ttu-id="df892-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df892-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df892-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df892-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df892-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df892-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df892-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df892-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df892-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df892-114">See Also</span></span>  
 [<span data-ttu-id="df892-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="df892-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
