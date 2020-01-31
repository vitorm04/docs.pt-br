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
ms.openlocfilehash: e5d828b8252b47c2edddbe14713208ae8bc2d19d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777160"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="952d5-102">Método ICorDebugManagedCallback::StepComplete</span><span class="sxs-lookup"><span data-stu-id="952d5-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="952d5-103">Notifica o depurador de que uma etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="952d5-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="952d5-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="952d5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="952d5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="952d5-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread no qual a etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="952d5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="952d5-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual a etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="952d5-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="952d5-108">no Um ponteiro para um objeto ICorDebugStepper que representa a etapa na execução de código.</span><span class="sxs-lookup"><span data-stu-id="952d5-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="952d5-109">no Um valor da enumeração CorDebugStepReason que indica o resultado de uma etapa individual.</span><span class="sxs-lookup"><span data-stu-id="952d5-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="952d5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="952d5-110">Remarks</span></span>  
 <span data-ttu-id="952d5-111">O stepper pode ser usado para continuar a depuração, se desejado, a menos que a depuração seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="952d5-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="952d5-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="952d5-112">Requirements</span></span>  
 <span data-ttu-id="952d5-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="952d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="952d5-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="952d5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="952d5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="952d5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="952d5-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="952d5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952d5-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="952d5-117">See also</span></span>

- [<span data-ttu-id="952d5-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="952d5-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
