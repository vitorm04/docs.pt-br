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
ms.openlocfilehash: 0431b54997c9889e2b3206392e86e4dcde45ffb3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212445"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="b8312-102">Método ICorDebugManagedCallback::EvalComplete</span><span class="sxs-lookup"><span data-stu-id="b8312-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="b8312-103">Notifica o depurador de que uma avaliação foi concluída.</span><span class="sxs-lookup"><span data-stu-id="b8312-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8312-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8312-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8312-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8312-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b8312-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual a avaliação foi executada.</span><span class="sxs-lookup"><span data-stu-id="b8312-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b8312-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual a avaliação foi executada.</span><span class="sxs-lookup"><span data-stu-id="b8312-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="b8312-108">no Um ponteiro para um objeto ICorDebugEval que representa o código que realizou a avaliação.</span><span class="sxs-lookup"><span data-stu-id="b8312-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8312-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8312-109">Requirements</span></span>  
 <span data-ttu-id="b8312-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8312-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8312-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8312-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8312-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8312-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8312-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8312-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8312-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8312-114">See also</span></span>

- [<span data-ttu-id="b8312-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b8312-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
