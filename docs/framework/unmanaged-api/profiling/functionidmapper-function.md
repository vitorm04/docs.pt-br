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
ms.openlocfilehash: 23c6f0a29160b6e1dc194cf360c07374c565522b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440697"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="3a09f-102">Função FunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="3a09f-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="3a09f-103">Notifica o criador de perfil de que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usada nos retornos de chamada [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)e [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) para essa função.</span><span class="sxs-lookup"><span data-stu-id="3a09f-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="3a09f-104">`FunctionIDMapper` também permite que o criador de perfil indique se deseja receber retornos de chamada para essa função.</span><span class="sxs-lookup"><span data-stu-id="3a09f-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a09f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a09f-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a09f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a09f-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="3a09f-107">no O identificador de função a ser remapeado.</span><span class="sxs-lookup"><span data-stu-id="3a09f-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="3a09f-108">fora Um ponteiro para um valor que o criador de perfil define para `true` se deseja receber `FunctionEnter2`, `FunctionLeave2`e `FunctionTailcall2` retornos de chamada; caso contrário, ele definirá esse valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="3a09f-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a09f-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3a09f-109">Return Value</span></span>  
 <span data-ttu-id="3a09f-110">O criador de perfil retorna um valor que o mecanismo de execução usa como um identificador de função alternativo.</span><span class="sxs-lookup"><span data-stu-id="3a09f-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="3a09f-111">O valor de retorno não pode ser nulo, a menos que `false` seja retornado em `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="3a09f-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="3a09f-112">Caso contrário, um valor de retorno nulo produzirá resultados imprevisíveis, incluindo possivelmente interromper o processo.</span><span class="sxs-lookup"><span data-stu-id="3a09f-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a09f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a09f-113">Remarks</span></span>  
 <span data-ttu-id="3a09f-114">A função `FunctionIDMapper` é um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3a09f-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="3a09f-115">Ele é implementado pelo criador de perfil para remapear uma ID de função para algum outro identificador que seja mais útil para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="3a09f-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="3a09f-116">O `FunctionIDMapper` retorna a ID alternativa a ser usada para qualquer função específica.</span><span class="sxs-lookup"><span data-stu-id="3a09f-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="3a09f-117">Em seguida, o mecanismo de execução honra a solicitação do criador de perfil, passando essa ID alternativa, além da ID de função tradicional, de volta para o criador de perfil no parâmetro `clientData` dos ganchos `FunctionEnter2`, `FunctionLeave2`e `FunctionTailcall2`, para identificar a função para a qual o gancho está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="3a09f-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="3a09f-118">Você pode usar o método [ICorProfilerInfo:: SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) para especificar a implementação da função `FunctionIDMapper`.</span><span class="sxs-lookup"><span data-stu-id="3a09f-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="3a09f-119">Você pode chamar o método `ICorProfilerInfo::SetFunctionIDMapper` apenas uma vez e é recomendável fazer isso no retorno de chamada [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3a09f-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="3a09f-120">Por padrão, supõe-se que um criador de perfil que define o sinalizador de COR_PRF_MONITOR_ENTERLEAVE usando [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)e que define ganchos via [ICorProfilerInfo:: SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), deve receber os retornos de chamada `FunctionEnter2`, `FunctionLeave2`e `FunctionTailcall2` para cada função.</span><span class="sxs-lookup"><span data-stu-id="3a09f-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="3a09f-121">No entanto, os profileres podem implementar `FunctionIDMapper` para evitar seletivamente o recebimento desses retornos de chamada para determinadas funções, definindo `pbHookFunction` como `false`.</span><span class="sxs-lookup"><span data-stu-id="3a09f-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="3a09f-122">Os profileres devem ser tolerantes a casos em que vários threads de um aplicativo de perfil criado chamam o mesmo método/função simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="3a09f-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="3a09f-123">Nesses casos, o criador de perfil pode receber vários `FunctionIDMapper` retornos de chamada para o mesmo `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="3a09f-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="3a09f-124">O criador de perfil deve ter certeza de retornar os mesmos valores desse retorno de chamada quando ele é chamado várias vezes com o mesmo `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="3a09f-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a09f-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a09f-125">Requirements</span></span>  
 <span data-ttu-id="3a09f-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a09f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a09f-127">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="3a09f-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3a09f-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a09f-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a09f-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a09f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a09f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a09f-130">See also</span></span>

- [<span data-ttu-id="3a09f-131">Método SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="3a09f-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="3a09f-132">Função FunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="3a09f-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [<span data-ttu-id="3a09f-133">Função FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="3a09f-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="3a09f-134">Função FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="3a09f-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="3a09f-135">Função FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="3a09f-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="3a09f-136">Criando perfil de funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="3a09f-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
