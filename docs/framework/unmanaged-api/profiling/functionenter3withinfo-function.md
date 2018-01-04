---
title: "Função FunctionEnter3WithInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3WithInfo
api_location: mscorwks.cll
api_type: COM
f1_keywords: FunctionEnter3WithInfo
helpviewer_keywords: FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 848ef06f73aa0cce5d6991a7a59a8ce51ab1745a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="8d4ce-102">Função FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="8d4ce-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="8d4ce-103">Notifica o criador de perfil que o controle está sendo passado para uma função e fornece um identificador que pode ser passado para o [ICorProfilerInfo3::GetFunctionEnter3Info método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) para recuperar os argumentos de quadro e função de pilha.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d4ce-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d4ce-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d4ce-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="8d4ce-106">[in] O identificador da função à qual o controle é passado.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="8d4ce-107">[in] Um identificador opaco que representa informações sobre um determinado registro de ativação.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="8d4ce-108">Esse identificador é válido somente durante o retorno de chamada para o qual ele é passado.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d4ce-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d4ce-109">Remarks</span></span>  
 <span data-ttu-id="8d4ce-110">O `FunctionEnter3WithInfo` método de retorno de chamada notifica o criador de perfil como funções são chamadas e permite que o criador de perfil usar o [ICorProfilerInfo3::GetFunctionEnter3Info método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) para inspecionar os valores de argumento.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="8d4ce-111">Para acessar informações de argumento, o `COR_PRF_ENABLE_FUNCTION_ARGS` sinalizador deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="8d4ce-112">O criador de perfil pode usar o [: SetEventMask método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento e, em seguida, use o [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar seu implementação dessa função.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="8d4ce-113">O `FunctionEnter3WithInfo` função é um retorno de chamada; você deve implementá-la.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="8d4ce-114">A implementação deve usar o `__declspec(naked)` atributo de classe de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="8d4ce-115">O mecanismo de execução não salva quaisquer registros antes de chamar essa função.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="8d4ce-116">Na entrada, você deve salvar todos os registros que você usa, incluindo aqueles na unidade de ponto flutuante (FPU).</span><span class="sxs-lookup"><span data-stu-id="8d4ce-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="8d4ce-117">Na saída, você deve restaurar a pilha por retirar desativar todos os parâmetros que foram empurrados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="8d4ce-118">A implementação de `FunctionEnter3WithInfo` não devem bloquear, porque ele atrasará a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="8d4ce-119">A implementação não deve tentar uma coleta de lixo, porque a pilha pode não estar em um estado de amigável para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="8d4ce-120">Se você tentar uma coleta de lixo, tempo de execução será bloqueado até que `FunctionEnter3WithInfo` retorna.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="8d4ce-121">O `FunctionEnter3WithInfo` função não deve chamar código gerenciado ou fazer com que uma alocação de memória gerenciada de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="8d4ce-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d4ce-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d4ce-122">Requirements</span></span>  
 <span data-ttu-id="8d4ce-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d4ce-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d4ce-124">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="8d4ce-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8d4ce-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d4ce-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d4ce-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d4ce-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4ce-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d4ce-127">See Also</span></span>  
 [<span data-ttu-id="8d4ce-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="8d4ce-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [<span data-ttu-id="8d4ce-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="8d4ce-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="8d4ce-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="8d4ce-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="8d4ce-131">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="8d4ce-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
