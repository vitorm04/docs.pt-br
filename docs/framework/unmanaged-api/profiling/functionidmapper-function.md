---
title: Função FunctionIDMapper
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2de19252b5c978fef38124636e4098ae5ece1b0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097932"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="35e19-102">Função FunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="35e19-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="35e19-103">Notifica o criador de perfil que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usado na [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), e [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="35e19-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> `FunctionIDMapper` <span data-ttu-id="35e19-104">também permite que o criador de perfil indicar se deseja receber retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="35e19-104">also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35e19-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35e19-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35e19-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35e19-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="35e19-107">[in] O identificador de função a ser remapeado.</span><span class="sxs-lookup"><span data-stu-id="35e19-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="35e19-108">[out] Um ponteiro para um valor que o criador de perfil define como `true` se desejar receber `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` retornos de chamada; caso contrário, ele define esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="35e19-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35e19-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="35e19-109">Return Value</span></span>  
 <span data-ttu-id="35e19-110">O criador de perfil retorna um valor que o mecanismo de execução usa como um identificador de função alternativa.</span><span class="sxs-lookup"><span data-stu-id="35e19-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="35e19-111">O valor de retorno não pode ser nulo, a menos que `false` é retornado no `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="35e19-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="35e19-112">Caso contrário, um valor de retorno nulo produzirá resultados imprevisíveis, incluindo, possivelmente, a interrupção do processo.</span><span class="sxs-lookup"><span data-stu-id="35e19-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35e19-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="35e19-113">Remarks</span></span>  
 <span data-ttu-id="35e19-114">O `FunctionIDMapper` função é um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="35e19-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="35e19-115">Ela é implementada pelo criador de perfil para remapear um ID de função para outro identificador que é mais útil para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="35e19-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="35e19-116">O `FunctionIDMapper` retorna a ID alternativa a ser usado para qualquer função determinada.</span><span class="sxs-lookup"><span data-stu-id="35e19-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="35e19-117">O mecanismo de execução, em seguida, honra a solicitação do criador de perfil, passando essa ID alternativa, a ID da função tradicional, além de volta para o criador de perfil na `clientData` parâmetro do `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` ganchos para identificar a função para o qual o gancho está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="35e19-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="35e19-118">Você pode usar o [ICorProfilerInfo:: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) método para especificar a implementação do `FunctionIDMapper` função.</span><span class="sxs-lookup"><span data-stu-id="35e19-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="35e19-119">Você pode chamar o `ICorProfilerInfo::SetFunctionIDMapper` método apenas uma vez e podemos recomendar que você faça isso na [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="35e19-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="35e19-120">Por padrão, supõe-se que um criador de perfil que define o sinalizador COR_PRF_MONITOR_ENTERLEAVE usando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), e que define os ganchos via [ICorProfilerInfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), deve receber os `FunctionEnter2`, `FunctionLeave2`, e `FunctionTailcall2` retornos de chamada para cada função.</span><span class="sxs-lookup"><span data-stu-id="35e19-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="35e19-121">No entanto, os criadores de perfil podem implementar `FunctionIDMapper` para evitar seletivamente receber esses retornos de chamada para determinadas funções, definindo `pbHookFunction` para `false`.</span><span class="sxs-lookup"><span data-stu-id="35e19-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="35e19-122">Criadores de perfil devem ser tolerante a falhas de casos em que vários threads de um aplicativo analisado estiver chamando a método ou a função mesma simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="35e19-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="35e19-123">Nesses casos, o criador de perfil pode receber vários `FunctionIDMapper` retornos de chamada para o mesmo `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="35e19-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="35e19-124">O criador de perfil deve ser determinada retornar os mesmos valores desse retorno de chamada quando ele é chamado várias vezes com o mesmo `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="35e19-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35e19-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35e19-125">Requirements</span></span>  
 <span data-ttu-id="35e19-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35e19-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35e19-127">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="35e19-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="35e19-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35e19-128">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="35e19-129">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="35e19-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35e19-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35e19-130">See also</span></span>

- [<span data-ttu-id="35e19-131">Método SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="35e19-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="35e19-132">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="35e19-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [<span data-ttu-id="35e19-133">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="35e19-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="35e19-134">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="35e19-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="35e19-135">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="35e19-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="35e19-136">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="35e19-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
