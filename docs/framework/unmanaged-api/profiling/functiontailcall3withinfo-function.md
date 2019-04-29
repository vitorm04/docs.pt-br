---
title: Função FunctionTailcall3WithInfo
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4352d006c95a5b85341625220e6c7e62a86b482a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598760"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="c9363-102">Função FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9363-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="c9363-103">Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função e fornece um identificador que pode ser passado para o [método ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) para recuperar o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="c9363-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9363-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9363-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9363-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9363-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="c9363-106">[in] O identificador da função em execução no momento que está prestes a fazer uma cauda de chamada.</span><span class="sxs-lookup"><span data-stu-id="c9363-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="c9363-107">[in] Um identificador opaco que representa informações sobre um registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="c9363-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="c9363-108">Esse identificador é válido somente durante o retorno de chamada para o qual ele é passado.</span><span class="sxs-lookup"><span data-stu-id="c9363-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9363-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9363-109">Remarks</span></span>  
 <span data-ttu-id="c9363-110">O `FunctionTailcall3WithInfo` método de retorno de chamada notifica o criador de perfil como funções são chamadas e permite que o criador de perfil usar o [método ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) para inspecionar o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="c9363-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="c9363-111">Para acessar informações de quadro de pilha, o `COR_PRF_ENABLE_FRAME_INFO` sinalizador deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="c9363-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="c9363-112">O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o [método ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar seu implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="c9363-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="c9363-113">O `FunctionTailcall3WithInfo` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="c9363-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="c9363-114">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="c9363-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="c9363-115">O mecanismo de execução não salva qualquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="c9363-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c9363-116">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="c9363-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c9363-117">Na saída, você deve restaurar a pilha de popping desativar todos os parâmetros que foram enviados por push ao seu chamador.</span><span class="sxs-lookup"><span data-stu-id="c9363-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c9363-118">A implementação de `FunctionTailcall3WithInfo` não devem bloquear, porque isso atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c9363-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="c9363-119">A implementação não deve tentar uma coleta de lixo, porque a pilha não pode estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c9363-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c9363-120">Se você tentar uma coleta de lixo, o tempo de execução será bloqueado até que `FunctionTailcall3WithInfo` retorna.</span><span class="sxs-lookup"><span data-stu-id="c9363-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="c9363-121">Além disso, a função FunctionTailcall3WithInfo não deve chamar código gerenciado ou fazer com que uma alocação de memória gerenciada de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="c9363-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9363-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9363-122">Requirements</span></span>  
 <span data-ttu-id="c9363-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9363-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9363-124">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c9363-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c9363-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9363-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9363-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9363-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9363-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9363-127">See also</span></span>

- [<span data-ttu-id="c9363-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="c9363-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="c9363-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="c9363-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="c9363-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="c9363-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="c9363-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9363-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="c9363-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9363-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="c9363-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="c9363-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="c9363-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9363-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="c9363-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="c9363-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="c9363-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="c9363-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="c9363-137">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="c9363-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
