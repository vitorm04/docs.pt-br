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
ms.openlocfilehash: 202aed64de78675c79f998afb4483e0d19b811de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445963"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="381d3-102">Função FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="381d3-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="381d3-103">Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função e fornece um identificador que pode ser passado para o [método ICorProfilerInfo3:: GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) para recuperar o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="381d3-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="381d3-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="381d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="381d3-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="381d3-106">no O identificador da função atualmente em execução que está prestes a fazer uma chamada final.</span><span class="sxs-lookup"><span data-stu-id="381d3-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="381d3-107">no Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="381d3-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="381d3-108">Esse identificador é válido somente durante o retorno de chamada ao qual é passado.</span><span class="sxs-lookup"><span data-stu-id="381d3-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="381d3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="381d3-109">Remarks</span></span>  
 <span data-ttu-id="381d3-110">O método de retorno de chamada `FunctionTailcall3WithInfo` notifica o criador de perfil conforme as funções são chamadas e permite que o criador de perfil Use o [método ICorProfilerInfo3:: GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) para inspecionar o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="381d3-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="381d3-111">Para acessar as informações do registro de ativação, o sinalizador `COR_PRF_ENABLE_FRAME_INFO` precisa ser definido.</span><span class="sxs-lookup"><span data-stu-id="381d3-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="381d3-112">O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="381d3-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="381d3-113">A função `FunctionTailcall3WithInfo` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="381d3-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="381d3-114">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="381d3-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="381d3-115">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="381d3-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="381d3-116">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="381d3-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="381d3-117">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="381d3-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="381d3-118">A implementação de `FunctionTailcall3WithInfo` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="381d3-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="381d3-119">A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="381d3-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="381d3-120">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionTailcall3WithInfo` retorne.</span><span class="sxs-lookup"><span data-stu-id="381d3-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="381d3-121">Além disso, a função FunctionTailcall3WithInfo não deve chamar um código gerenciado ou causar uma alocação de memória gerenciada de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="381d3-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="381d3-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="381d3-122">Requirements</span></span>  
 <span data-ttu-id="381d3-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="381d3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="381d3-124">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="381d3-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="381d3-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="381d3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="381d3-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="381d3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="381d3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="381d3-127">See also</span></span>

- [<span data-ttu-id="381d3-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="381d3-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="381d3-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="381d3-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="381d3-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="381d3-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="381d3-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="381d3-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="381d3-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="381d3-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="381d3-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="381d3-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="381d3-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="381d3-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="381d3-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="381d3-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="381d3-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="381d3-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="381d3-137">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="381d3-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
