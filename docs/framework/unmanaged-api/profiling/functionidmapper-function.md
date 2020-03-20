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
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175168"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="9a971-102">Função FunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="9a971-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="9a971-103">Notifica o profiler de que o identificador dado de uma função pode ser remapped para um ID alternativo a ser usado nos [retornos de functionEnter2,](functionenter2-function.md) [FunctionLeave2](functionleave2-function.md)e [FunctionTailcall2](functiontailcall2-function.md) para essa função.</span><span class="sxs-lookup"><span data-stu-id="9a971-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="9a971-104">`FunctionIDMapper`também permite que o profiler indique se ele quer receber retornos para essa função.</span><span class="sxs-lookup"><span data-stu-id="9a971-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a971-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a971-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a971-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a971-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="9a971-107">\[em] O identificador de função a ser remapeado.</span><span class="sxs-lookup"><span data-stu-id="9a971-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="9a971-108">\[fora] Um ponteiro para um valor `true` que o profiler `FunctionLeave2`define `FunctionTailcall2` para se ele quiser receber `FunctionEnter2`, e retornos de chamada; caso contrário, ele define `false`esse valor para .</span><span class="sxs-lookup"><span data-stu-id="9a971-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="9a971-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9a971-109">Return Value</span></span>  
 <span data-ttu-id="9a971-110">O profiler retorna um valor que o mecanismo de execução usa como um identificador de função alternativa.</span><span class="sxs-lookup"><span data-stu-id="9a971-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="9a971-111">O valor de devolução não pode ser nulo a menos que `false` seja devolvido em `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="9a971-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="9a971-112">Caso contrário, um valor de retorno nulo produzirá resultados imprevisíveis, incluindo possivelmente interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="9a971-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a971-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a971-113">Remarks</span></span>  
 <span data-ttu-id="9a971-114">A `FunctionIDMapper` função é um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="9a971-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="9a971-115">Ele é implementado pelo profiler para remapear um ID de função para algum outro identificador que seja mais útil para o profiler.</span><span class="sxs-lookup"><span data-stu-id="9a971-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="9a971-116">O `FunctionIDMapper` retorno do ID alternativo a ser usado para qualquer função.</span><span class="sxs-lookup"><span data-stu-id="9a971-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="9a971-117">O motor de execução então honra o pedido do profiler, passando este ID alternativo, além `clientData` do ID `FunctionEnter2` `FunctionLeave2`de `FunctionTailcall2` função tradicional, de volta ao profiler no parâmetro do , e ganchos, para identificar a função para a qual o gancho está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="9a971-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="9a971-118">Você pode usar o método [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) `FunctionIDMapper` para especificar a implementação da função.</span><span class="sxs-lookup"><span data-stu-id="9a971-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="9a971-119">Você pode `ICorProfilerInfo::SetFunctionIDMapper` chamar o método apenas uma vez, e recomendamos que você o faça no [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="9a971-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="9a971-120">Por padrão, supõe-se que um profiler que define o COR_PRF_MONITOR_ENTERLEAVE flag usando [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), e que define ganchos via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) `FunctionLeave2`ou `FunctionTailcall2` [ICorProfilerInfo2:SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), deve receber os `FunctionEnter2`, e retornos de chamadas para cada função.</span><span class="sxs-lookup"><span data-stu-id="9a971-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="9a971-121">No entanto, os `FunctionIDMapper` profilers podem implementar para evitar seletivamente `pbHookFunction` `false`receber esses retornos de chamadas para determinadas funções, configurando para .</span><span class="sxs-lookup"><span data-stu-id="9a971-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="9a971-122">Os profilers devem ser tolerantes aos casos em que vários segmentos de um aplicativo perfilado estão chamando o mesmo método/função simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="9a971-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="9a971-123">Nesses casos, o profiler `FunctionIDMapper` pode receber vários `FunctionID`retornos de chamada para o mesmo .</span><span class="sxs-lookup"><span data-stu-id="9a971-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="9a971-124">O profiler deve ter certeza de retornar os mesmos valores a `FunctionID`partir deste retorno de chamada quando for chamado várias vezes com o mesmo .</span><span class="sxs-lookup"><span data-stu-id="9a971-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a971-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a971-125">Requirements</span></span>  
 <span data-ttu-id="9a971-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a971-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a971-127">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="9a971-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9a971-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a971-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a971-129">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a971-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a971-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a971-130">See also</span></span>

- [<span data-ttu-id="9a971-131">Método SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="9a971-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="9a971-132">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="9a971-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="9a971-133">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="9a971-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="9a971-134">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="9a971-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="9a971-135">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="9a971-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="9a971-136">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="9a971-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
