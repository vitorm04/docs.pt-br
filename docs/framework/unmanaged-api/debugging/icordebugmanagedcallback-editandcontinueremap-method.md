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
ms.openlocfilehash: 3fd1686eb268b9d4e347fe28e067a5321327dbd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137384"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="b8e72-102">Método ICorDebugManagedCallback::EditAndContinueRemap</span><span class="sxs-lookup"><span data-stu-id="b8e72-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="b8e72-103">Esse método foi substituído.</span><span class="sxs-lookup"><span data-stu-id="b8e72-103">This method has been deprecated.</span></span> <span data-ttu-id="b8e72-104">Ele notifica o depurador de que um evento de remapeamento foi enviado para o ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="b8e72-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e72-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8e72-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b8e72-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8e72-106">Remarks</span></span>  
 <span data-ttu-id="b8e72-107">O método `EditAndContinueRemap` é chamado quando a execução do código em uma versão antiga de uma função atualizada foi tentada.</span><span class="sxs-lookup"><span data-stu-id="b8e72-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="b8e72-108">O Common Language Runtime chama o método `EditAndContinueRemap` para enviar um evento de remapeamento para o IDE.</span><span class="sxs-lookup"><span data-stu-id="b8e72-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e72-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8e72-109">Requirements</span></span>  
 <span data-ttu-id="b8e72-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8e72-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e72-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8e72-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8e72-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8e72-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8e72-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8e72-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e72-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8e72-114">See also</span></span>

- [<span data-ttu-id="b8e72-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b8e72-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
