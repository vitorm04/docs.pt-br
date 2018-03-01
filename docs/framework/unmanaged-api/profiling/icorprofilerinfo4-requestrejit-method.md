---
title: "Método ICorProfilerInfo4::RequestReJIT"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4da57e95813afa1135482bef7cf6ab50ee6365cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="6f643-102">Método ICorProfilerInfo4::RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="6f643-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="6f643-103">Solicita uma recompilação de JIT de todas as instâncias das funções especificadas.</span><span class="sxs-lookup"><span data-stu-id="6f643-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f643-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f643-104">Syntax</span></span>  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f643-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f643-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="6f643-106">[in] O número de funções de recompilar.</span><span class="sxs-lookup"><span data-stu-id="6f643-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="6f643-107">[in] Especifica o `moduleId` parte das (`module`, `methodDef`) pares que identificam as funções a ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="6f643-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="6f643-108">[in] Especifica o `methodId` parte das (`module`, `methodDef`) pares que identificam as funções a ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="6f643-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f643-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6f643-109">Return Value</span></span>  
 <span data-ttu-id="6f643-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="6f643-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6f643-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f643-111">HRESULT</span></span>|<span data-ttu-id="6f643-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f643-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f643-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f643-113">S_OK</span></span>|<span data-ttu-id="6f643-114">Foi feita uma tentativa para marcar todos os métodos para recompilação de JIT.</span><span class="sxs-lookup"><span data-stu-id="6f643-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="6f643-115">O criador de perfil deve implementar o [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) método para determinar quais métodos com êxito foram marcados para recompilação de JIT.</span><span class="sxs-lookup"><span data-stu-id="6f643-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="6f643-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="6f643-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="6f643-117">O criador de perfil deve implementar o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface para a chamada com suporte.</span><span class="sxs-lookup"><span data-stu-id="6f643-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="6f643-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="6f643-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="6f643-119">Recompilação de JIT não foi habilitada.</span><span class="sxs-lookup"><span data-stu-id="6f643-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="6f643-120">Você deve habilitar recompilação JIT durante a inicialização por meio de [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir o `COR_PRF_ENABLE_REJIT` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="6f643-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="6f643-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6f643-121">E_INVALIDARG</span></span>|<span data-ttu-id="6f643-122">`cFunctions`é 0, ou `moduleIds` ou `methodIds` é `NULL`.</span><span class="sxs-lookup"><span data-stu-id="6f643-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="6f643-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6f643-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6f643-124">O CLR não pôde concluir a solicitação porque ele ficou sem memória.</span><span class="sxs-lookup"><span data-stu-id="6f643-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f643-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f643-125">Remarks</span></span>  
 <span data-ttu-id="6f643-126">Chamar `RequestReJIT` para que o tempo de execução recompilar um conjunto especificado de funções.</span><span class="sxs-lookup"><span data-stu-id="6f643-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="6f643-127">Um criador de perfil de código, em seguida, pode usar o [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface para ajustar o código que é gerado quando as funções são recompiladas.</span><span class="sxs-lookup"><span data-stu-id="6f643-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="6f643-128">Isso não afeta a funções em execução no momento, apenas futuras invocações.</span><span class="sxs-lookup"><span data-stu-id="6f643-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="6f643-129">Se qualquer uma das funções especificadas anteriormente foi recompilado JIT, solicitar uma recompilação é equivalente a reversão e recompilar a função.</span><span class="sxs-lookup"><span data-stu-id="6f643-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="6f643-130">Para preservar a possibilidade de reversão, quando o compilador JIT compila a versão original de uma função, ele considera apenas as versões originais de seus chamados para decisões de inlining.</span><span class="sxs-lookup"><span data-stu-id="6f643-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="6f643-131">Quando o compilador JIT recompila uma função, ele considera as versões atuais (recompiladas ou originais) de seus chamados de inlining.</span><span class="sxs-lookup"><span data-stu-id="6f643-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="6f643-132">Um criador de perfil normalmente chama `RequestReJIT` em resposta à entrada do usuário solicitando que o criador de perfil instrumentar um ou mais métodos.</span><span class="sxs-lookup"><span data-stu-id="6f643-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="6f643-133">`RequestReJIT`Normalmente, suspende o tempo de execução para fazer parte de seu trabalho e podem potencialmente gatilho uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6f643-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="6f643-134">Como tal, o criador de perfil deve chamar `RequestReJIT` de um thread ele criou anteriormente e não de um thread criado pelo CLR que está executando um retorno de chamada do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="6f643-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f643-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f643-135">Requirements</span></span>  
 <span data-ttu-id="6f643-136">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f643-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f643-137">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f643-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f643-138">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f643-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f643-139">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f643-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f643-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f643-140">See Also</span></span>  
 [<span data-ttu-id="6f643-141">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="6f643-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="6f643-142">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6f643-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6f643-143">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6f643-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
