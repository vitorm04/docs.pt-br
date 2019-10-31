---
title: Método ICorDebugManagedCallback::EvalComplete
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
ms.openlocfilehash: d52c19f8663a776215241ddb16f3aa9ba00c0d36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137348"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="21e81-102">Método ICorDebugManagedCallback::EvalComplete</span><span class="sxs-lookup"><span data-stu-id="21e81-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="21e81-103">Notifica o depurador de que uma avaliação foi concluída.</span><span class="sxs-lookup"><span data-stu-id="21e81-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21e81-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21e81-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21e81-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="21e81-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual a avaliação foi executada.</span><span class="sxs-lookup"><span data-stu-id="21e81-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="21e81-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual a avaliação foi executada.</span><span class="sxs-lookup"><span data-stu-id="21e81-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="21e81-108">no Um ponteiro para um objeto ICorDebugEval que representa o código que realizou a avaliação.</span><span class="sxs-lookup"><span data-stu-id="21e81-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e81-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21e81-109">Requirements</span></span>  
 <span data-ttu-id="21e81-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e81-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e81-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21e81-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21e81-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21e81-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21e81-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e81-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e81-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21e81-114">See also</span></span>

- [<span data-ttu-id="21e81-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="21e81-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
