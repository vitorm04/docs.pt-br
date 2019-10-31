---
title: Método ICorDebugManagedCallback::EvalException
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
ms.openlocfilehash: 70ae72968c3411a6732b09c0afe3d82931410cb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130810"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="703a1-102">Método ICorDebugManagedCallback::EvalException</span><span class="sxs-lookup"><span data-stu-id="703a1-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="703a1-103">Notifica o depurador de que uma avaliação terminou com uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="703a1-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="703a1-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="703a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="703a1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="703a1-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual a avaliação foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="703a1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="703a1-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread em que a avaliação foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="703a1-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="703a1-108">no Um ponteiro para um objeto ICorDebugEval que representa o código que realizou a avaliação.</span><span class="sxs-lookup"><span data-stu-id="703a1-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="703a1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="703a1-109">Requirements</span></span>  
 <span data-ttu-id="703a1-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="703a1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="703a1-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="703a1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="703a1-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="703a1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="703a1-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="703a1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703a1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="703a1-114">See also</span></span>

- [<span data-ttu-id="703a1-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="703a1-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
