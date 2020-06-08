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
ms.openlocfilehash: 235bae64fe5e6a534f2a650050c6c9ad4aa8fe84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500618"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="7701c-102">Função FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7701c-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="7701c-103">Notifica o criador de perfil que o controle está sendo retornado de uma função e fornece um identificador que pode ser passado para o [método ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) para recuperar o quadro de pilha e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="7701c-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7701c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7701c-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7701c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7701c-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="7701c-106">\[in] o identificador da função a partir da qual o controle é retornado.</span><span class="sxs-lookup"><span data-stu-id="7701c-106">\[in] The identifier of the function from which control is returned.</span></span>

- `eltInfo`

  <span data-ttu-id="7701c-107">\[in] um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="7701c-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7701c-108">Esse identificador é válido somente durante o retorno de chamada ao qual é passado.</span><span class="sxs-lookup"><span data-stu-id="7701c-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="7701c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7701c-109">Remarks</span></span>  
 <span data-ttu-id="7701c-110">O `FunctionLeave3WithInfo` método de retorno de chamada notifica o criador de perfil conforme as funções são chamadas e permite que o criador de perfil Use o [método ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) para inspecionar o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="7701c-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="7701c-111">Para acessar informações de valor de retorno, o `COR_PRF_ENABLE_FUNCTION_RETVAL` sinalizador precisa ser definido.</span><span class="sxs-lookup"><span data-stu-id="7701c-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="7701c-112">O criador de perfil pode usar o [método ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, usar o [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar sua implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="7701c-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="7701c-113">A `FunctionLeave3WithInfo` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="7701c-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="7701c-114">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="7701c-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="7701c-115">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="7701c-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="7701c-116">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="7701c-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="7701c-117">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="7701c-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7701c-118">A implementação de `FunctionLeave3WithInfo` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7701c-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="7701c-119">A implementação não deve tentar uma coleta de lixo, pois a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7701c-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7701c-120">Se for feita uma tentativa de coleta de lixo, o tempo de execução será bloqueado até o `FunctionLeave3WithInfo` retorno.</span><span class="sxs-lookup"><span data-stu-id="7701c-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="7701c-121">A `FunctionLeave3WithInfo` função não deve chamar código gerenciado ou causar uma alocação de memória gerenciada de qualquer forma.</span><span class="sxs-lookup"><span data-stu-id="7701c-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7701c-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7701c-122">Requirements</span></span>  
 <span data-ttu-id="7701c-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7701c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7701c-124">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="7701c-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7701c-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7701c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7701c-126">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7701c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7701c-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7701c-127">See also</span></span>

- [<span data-ttu-id="7701c-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="7701c-128">GetFunctionLeave3Info</span></span>](icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="7701c-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="7701c-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="7701c-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="7701c-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="7701c-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="7701c-131">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="7701c-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7701c-132">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="7701c-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7701c-133">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="7701c-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="7701c-134">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="7701c-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7701c-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="7701c-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="7701c-136">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="7701c-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="7701c-137">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="7701c-138">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="7701c-138">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
