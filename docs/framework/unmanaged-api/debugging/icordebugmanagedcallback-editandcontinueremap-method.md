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
ms.openlocfilehash: 78b87b5c566b0d760a205757430123665fb2fcd3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213693"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="93723-102">Método ICorDebugManagedCallback::EditAndContinueRemap</span><span class="sxs-lookup"><span data-stu-id="93723-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="93723-103">Esse método foi substituído.</span><span class="sxs-lookup"><span data-stu-id="93723-103">This method has been deprecated.</span></span> <span data-ttu-id="93723-104">Ele notifica o depurador de que um evento de remapeamento foi enviado para o ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="93723-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93723-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93723-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="93723-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="93723-106">Remarks</span></span>  
 <span data-ttu-id="93723-107">O `EditAndContinueRemap` método é chamado quando a execução do código em uma versão antiga de uma função atualizada foi tentada.</span><span class="sxs-lookup"><span data-stu-id="93723-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="93723-108">O Common Language Runtime chama o `EditAndContinueRemap` método para enviar um evento de remapeamento para o IDE.</span><span class="sxs-lookup"><span data-stu-id="93723-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93723-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93723-109">Requirements</span></span>  
 <span data-ttu-id="93723-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93723-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93723-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93723-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93723-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93723-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93723-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93723-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93723-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="93723-114">See also</span></span>

- [<span data-ttu-id="93723-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="93723-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
