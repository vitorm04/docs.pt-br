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
ms.openlocfilehash: 53fedde028c7551e929cb583d38a4ec6937f2a8c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938090"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="eb766-102">ICorDebugFunction3::Método GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="eb766-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="eb766-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="eb766-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="eb766-104">Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o Il de uma solicitação de ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="eb766-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb766-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb766-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb766-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb766-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="eb766-107">Um ponteiro para a IL de uma solicitação ReJIT ativa.</span><span class="sxs-lookup"><span data-stu-id="eb766-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb766-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb766-108">Remarks</span></span>  
 <span data-ttu-id="eb766-109">Se o método representado por este objeto `ICorDebugFunction3` tiver uma solicitação ReJIT ativa, `ppReJitedILCode` retornará um ponteiro para sua IL.</span><span class="sxs-lookup"><span data-stu-id="eb766-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="eb766-110">Se não houver nenhuma solicitação ativa, que é um caso comum, `ppReJitedILCode` será **NULL**.</span><span class="sxs-lookup"><span data-stu-id="eb766-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="eb766-111">Uma solicitação ReJIT torna-se ativa logo após a execução retornar da chamada do método [ICorProfilerCallback4:: GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eb766-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="eb766-112">Pode ainda não estar compilada em JIT e threads podem ainda estar em execução na versão original do código.</span><span class="sxs-lookup"><span data-stu-id="eb766-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="eb766-113">Uma solicitação ReJIT se torna inativa durante a chamada do criador de perfil para o método [ICorProfilerInfo4:: RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eb766-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="eb766-114">Mesmo depois que a IL é revertida, um thread ainda pode estar em execução no código ReJIT (recompilado por JIT).</span><span class="sxs-lookup"><span data-stu-id="eb766-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb766-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="eb766-115">Requirements</span></span>  
 <span data-ttu-id="eb766-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb766-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb766-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb766-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb766-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb766-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb766-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb766-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb766-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="eb766-120">See also</span></span>

- [<span data-ttu-id="eb766-121">Interface ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="eb766-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [<span data-ttu-id="eb766-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="eb766-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="eb766-123">ReJIT: um guia de instruções</span><span class="sxs-lookup"><span data-stu-id="eb766-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
