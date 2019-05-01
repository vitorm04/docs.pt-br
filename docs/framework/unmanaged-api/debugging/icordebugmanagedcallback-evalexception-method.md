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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 602bcd12d1fd4c5806de6db81252731baa447b7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988215"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="e3aa9-102">Método ICorDebugManagedCallback::EvalException</span><span class="sxs-lookup"><span data-stu-id="e3aa9-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="e3aa9-103">Notifica o depurador que uma avaliação foi encerrada com uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="e3aa9-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3aa9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3aa9-104">Syntax</span></span>  
  
```  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3aa9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3aa9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e3aa9-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual a avaliação foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="e3aa9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e3aa9-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual a avaliação foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="e3aa9-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="e3aa9-108">[in] Um ponteiro para um objeto ICorDebugEval que representa o código que executou a avaliação.</span><span class="sxs-lookup"><span data-stu-id="e3aa9-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3aa9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3aa9-109">Requirements</span></span>  
 <span data-ttu-id="e3aa9-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3aa9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3aa9-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3aa9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3aa9-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3aa9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3aa9-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3aa9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3aa9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3aa9-114">See also</span></span>

- [<span data-ttu-id="e3aa9-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="e3aa9-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
