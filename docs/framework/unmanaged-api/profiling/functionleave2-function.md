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
ms.openlocfilehash: e40687f7f843dc563801bb01b503d2ae94a094fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446021"
---
# <a name="functionleave2-function"></a><span data-ttu-id="15b89-102">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="15b89-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="15b89-103">Notifica o criador de perfil de que uma função está prestes a retornar ao chamador e fornece informações sobre o quadro de pilha e o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="15b89-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15b89-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15b89-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15b89-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="15b89-106">no O identificador da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="15b89-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="15b89-107">no O identificador da função remapeada, que o criador de perfil especificou anteriormente por meio da função [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="15b89-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="15b89-108">no Um valor `COR_PRF_FRAME_INFO` que aponta para informações sobre o registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="15b89-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="15b89-109">O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no método [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="15b89-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="15b89-110">no Um ponteiro para uma estrutura de [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) que especifica o local da memória do valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="15b89-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="15b89-111">Para acessar informações de valor de retorno, o sinalizador de `COR_PRF_ENABLE_FUNCTION_RETVAL` deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="15b89-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="15b89-112">O criador de perfil pode usar o método [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="15b89-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15b89-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="15b89-113">Remarks</span></span>  
 <span data-ttu-id="15b89-114">Os valores dos parâmetros `func` e `retvalRange` não são válidos depois que a função `FunctionLeave2` retorna, pois os valores podem ser alterados ou destruídos.</span><span class="sxs-lookup"><span data-stu-id="15b89-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="15b89-115">A função `FunctionLeave2` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="15b89-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="15b89-116">A implementação deve usar o atributo de classe de armazenamento `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="15b89-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="15b89-117">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="15b89-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="15b89-118">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="15b89-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="15b89-119">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="15b89-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="15b89-120">A implementação de `FunctionLeave2` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="15b89-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="15b89-121">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="15b89-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="15b89-122">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionLeave2` retorne.</span><span class="sxs-lookup"><span data-stu-id="15b89-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="15b89-123">Além disso, a função `FunctionLeave2` não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="15b89-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15b89-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15b89-124">Requirements</span></span>  
 <span data-ttu-id="15b89-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15b89-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15b89-126">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="15b89-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="15b89-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15b89-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15b89-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15b89-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b89-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15b89-129">See also</span></span>

- [<span data-ttu-id="15b89-130">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="15b89-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="15b89-131">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="15b89-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="15b89-132">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="15b89-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="15b89-133">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="15b89-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
