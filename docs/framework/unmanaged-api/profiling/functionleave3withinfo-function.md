---
title: Função FunctionLeave3WithInfo
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: a62f402fbfae6188ab0423ea7a55a4dfc6cb4112
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427406"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="c5e91-102">Função FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c5e91-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="c5e91-103">Notifica o criador de perfil que o controle está sendo retornado de uma função e fornece um identificador que pode ser passado para o [método ICorProfilerInfo3:: GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) para recuperar o quadro de pilha e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c5e91-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5e91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5e91-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5e91-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c5e91-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="c5e91-106">no O identificador da função da qual o controle é retornado.</span><span class="sxs-lookup"><span data-stu-id="c5e91-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="c5e91-107">no Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="c5e91-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="c5e91-108">Esse identificador é válido somente durante o retorno de chamada ao qual é passado.</span><span class="sxs-lookup"><span data-stu-id="c5e91-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5e91-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5e91-109">Remarks</span></span>  
 <span data-ttu-id="c5e91-110">O método de retorno de chamada `FunctionLeave3WithInfo` notifica o criador de perfil conforme as funções são chamadas e permite que o criador de perfil Use o [método ICorProfilerInfo3:: GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) para inspecionar o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c5e91-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="c5e91-111">Para acessar informações de valor de retorno, o sinalizador de `COR_PRF_ENABLE_FUNCTION_RETVAL` precisa ser definido.</span><span class="sxs-lookup"><span data-stu-id="c5e91-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="c5e91-112">O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="c5e91-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="c5e91-113">A função `FunctionLeave3WithInfo` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="c5e91-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="c5e91-114">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="c5e91-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="c5e91-115">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="c5e91-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c5e91-116">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="c5e91-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c5e91-117">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="c5e91-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c5e91-118">A implementação de `FunctionLeave3WithInfo` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c5e91-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="c5e91-119">A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c5e91-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c5e91-120">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionLeave3WithInfo` retorne.</span><span class="sxs-lookup"><span data-stu-id="c5e91-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="c5e91-121">A função `FunctionLeave3WithInfo` não deve chamar um código gerenciado ou causar uma alocação de memória gerenciada de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="c5e91-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5e91-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5e91-122">Requirements</span></span>  
 <span data-ttu-id="c5e91-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5e91-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5e91-124">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="c5e91-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c5e91-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5e91-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5e91-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5e91-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e91-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5e91-127">See also</span></span>

- [<span data-ttu-id="c5e91-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="c5e91-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="c5e91-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="c5e91-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="c5e91-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="c5e91-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="c5e91-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="c5e91-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="c5e91-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c5e91-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="c5e91-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c5e91-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="c5e91-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="c5e91-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="c5e91-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c5e91-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="c5e91-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="c5e91-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="c5e91-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="c5e91-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="c5e91-138">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="c5e91-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
