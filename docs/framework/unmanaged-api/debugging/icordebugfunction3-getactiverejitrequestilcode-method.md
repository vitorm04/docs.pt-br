---
title: "ICorDebugFunction3::Método GetActiveReJitRequestILCode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugFunction3.GetActiveReJitRequestILCode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6459297a2a04728ca87801bfc8484acec384a45c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="c9e0b-102">ICorDebugFunction3::Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="c9e0b-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="c9e0b-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="c9e0b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c9e0b-104">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o IL de uma solicitação ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="c9e0b-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e0b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9e0b-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9e0b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9e0b-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="c9e0b-107">Um ponteiro para a IL de uma solicitação ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="c9e0b-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9e0b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9e0b-108">Remarks</span></span>  
 <span data-ttu-id="c9e0b-109">Se o método representado por este objeto `ICorDebugFunction3` tiver uma solicitação ReJIT ativa, `ppReJitedILCode` retornará um ponteiro para sua IL.</span><span class="sxs-lookup"><span data-stu-id="c9e0b-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="c9e0b-110">Se não houver nenhuma solicitação ativa, o que é o caso comum, em seguida, `ppReJitedILCode` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="c9e0b-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="c9e0b-111">Uma solicitação de ReJIT se torna ativa após a execução retorna a partir de [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) chamada de método.</span><span class="sxs-lookup"><span data-stu-id="c9e0b-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="c9e0b-112">Pode ainda não estar compilada em JIT e threads podem ainda estar em execução na versão original do código.</span><span class="sxs-lookup"><span data-stu-id="c9e0b-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="c9e0b-113">Uma solicitação de ReJIT se torna inativa durante a chamada do criador de perfil para o [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="c9e0b-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="c9e0b-114">Mesmo depois que a IL é revertida, um thread ainda pode estar em execução no código ReJIT (recompilado por JIT).</span><span class="sxs-lookup"><span data-stu-id="c9e0b-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e0b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9e0b-115">Requirements</span></span>  
 <span data-ttu-id="c9e0b-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9e0b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9e0b-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9e0b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9e0b-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9e0b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9e0b-119">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9e0b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e0b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9e0b-120">See Also</span></span>  
 [<span data-ttu-id="c9e0b-121">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="c9e0b-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 [<span data-ttu-id="c9e0b-122">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="c9e0b-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c9e0b-123">ReJIT: Um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="c9e0b-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
