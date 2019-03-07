---
title: Função FunctionLeave2
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9985b5a5547097c0474eb3a5797388d1444083e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471576"
---
# <a name="functionleave2-function"></a><span data-ttu-id="3348c-102">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="3348c-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="3348c-103">Notifica o criador de perfil que uma função está prestes a retornar ao chamador e fornece informações sobre o stack frame e função de valor retornado.</span><span class="sxs-lookup"><span data-stu-id="3348c-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3348c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3348c-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3348c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3348c-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="3348c-106">[in] O identificador da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="3348c-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="3348c-107">[in] O identificador de função remapeada, que o criador de perfil especificado anteriormente por meio de [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="3348c-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="3348c-108">[in] Um `COR_PRF_FRAME_INFO` valor aponta para obter informações sobre o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="3348c-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="3348c-109">O criador de perfil deve tratar isso como um identificador opaco que pode ser passado para o mecanismo de execução no [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="3348c-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="3348c-110">[in] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) estrutura que especifica o local da memória do valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="3348c-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="3348c-111">Para acessar informações de valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="3348c-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="3348c-112">O criador de perfil pode usar o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="3348c-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3348c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3348c-113">Remarks</span></span>  
 <span data-ttu-id="3348c-114">Os valores da `func` e `retvalRange` parâmetros não são válidos após o `FunctionLeave2` função retorna porque os valores podem ser alterados ou ser destruídos.</span><span class="sxs-lookup"><span data-stu-id="3348c-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="3348c-115">O `FunctionLeave2` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="3348c-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="3348c-116">A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="3348c-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3348c-117">O mecanismo de execução não salva qualquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="3348c-117">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="3348c-118">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="3348c-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="3348c-119">Na saída, você deve restaurar a pilha de popping desativar todos os parâmetros que foram enviados por push ao seu chamador.</span><span class="sxs-lookup"><span data-stu-id="3348c-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3348c-120">A implementação de `FunctionLeave2` não devem bloquear porque isso atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3348c-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3348c-121">A implementação não deve tentar uma coleta de lixo, porque a pilha não pode estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3348c-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3348c-122">Se você tentar uma coleta de lixo, o tempo de execução será bloqueado até que `FunctionLeave2` retorna.</span><span class="sxs-lookup"><span data-stu-id="3348c-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="3348c-123">Além disso, o `FunctionLeave2` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="3348c-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3348c-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3348c-124">Requirements</span></span>  
 <span data-ttu-id="3348c-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3348c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3348c-126">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3348c-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3348c-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3348c-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3348c-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3348c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3348c-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3348c-129">See also</span></span>
- [<span data-ttu-id="3348c-130">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="3348c-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="3348c-131">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="3348c-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="3348c-132">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="3348c-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="3348c-133">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="3348c-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
