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
ms.openlocfilehash: afc818dfe625bfc329ceb1660539eb119702a90d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500670"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="22220-102">Função FunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="22220-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="22220-103">Notifica o criador de perfil de que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usada nos retornos de chamada [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)e [FunctionTailcall2](functiontailcall2-function.md) para essa função.</span><span class="sxs-lookup"><span data-stu-id="22220-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="22220-104">`FunctionIDMapper`também permite que o criador de perfil indique se deseja receber retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="22220-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22220-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22220-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22220-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22220-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="22220-107">\[no] o identificador de função a ser remapeado.</span><span class="sxs-lookup"><span data-stu-id="22220-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="22220-108">\[out] um ponteiro para um valor que o criador de perfil define `true` se deseja receber `FunctionEnter2` , `FunctionLeave2` e `FunctionTailcall2` retornos de chamada; caso contrário, ele define esse valor como `false` .</span><span class="sxs-lookup"><span data-stu-id="22220-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="22220-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="22220-109">Return Value</span></span>  
 <span data-ttu-id="22220-110">O criador de perfil retorna um valor que o mecanismo de execução usa como um identificador de função alternativo.</span><span class="sxs-lookup"><span data-stu-id="22220-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="22220-111">O valor de retorno não pode ser nulo, a menos que `false` seja retornado em `pbHookFunction` .</span><span class="sxs-lookup"><span data-stu-id="22220-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="22220-112">Caso contrário, um valor de retorno nulo produzirá resultados imprevisíveis, incluindo possivelmente interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="22220-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22220-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="22220-113">Remarks</span></span>  
 <span data-ttu-id="22220-114">A `FunctionIDMapper` função é um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="22220-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="22220-115">Ele é implementado pelo criador de perfil para remapear uma ID de função para algum outro identificador que seja mais útil para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="22220-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="22220-116">O `FunctionIDMapper` retorna a ID alternativa a ser usada para qualquer função especificada.</span><span class="sxs-lookup"><span data-stu-id="22220-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="22220-117">Em seguida, o mecanismo de execução honra a solicitação do criador de perfil, passando essa ID alternativa, além da ID de função tradicional, de volta para o criador de perfil no `clientData` parâmetro de `FunctionEnter2` , `FunctionLeave2` e os `FunctionTailcall2` ganchos, para identificar a função para a qual o gancho está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="22220-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="22220-118">Você pode usar o método [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) para especificar a implementação da `FunctionIDMapper` função.</span><span class="sxs-lookup"><span data-stu-id="22220-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="22220-119">Você pode chamar o `ICorProfilerInfo::SetFunctionIDMapper` método apenas uma vez e é recomendável fazer isso no retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="22220-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="22220-120">Por padrão, supõe-se que um criador de perfil que define o sinalizador de COR_PRF_MONITOR_ENTERLEAVE usando [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)e que define ganchos via [ICorProfilerInfo:: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), deve receber os `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` retornos de chamada, e para cada função.</span><span class="sxs-lookup"><span data-stu-id="22220-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="22220-121">No entanto, os profileres podem implementar `FunctionIDMapper` para evitar seletivamente o recebimento desses retornos de chamada para determinadas funções definindo `pbHookFunction` como `false` .</span><span class="sxs-lookup"><span data-stu-id="22220-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="22220-122">Os profileres devem ser tolerantes a casos em que vários threads de um aplicativo de perfil criado chamam o mesmo método/função simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="22220-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="22220-123">Nesses casos, o criador de perfil pode receber vários `FunctionIDMapper` retornos de chamada para o mesmo `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="22220-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="22220-124">O criador de perfil deve ter certeza de retornar os mesmos valores desse retorno de chamada quando ele é chamado várias vezes com o mesmo `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="22220-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22220-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22220-125">Requirements</span></span>  
 <span data-ttu-id="22220-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22220-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22220-127">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="22220-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="22220-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22220-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22220-129">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22220-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22220-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="22220-130">See also</span></span>

- [<span data-ttu-id="22220-131">Método SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="22220-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="22220-132">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="22220-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="22220-133">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="22220-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="22220-134">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="22220-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="22220-135">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="22220-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="22220-136">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="22220-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
