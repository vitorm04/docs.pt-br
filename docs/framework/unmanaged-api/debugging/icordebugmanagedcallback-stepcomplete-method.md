---
title: Método ICorDebugManagedCallback::StepComplete
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
ms.openlocfilehash: 89b010706222ad44bccabd94191c42a888584944
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212653"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="b387b-102">Método ICorDebugManagedCallback::StepComplete</span><span class="sxs-lookup"><span data-stu-id="b387b-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="b387b-103">Notifica o depurador de que uma etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="b387b-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b387b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b387b-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b387b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b387b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b387b-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread no qual a etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="b387b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b387b-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual a etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="b387b-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="b387b-108">no Um ponteiro para um objeto ICorDebugStepper que representa a etapa na execução de código.</span><span class="sxs-lookup"><span data-stu-id="b387b-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="b387b-109">no Um valor da enumeração CorDebugStepReason que indica o resultado de uma etapa individual.</span><span class="sxs-lookup"><span data-stu-id="b387b-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b387b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b387b-110">Remarks</span></span>  
 <span data-ttu-id="b387b-111">O stepper pode ser usado para continuar a depuração, se desejado, a menos que a depuração seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="b387b-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b387b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b387b-112">Requirements</span></span>  
 <span data-ttu-id="b387b-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b387b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b387b-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b387b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b387b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b387b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b387b-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b387b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b387b-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="b387b-117">See also</span></span>

- [<span data-ttu-id="b387b-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b387b-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
