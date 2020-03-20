---
title: Função FunctionEnter2
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177053"
---
# <a name="functionenter2-function"></a><span data-ttu-id="542f7-102">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="542f7-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="542f7-103">Notifica o profiler de que o controle está sendo passado para uma função e fornece informações sobre o quadro de pilha e argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="542f7-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="542f7-104">Esta função substitui a função [FunctionEnter.](functionenter-function.md)</span><span class="sxs-lookup"><span data-stu-id="542f7-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="542f7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="542f7-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="542f7-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="542f7-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="542f7-107">\[em] O identificador da função para a qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="542f7-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="542f7-108">\[em] O identificador de função remapped, que o profiler anteriormente especificado usando a função [FunctionIDMapper.](functionidmapper-function.md)</span><span class="sxs-lookup"><span data-stu-id="542f7-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="542f7-109">\[em] `COR_PRF_FRAME_INFO` Um valor que aponta para informações sobre o quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="542f7-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="542f7-110">O profiler deve tratá-lo como uma alça opaca que pode ser passada de volta para o mecanismo de execução no método [ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)</span><span class="sxs-lookup"><span data-stu-id="542f7-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="542f7-111">\[em] Um ponteiro para uma estrutura [de COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) que especifica os locais na memória dos argumentos da função.</span><span class="sxs-lookup"><span data-stu-id="542f7-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="542f7-112">Para acessar as informações `COR_PRF_ENABLE_FUNCTION_ARGS` do argumento, a bandeira deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="542f7-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="542f7-113">O profiler pode usar o método [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="542f7-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="542f7-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="542f7-114">Remarks</span></span>  
 <span data-ttu-id="542f7-115">Os valores `func` `argumentInfo` dos parâmetros e `FunctionEnter2` dos parâmetros não são válidos após o retorno da função porque os valores podem mudar ou ser destruídos.</span><span class="sxs-lookup"><span data-stu-id="542f7-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="542f7-116">A `FunctionEnter2` função é um retorno de chamada; você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="542f7-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="542f7-117">A implementação `__declspec`deve`naked`usar o atributo () classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="542f7-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="542f7-118">O motor de execução não salva nenhum registro antes de chamar esta função.</span><span class="sxs-lookup"><span data-stu-id="542f7-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="542f7-119">Na entrada, você deve salvar todos os registros que você usa, incluindo os da unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="542f7-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="542f7-120">Na saída, você deve restaurar a pilha, atirando todos os parâmetros que foram empurrados pelo seu interlocutor.</span><span class="sxs-lookup"><span data-stu-id="542f7-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="542f7-121">A implantação `FunctionEnter2` não deve bloquear porque vai atrasar a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="542f7-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="542f7-122">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado favorável à coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="542f7-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="542f7-123">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até `FunctionEnter2` o retorno.</span><span class="sxs-lookup"><span data-stu-id="542f7-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="542f7-124">Além disso, a `FunctionEnter2` função não deve chamar para código gerenciado ou de qualquer forma causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="542f7-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="542f7-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="542f7-125">Requirements</span></span>  
 <span data-ttu-id="542f7-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="542f7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="542f7-127">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="542f7-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="542f7-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="542f7-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="542f7-129">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="542f7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542f7-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="542f7-130">See also</span></span>

- [<span data-ttu-id="542f7-131">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="542f7-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="542f7-132">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="542f7-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="542f7-133">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="542f7-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="542f7-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="542f7-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
