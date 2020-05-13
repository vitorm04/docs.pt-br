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
ms.openlocfilehash: 20a841006d51671a491e11c4e40287baf739d191
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209817"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="3234f-102">Método ICorDebugManagedCallback::EvalException</span><span class="sxs-lookup"><span data-stu-id="3234f-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="3234f-103">Notifica o depurador de que uma avaliação terminou com uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="3234f-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3234f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3234f-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3234f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3234f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3234f-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual a avaliação foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="3234f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="3234f-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread em que a avaliação foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="3234f-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="3234f-108">no Um ponteiro para um objeto ICorDebugEval que representa o código que realizou a avaliação.</span><span class="sxs-lookup"><span data-stu-id="3234f-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3234f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3234f-109">Requirements</span></span>  
 <span data-ttu-id="3234f-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3234f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3234f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3234f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3234f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3234f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3234f-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3234f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3234f-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="3234f-114">See also</span></span>

- [<span data-ttu-id="3234f-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="3234f-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
