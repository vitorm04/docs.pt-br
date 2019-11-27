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
ms.openlocfilehash: f4deec3e2b49b5cd6a924af8024e775c5c549f97
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440852"
---
# <a name="functionenter2-function"></a><span data-ttu-id="69de8-102">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="69de8-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="69de8-103">Notifica o criador de perfil que o controle está sendo passado para uma função e fornece informações sobre o quadro de pilha e os argumentos de função.</span><span class="sxs-lookup"><span data-stu-id="69de8-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="69de8-104">Essa função substitui a função [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="69de8-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69de8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69de8-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69de8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69de8-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="69de8-107">no O identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="69de8-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="69de8-108">no O identificador da função remapeada, que o criador de perfil especificou anteriormente usando a função [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) .</span><span class="sxs-lookup"><span data-stu-id="69de8-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="69de8-109">no Um valor `COR_PRF_FRAME_INFO` que aponta para informações sobre o registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="69de8-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="69de8-110">O criador de perfil deve tratar isso como um identificador opaco que pode ser passado de volta para o mecanismo de execução no método [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="69de8-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="69de8-111">no Um ponteiro para uma estrutura de [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) que especifica os locais na memória dos argumentos da função.</span><span class="sxs-lookup"><span data-stu-id="69de8-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="69de8-112">Para acessar informações de argumento, o sinalizador de `COR_PRF_ENABLE_FUNCTION_ARGS` deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="69de8-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="69de8-113">O criador de perfil pode usar o método [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.</span><span class="sxs-lookup"><span data-stu-id="69de8-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69de8-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="69de8-114">Remarks</span></span>  
 <span data-ttu-id="69de8-115">Os valores dos parâmetros `func` e `argumentInfo` não são válidos depois que a função `FunctionEnter2` retorna, pois os valores podem ser alterados ou destruídos.</span><span class="sxs-lookup"><span data-stu-id="69de8-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="69de8-116">A função `FunctionEnter2` é um retorno de chamada; Você deve implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="69de8-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="69de8-117">A implementação deve usar o atributo de classe de armazenamento `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="69de8-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="69de8-118">O mecanismo de execução não salva nenhum registro antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="69de8-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="69de8-119">Na entrada, você deve salvar todos os registros que usar, incluindo aqueles na FPU (unidade de ponto flutuante).</span><span class="sxs-lookup"><span data-stu-id="69de8-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="69de8-120">Ao sair, você deve restaurar a pilha removendo todos os parâmetros que foram enviados por Push por seu chamador.</span><span class="sxs-lookup"><span data-stu-id="69de8-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="69de8-121">A implementação de `FunctionEnter2` não deve bloquear, pois atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="69de8-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="69de8-122">A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado amigável de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="69de8-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="69de8-123">Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até que `FunctionEnter2` retorne.</span><span class="sxs-lookup"><span data-stu-id="69de8-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="69de8-124">Além disso, a função `FunctionEnter2` não deve chamar um código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="69de8-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69de8-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69de8-125">Requirements</span></span>  
 <span data-ttu-id="69de8-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69de8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69de8-127">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="69de8-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="69de8-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69de8-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69de8-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69de8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69de8-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69de8-130">See also</span></span>

- [<span data-ttu-id="69de8-131">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="69de8-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="69de8-132">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="69de8-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="69de8-133">Método SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="69de8-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="69de8-134">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="69de8-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
