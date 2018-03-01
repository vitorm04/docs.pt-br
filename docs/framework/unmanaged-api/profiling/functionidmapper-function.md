---
title: "Função FunctionIDMapper"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24e48ecb551a5faacc7da94b857b2e260f5aeca0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="functionidmapper-function"></a><span data-ttu-id="d6a04-102">Função FunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d6a04-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="d6a04-103">Notifica o criador de perfil que o identificador especificado de uma função pode ser mapeado novamente para uma ID alternativa a ser usado no [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), e [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="d6a04-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="d6a04-104">`FunctionIDMapper`também permite que o criador de perfil indicar se deseja receber retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="d6a04-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6a04-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6a04-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6a04-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6a04-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="d6a04-107">[in] O identificador de função a ser remapeados.</span><span class="sxs-lookup"><span data-stu-id="d6a04-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="d6a04-108">[out] Um ponteiro para um valor que define o criador de perfil para `true` se deseja receber `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` retornos de chamada; caso contrário, ele define esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="d6a04-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6a04-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d6a04-109">Return Value</span></span>  
 <span data-ttu-id="d6a04-110">O criador de perfil retorna um valor que usa o mecanismo de execução como um identificador de função alternativos.</span><span class="sxs-lookup"><span data-stu-id="d6a04-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="d6a04-111">O valor de retorno não pode ser nulo, a menos que `false` é retornado no `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="d6a04-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="d6a04-112">Caso contrário, um valor de retorno nulo produzirá resultados imprevisíveis, incluindo possivelmente interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="d6a04-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6a04-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6a04-113">Remarks</span></span>  
 <span data-ttu-id="d6a04-114">O `FunctionIDMapper` função é um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d6a04-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="d6a04-115">Ele é implementado pelo criador de perfil para remapear uma ID de função para outro identificador que é mais útil para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="d6a04-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="d6a04-116">O `FunctionIDMapper` retorna a ID alternativa a ser usado para qualquer função fornecida.</span><span class="sxs-lookup"><span data-stu-id="d6a04-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="d6a04-117">O mecanismo de execução, em seguida, leva em conta a solicitação do criador de perfil, passando essa ID alternativo, além da ID de função tradicional, volta para o criador de perfil no `clientData` parâmetro o `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` ganchos para identificar a função para a qual o gancho está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="d6a04-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="d6a04-118">Você pode usar o [: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) método para especificar a implementação de `FunctionIDMapper` função.</span><span class="sxs-lookup"><span data-stu-id="d6a04-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="d6a04-119">Você pode chamar o `ICorProfilerInfo::SetFunctionIDMapper` método apenas uma vez e é recomendável que você faça isso no [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d6a04-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="d6a04-120">Por padrão, supõe-se que um criador de perfil que define o sinalizador COR_PRF_MONITOR_ENTERLEAVE usando [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), e que define ganchos via [Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), deve receber o `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` retornos de chamada para cada função.</span><span class="sxs-lookup"><span data-stu-id="d6a04-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="d6a04-121">No entanto, os criadores de perfil podem implementar `FunctionIDMapper` evitar seletivamente a receber esses retornos de chamada para determinadas funções definindo `pbHookFunction` para `false`.</span><span class="sxs-lookup"><span data-stu-id="d6a04-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="d6a04-122">Criadores de perfil devem ser tolerante a falhas de casos em que vários threads de um aplicativo de perfil estão chamando a método/função mesmo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="d6a04-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="d6a04-123">Nesses casos, o criador de perfil pode receber vários `FunctionIDMapper` retornos de chamada para o mesmo `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="d6a04-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="d6a04-124">O criador de perfil deve ser determinada retornar os mesmos valores desse retorno de chamada quando ele for chamado várias vezes com o mesmo `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="d6a04-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6a04-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6a04-125">Requirements</span></span>  
 <span data-ttu-id="d6a04-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6a04-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6a04-127">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="d6a04-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d6a04-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6a04-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6a04-129">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6a04-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a04-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6a04-130">See Also</span></span>  
 [<span data-ttu-id="d6a04-131">Método SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d6a04-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="d6a04-132">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="d6a04-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [<span data-ttu-id="d6a04-133">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="d6a04-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="d6a04-134">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="d6a04-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="d6a04-135">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="d6a04-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="d6a04-136">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="d6a04-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
