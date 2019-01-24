---
title: Método ICorDebugManagedCallback2::FunctionRemapOpportunity
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86736f885e40e553195cf2a5f84575a5384e6b60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564702"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="255b9-102">Método ICorDebugManagedCallback2::FunctionRemapOpportunity</span><span class="sxs-lookup"><span data-stu-id="255b9-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="255b9-103">Notifica o depurador para que a execução de código atingiu um ponto de sequência em uma versão mais antiga de uma função editada.</span><span class="sxs-lookup"><span data-stu-id="255b9-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="255b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="255b9-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="255b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="255b9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="255b9-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a função editada.</span><span class="sxs-lookup"><span data-stu-id="255b9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="255b9-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual o remapeamento de ponto de interrupção foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="255b9-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="255b9-108">[in] Um ponteiro para um objeto ICorDebugFunction que representa a versão da função que está sendo executado no thread.</span><span class="sxs-lookup"><span data-stu-id="255b9-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="255b9-109">[in] Um ponteiro para um objeto de ICorDebugFunction que representa a versão mais recente da função.</span><span class="sxs-lookup"><span data-stu-id="255b9-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="255b9-110">[in] O Microsoft intermediate language (MSIL) deslocamento o ponteiro de instrução na versão antiga da função.</span><span class="sxs-lookup"><span data-stu-id="255b9-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="255b9-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="255b9-111">Remarks</span></span>  
 <span data-ttu-id="255b9-112">Esse retorno de chamada oferece o depurador a oportunidade para remapear o ponteiro de instrução ao seu local apropriado na nova versão da função especificada chamando o [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="255b9-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="255b9-113">Se o depurador não chama `RemapFunction` antes de chamar o [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) método, o tempo de execução continuarão a executar o código antigo e dispararão a outro `FunctionRemapOpportunity` retorno de chamada no próximo ponto de sequência.</span><span class="sxs-lookup"><span data-stu-id="255b9-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="255b9-114">Esse retorno de chamada será invocado para cada quadro que está executando uma versão mais antiga da função determinada até que o depurador Retorna S_OK.</span><span class="sxs-lookup"><span data-stu-id="255b9-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="255b9-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="255b9-115">Requirements</span></span>  
 <span data-ttu-id="255b9-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="255b9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="255b9-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="255b9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="255b9-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="255b9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="255b9-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="255b9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="255b9-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="255b9-120">See also</span></span>
- [<span data-ttu-id="255b9-121">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="255b9-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="255b9-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="255b9-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
