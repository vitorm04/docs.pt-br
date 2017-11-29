---
title: "Método ICorDebugManagedCallback::StepComplete"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.StepComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eabc9a2730a1afdf574cee97a6f1b40bae34c7ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="a7ff5-102">Método ICorDebugManagedCallback::StepComplete</span><span class="sxs-lookup"><span data-stu-id="a7ff5-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="a7ff5-103">Notifica o depurador que uma etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="a7ff5-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ff5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7ff5-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7ff5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7ff5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a7ff5-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o segmento em que a etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="a7ff5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a7ff5-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o thread em que a etapa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="a7ff5-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="a7ff5-108">[in] Um ponteiro para um objeto ICorDebugStepper que representa a etapa na execução de código.</span><span class="sxs-lookup"><span data-stu-id="a7ff5-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="a7ff5-109">[in] Um valor da enumeração CorDebugStepReason que indica o resultado de uma etapa individual.</span><span class="sxs-lookup"><span data-stu-id="a7ff5-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ff5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7ff5-110">Remarks</span></span>  
 <span data-ttu-id="a7ff5-111">O seletor pode ser usado para continuar a depuração se desejado, a menos que a depuração será encerrada.</span><span class="sxs-lookup"><span data-stu-id="a7ff5-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ff5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7ff5-112">Requirements</span></span>  
 <span data-ttu-id="a7ff5-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ff5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ff5-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7ff5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7ff5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7ff5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7ff5-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ff5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ff5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7ff5-117">See Also</span></span>  
 [<span data-ttu-id="a7ff5-118">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a7ff5-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
