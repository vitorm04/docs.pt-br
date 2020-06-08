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
ms.openlocfilehash: a2a3d58e0631fceab96c32f9d86fef25973fed84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500657"
---
# <a name="functionleave2-function"></a><span data-ttu-id="c016a-102">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="c016a-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="c016a-103">Notifica o criador de perfil de que uma função está prestes a retornar ao chamador e fornece informações sobre o quadro de pilha e o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="c016a-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c016a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c016a-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c016a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c016a-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="c016a-106">\[in] o identificador da função que está retornando.</span><span class="sxs-lookup"><span data-stu-id="c016a-106">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="c016a-107">\[in] o identificador da função remapeada, que o criador de perfil especificou anteriormente por meio da função [FunctionIDMapper](functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c016a-107">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="c016a-108">\[in] um `COR_PRF_FRAME_INFO` valor que aponta para informações sobre o registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="c016a-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="c016a-109">O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no método [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c016a-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="c016a-110">\[in] um ponteiro para uma estrutura de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) que especifica o local da memória do valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="c016a-110">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="c016a-111">Para acessar informações de valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="c016a-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="c016a-112">O criador de perfil pode usar o método [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="c016a-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="c016a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c016a-113">Remarks</span></span>  
 <span data-ttu-id="c016a-114">Os valores dos `func` parâmetros e `retvalRange` não são válidos após a `FunctionLeave2` função retornar, pois os valores podem ser alterados ou destruídos.</span><span class="sxs-lookup"><span data-stu-id="c016a-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="c016a-115">A `FunctionLeave2` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="c016a-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="c016a-116">A implementação deve usar o `__declspec` `naked` atributo de classe de armazenamento ().</span><span class="sxs-lookup"><span data-stu-id="c016a-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="c016a-117">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="c016a-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c016a-118">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="c016a-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c016a-119">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="c016a-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c016a-120">A implementação de `FunctionLeave2` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c016a-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="c016a-121">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c016a-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c016a-122">Se for feita uma tentativa de coleta de lixo, o tempo de execução será bloqueado até o `FunctionLeave2` retorno.</span><span class="sxs-lookup"><span data-stu-id="c016a-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="c016a-123">Além disso, a `FunctionLeave2` função não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="c016a-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c016a-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c016a-124">Requirements</span></span>  
 <span data-ttu-id="c016a-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c016a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c016a-126">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="c016a-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c016a-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c016a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c016a-128">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c016a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c016a-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="c016a-129">See also</span></span>

- [<span data-ttu-id="c016a-130">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="c016a-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="c016a-131">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="c016a-131">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="c016a-132">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="c016a-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="c016a-133">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="c016a-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
