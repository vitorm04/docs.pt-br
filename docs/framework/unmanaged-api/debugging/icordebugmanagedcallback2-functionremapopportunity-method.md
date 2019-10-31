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
ms.openlocfilehash: c6c361113a441df050a8e7cd5219819cc8332581
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131489"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="2e9e4-102">Método ICorDebugManagedCallback2::FunctionRemapOpportunity</span><span class="sxs-lookup"><span data-stu-id="2e9e4-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="2e9e4-103">Notifica o depurador de que a execução de código atingiu um ponto de sequência em uma versão mais antiga de uma função editada.</span><span class="sxs-lookup"><span data-stu-id="2e9e4-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e9e4-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e9e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e9e4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2e9e4-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém a função editada.</span><span class="sxs-lookup"><span data-stu-id="2e9e4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2e9e4-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread no qual o ponto de interrupção do remapeamento foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="2e9e4-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="2e9e4-108">no Um ponteiro para um objeto ICorDebugFunction que representa a versão da função que está sendo executada no momento no thread.</span><span class="sxs-lookup"><span data-stu-id="2e9e4-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="2e9e4-109">no Um ponteiro para um objeto ICorDebugFunction que representa a versão mais recente da função.</span><span class="sxs-lookup"><span data-stu-id="2e9e4-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="2e9e4-110">no O deslocamento da MSIL (Microsoft Intermediate Language) do ponteiro de instrução na versão antiga da função.</span><span class="sxs-lookup"><span data-stu-id="2e9e4-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e9e4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e9e4-111">Remarks</span></span>  
 <span data-ttu-id="2e9e4-112">Esse retorno de chamada dá ao depurador uma oportunidade de remapear o ponteiro de instrução para seu local apropriado na nova versão da função especificada chamando o método [ICorDebugILFrame2:: RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2e9e4-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="2e9e4-113">Se o depurador não chamar `RemapFunction` antes de chamar o método [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , o tempo de execução continuará a executar o código antigo e acionará outro `FunctionRemapOpportunity` retorno de chamada no próximo ponto de sequência.</span><span class="sxs-lookup"><span data-stu-id="2e9e4-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="2e9e4-114">Esse retorno de chamada será invocado para cada quadro que está executando uma versão mais antiga da função fornecida até que o depurador retorne S_OK.</span><span class="sxs-lookup"><span data-stu-id="2e9e4-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e9e4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e9e4-115">Requirements</span></span>  
 <span data-ttu-id="2e9e4-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e9e4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e9e4-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e9e4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e9e4-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e9e4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e9e4-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e9e4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9e4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e9e4-120">See also</span></span>

- [<span data-ttu-id="2e9e4-121">Interface ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="2e9e4-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="2e9e4-122">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="2e9e4-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
