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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 413cde3d0977c1fd6897fc5bd6fa7a3fef00ac02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763343"
---
# <a name="functionenter2-function"></a><span data-ttu-id="e292b-102">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="e292b-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="e292b-103">Notifica o criador de perfil que o controle está sendo passado para uma função e fornece informações sobre a pilha de argumentos de função e de quadro.</span><span class="sxs-lookup"><span data-stu-id="e292b-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="e292b-104">Essa função substitui o [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="e292b-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e292b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e292b-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e292b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e292b-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="e292b-107">[in] O identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="e292b-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="e292b-108">[in] O identificador de função remapeada, que o criador de perfil especificado anteriormente usando o [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="e292b-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="e292b-109">[in] Um `COR_PRF_FRAME_INFO` valor aponta para obter informações sobre o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="e292b-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="e292b-110">O criador de perfil deve tratar isso como um identificador opaco que pode ser passado para o mecanismo de execução no [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e292b-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="e292b-111">[in] Um ponteiro para um [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) estrutura que especifica os locais na memória dos argumentos da função.</span><span class="sxs-lookup"><span data-stu-id="e292b-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="e292b-112">Para acessar informações de argumento, o `COR_PRF_ENABLE_FUNCTION_ARGS` sinalizador deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="e292b-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="e292b-113">O criador de perfil pode usar o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="e292b-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e292b-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="e292b-114">Remarks</span></span>  
 <span data-ttu-id="e292b-115">Os valores da `func` e `argumentInfo` parâmetros não são válidos após o `FunctionEnter2` função retorna porque os valores podem ser alterados ou ser destruídos.</span><span class="sxs-lookup"><span data-stu-id="e292b-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="e292b-116">O `FunctionEnter2` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="e292b-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="e292b-117">A implementação deve usar o `__declspec`(`naked`) atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="e292b-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="e292b-118">O mecanismo de execução não salva qualquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="e292b-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="e292b-119">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="e292b-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="e292b-120">Na saída, você deve restaurar a pilha de popping desativar todos os parâmetros que foram enviados por push ao seu chamador.</span><span class="sxs-lookup"><span data-stu-id="e292b-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="e292b-121">A implementação de `FunctionEnter2` não devem bloquear porque isso atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e292b-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="e292b-122">A implementação não deve tentar uma coleta de lixo, porque a pilha não pode estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e292b-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="e292b-123">Se você tentar uma coleta de lixo, o tempo de execução será bloqueado até que `FunctionEnter2` retorna.</span><span class="sxs-lookup"><span data-stu-id="e292b-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="e292b-124">Além disso, o `FunctionEnter2` função não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e292b-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e292b-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e292b-125">Requirements</span></span>  
 <span data-ttu-id="e292b-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e292b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e292b-127">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="e292b-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e292b-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e292b-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e292b-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e292b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e292b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e292b-130">See also</span></span>

- [<span data-ttu-id="e292b-131">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="e292b-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="e292b-132">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="e292b-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="e292b-133">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="e292b-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="e292b-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="e292b-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
