---
title: ICorDebugFunction3::Método GetActiveReJitRequestILCode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 9e7f682752cfefae63b574655a4fc5e8964146a0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213173"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="76400-102">ICorDebugFunction3::Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="76400-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="76400-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="76400-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="76400-104">Obtém um ponteiro de interface para um [ICorDebugILCode](icordebugilcode-interface.md) que contém o Il de uma solicitação de ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="76400-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76400-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76400-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76400-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76400-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="76400-107">Um ponteiro para a IL de uma solicitação ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="76400-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76400-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="76400-108">Remarks</span></span>  
 <span data-ttu-id="76400-109">Se o método representado por este objeto `ICorDebugFunction3` tiver uma solicitação ReJIT ativa, `ppReJitedILCode` retornará um ponteiro para sua IL.</span><span class="sxs-lookup"><span data-stu-id="76400-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="76400-110">Se não houver nenhuma solicitação ativa, que é um caso comum, `ppReJitedILCode` será **NULL**.</span><span class="sxs-lookup"><span data-stu-id="76400-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="76400-111">Uma solicitação ReJIT torna-se ativa logo após a execução retornar da chamada do método [ICorProfilerCallback4:: GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="76400-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="76400-112">Pode ainda não estar compilada em JIT e threads podem ainda estar em execução na versão original do código.</span><span class="sxs-lookup"><span data-stu-id="76400-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="76400-113">Uma solicitação ReJIT se torna inativa durante a chamada do criador de perfil para o método [ICorProfilerInfo4:: RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="76400-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="76400-114">Mesmo depois que a IL é revertida, um thread ainda pode estar em execução no código ReJIT (recompilado por JIT).</span><span class="sxs-lookup"><span data-stu-id="76400-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76400-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76400-115">Requirements</span></span>  
 <span data-ttu-id="76400-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76400-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76400-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76400-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76400-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76400-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76400-119">**.NET Framework versões:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76400-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76400-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="76400-120">See also</span></span>

- [<span data-ttu-id="76400-121">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="76400-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="76400-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="76400-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="76400-123">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="76400-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
