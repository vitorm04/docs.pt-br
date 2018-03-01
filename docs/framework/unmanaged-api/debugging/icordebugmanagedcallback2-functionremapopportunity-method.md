---
title: "Método ICorDebugManagedCallback2::FunctionRemapOpportunity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 208803acea65b24429938dc646e7abe70949b237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="23033-102">Método ICorDebugManagedCallback2::FunctionRemapOpportunity</span><span class="sxs-lookup"><span data-stu-id="23033-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="23033-103">Notifica o depurador que a execução de código atingiu um ponto de sequência em uma versão anterior de uma função editada.</span><span class="sxs-lookup"><span data-stu-id="23033-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23033-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23033-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23033-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23033-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="23033-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a função editada.</span><span class="sxs-lookup"><span data-stu-id="23033-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="23033-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o thread em que o ponto de interrupção remapear foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="23033-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="23033-108">[in] Um ponteiro para um objeto ICorDebugFunction que representa a versão da função que está sendo executada no thread.</span><span class="sxs-lookup"><span data-stu-id="23033-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="23033-109">[in] Um ponteiro para um objeto ICorDebugFunction que representa a versão mais recente da função.</span><span class="sxs-lookup"><span data-stu-id="23033-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="23033-110">[in] O deslocamento de intermediate language (MSIL) da Microsoft do ponteiro de instrução na versão antiga da função.</span><span class="sxs-lookup"><span data-stu-id="23033-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23033-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="23033-111">Remarks</span></span>  
 <span data-ttu-id="23033-112">Esse retorno de chamada de depurador uma oportunidade para remapear o ponteiro de instrução para seus devidos lugares na nova versão da função especificada, chamando o [Icordebugilframe2](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="23033-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="23033-113">Se o depurador não chamar `RemapFunction` antes de chamar o [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método, o tempo de execução continuará a executar o código antigo e disparam outro `FunctionRemapOpportunity` retorno de chamada no próximo ponto de sequência.</span><span class="sxs-lookup"><span data-stu-id="23033-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="23033-114">Esse retorno de chamada será invocado para todos os quadros que está executando uma versão mais antiga da função dada até que o depurador Retorna S_OK.</span><span class="sxs-lookup"><span data-stu-id="23033-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23033-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23033-115">Requirements</span></span>  
 <span data-ttu-id="23033-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23033-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23033-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23033-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23033-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23033-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23033-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23033-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23033-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23033-120">See Also</span></span>  
 [<span data-ttu-id="23033-121">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="23033-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="23033-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="23033-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
