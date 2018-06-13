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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd87709a9e8b0e943bcf89aa528872d465526218
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454273"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="9b512-102">Função FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9b512-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="9b512-103">Notifica o criador de perfil que o controle está sendo retornado de uma função e fornece um identificador que pode ser passado para o [ICorProfilerInfo3::GetFunctionLeave3Info método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) para recuperar o quadro de pilhas e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="9b512-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b512-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b512-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b512-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b512-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="9b512-106">[in] O identificador da função da qual o controle é retornado.</span><span class="sxs-lookup"><span data-stu-id="9b512-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="9b512-107">[in] Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="9b512-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="9b512-108">Esse identificador é válido somente durante o retorno de chamada para o qual ele é passado.</span><span class="sxs-lookup"><span data-stu-id="9b512-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b512-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b512-109">Remarks</span></span>  
 <span data-ttu-id="9b512-110">O `FunctionLeave3WithInfo` método de retorno de chamada notifica o criador de perfil como funções são chamadas e permite que o criador de perfil usar o [ICorProfilerInfo3::GetFunctionLeave3Info método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) para inspecionar o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="9b512-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="9b512-111">Para acessar informações do valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="9b512-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="9b512-112">O criador de perfil pode usar o [: SetEventMask método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, use o [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar seu implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="9b512-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="9b512-113">O `FunctionLeave3WithInfo` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="9b512-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="9b512-114">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="9b512-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="9b512-115">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="9b512-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="9b512-116">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="9b512-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="9b512-117">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="9b512-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="9b512-118">A implementação de `FunctionLeave3WithInfo` não devem bloquear, porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9b512-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="9b512-119">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9b512-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="9b512-120">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionLeave3WithInfo` retorna.</span><span class="sxs-lookup"><span data-stu-id="9b512-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="9b512-121">O `FunctionLeave3WithInfo` função não deve chamar código gerenciado ou fazer com que uma alocação de memória gerenciada de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="9b512-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b512-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b512-122">Requirements</span></span>  
 <span data-ttu-id="9b512-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b512-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b512-124">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="9b512-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9b512-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b512-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b512-126">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b512-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b512-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b512-127">See Also</span></span>  
 [<span data-ttu-id="9b512-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="9b512-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)  
 [<span data-ttu-id="9b512-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="9b512-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="9b512-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="9b512-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="9b512-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="9b512-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="9b512-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9b512-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="9b512-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9b512-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="9b512-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="9b512-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="9b512-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="9b512-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="9b512-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="9b512-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="9b512-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="9b512-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="9b512-138">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="9b512-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
