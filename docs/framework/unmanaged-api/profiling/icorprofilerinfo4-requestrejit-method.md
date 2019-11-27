---
title: Método ICorProfilerInfo4::RequestReJIT
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: eb4d5e1c4efd67914df95868b67ec5cc3fe6139a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444823"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="7c9cf-102">Método ICorProfilerInfo4::RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="7c9cf-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="7c9cf-103">Solicita uma recompilação JIT de todas as instâncias das funções especificadas.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c9cf-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c9cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7c9cf-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="7c9cf-106">no O número de funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="7c9cf-107">no Especifica a parte `moduleId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="7c9cf-108">no Especifica a parte `methodId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c9cf-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7c9cf-109">Return Value</span></span>  
 <span data-ttu-id="7c9cf-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7c9cf-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c9cf-111">HRESULT</span></span>|<span data-ttu-id="7c9cf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c9cf-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c9cf-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c9cf-113">S_OK</span></span>|<span data-ttu-id="7c9cf-114">Foi feita uma tentativa de marcar todos os métodos para a recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="7c9cf-115">O criador de perfil deve implementar o método [ICorProfilerCallback4:: ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) para determinar quais métodos foram marcados com êxito para recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="7c9cf-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="7c9cf-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="7c9cf-117">O criador de perfil deve implementar a interface [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) para que essa chamada seja suportada.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="7c9cf-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="7c9cf-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="7c9cf-119">A recompilação JIT não foi habilitada.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="7c9cf-120">Você deve habilitar a recompilação JIT durante a inicialização usando o método [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir o sinalizador de `COR_PRF_ENABLE_REJIT`.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="7c9cf-121">{1&gt;E_INVALIDARG&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7c9cf-121">E_INVALIDARG</span></span>|<span data-ttu-id="7c9cf-122">`cFunctions` é 0, ou `moduleIds` ou `methodIds` é `NULL`.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="7c9cf-123">{1&gt;E_OUTOFMEMORY&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7c9cf-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7c9cf-124">O CLR não pôde concluir a solicitação porque ficou sem memória.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c9cf-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c9cf-125">Remarks</span></span>  
 <span data-ttu-id="7c9cf-126">Chame `RequestReJIT` para que o tempo de execução recompile um conjunto especificado de funções.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="7c9cf-127">Um criador de perfil de código pode usar a interface [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) para ajustar o código que é gerado quando as funções são recompiladas.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="7c9cf-128">Isso não afeta as funções atualmente em execução, apenas as invocações de função futuras.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="7c9cf-129">Se qualquer uma das funções especificadas tiver sido recompilada por JIT, a solicitação de uma recompilação será equivalente à reversão e à recompilação da função.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="7c9cf-130">Para preservar o inversão, quando o compilador JIT compila a versão original de uma função, ele considera apenas as versões originais dos seus chamadores para as decisões de inalinhamento.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="7c9cf-131">Quando o compilador JIT recompila uma função, ele considera as versões atuais (recompiladas ou originais) de seus chamadores para o inlining.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="7c9cf-132">Um criador de perfil normalmente chama `RequestReJIT` em resposta à entrada do usuário solicitando que o criador de perfil tenha um ou mais métodos.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="7c9cf-133">o `RequestReJIT` normalmente suspende o tempo de execução para fazer parte de seu trabalho e pode potencialmente disparar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="7c9cf-134">Como tal, o criador de perfil deve chamar `RequestReJIT` de um thread criado anteriormente, e não de um thread criado pelo CLR que está atualmente executando um retorno de chamada do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="7c9cf-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9cf-135">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7c9cf-135">Requirements</span></span>  
 <span data-ttu-id="7c9cf-136">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9cf-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9cf-137">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7c9cf-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c9cf-138">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c9cf-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c9cf-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9cf-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9cf-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c9cf-140">See also</span></span>

- [<span data-ttu-id="7c9cf-141">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="7c9cf-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="7c9cf-142">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7c9cf-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="7c9cf-143">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7c9cf-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
