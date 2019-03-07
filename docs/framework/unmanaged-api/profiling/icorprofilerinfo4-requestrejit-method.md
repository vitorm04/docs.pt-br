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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20312b80a4882acdaf53d9bcbf95ae2babe0fdca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476692"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="8e92c-102">Método ICorProfilerInfo4::RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="8e92c-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="8e92c-103">Solicita uma recompilação JIT de todas as instâncias das funções especificadas.</span><span class="sxs-lookup"><span data-stu-id="8e92c-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e92c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e92c-104">Syntax</span></span>  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e92c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e92c-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="8e92c-106">[in] O número de funções para recompilar.</span><span class="sxs-lookup"><span data-stu-id="8e92c-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="8e92c-107">[in] Especifica o `moduleId` parte do (`module`, `methodDef`) pares que identificam as funções a ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="8e92c-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="8e92c-108">[in] Especifica o `methodId` parte do (`module`, `methodDef`) pares que identificam as funções a ser recompilado.</span><span class="sxs-lookup"><span data-stu-id="8e92c-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e92c-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8e92c-109">Return Value</span></span>  
 <span data-ttu-id="8e92c-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="8e92c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8e92c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e92c-111">HRESULT</span></span>|<span data-ttu-id="8e92c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e92c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e92c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e92c-113">S_OK</span></span>|<span data-ttu-id="8e92c-114">Foi feita uma tentativa para marcar todos os métodos de recompilação JIT.</span><span class="sxs-lookup"><span data-stu-id="8e92c-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="8e92c-115">O criador de perfis deve implementar o [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) método para determinar quais métodos foram marcados para recompilação JIT com êxito.</span><span class="sxs-lookup"><span data-stu-id="8e92c-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="8e92c-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="8e92c-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="8e92c-117">O criador de perfis deve implementar o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface para a chamada a ter suporte.</span><span class="sxs-lookup"><span data-stu-id="8e92c-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="8e92c-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="8e92c-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="8e92c-119">Recompilação JIT não foi habilitada.</span><span class="sxs-lookup"><span data-stu-id="8e92c-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="8e92c-120">Você deve habilitar recompilação JIT durante a inicialização usando o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir o `COR_PRF_ENABLE_REJIT` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="8e92c-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="8e92c-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8e92c-121">E_INVALIDARG</span></span>|<span data-ttu-id="8e92c-122">`cFunctions` é 0, ou `moduleIds` ou `methodIds` é `NULL`.</span><span class="sxs-lookup"><span data-stu-id="8e92c-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="8e92c-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8e92c-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8e92c-124">O CLR não pôde concluir a solicitação porque ele ficou sem memória.</span><span class="sxs-lookup"><span data-stu-id="8e92c-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e92c-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e92c-125">Remarks</span></span>  
 <span data-ttu-id="8e92c-126">Chamar `RequestReJIT` para ter o tempo de execução a recompilar um conjunto de funções especificado.</span><span class="sxs-lookup"><span data-stu-id="8e92c-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="8e92c-127">Um criador de perfil de código, em seguida, pode usar o [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface para ajustar o código que é gerado quando as funções são recompiladas.</span><span class="sxs-lookup"><span data-stu-id="8e92c-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="8e92c-128">Isso não afeta as funções em execução no momento, invocações de função só futuras.</span><span class="sxs-lookup"><span data-stu-id="8e92c-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="8e92c-129">Se qualquer uma das funções especificadas anteriormente tiver sido recompilado por JIT, solicitar uma recompilação é equivalente a reversão e recompilar a função.</span><span class="sxs-lookup"><span data-stu-id="8e92c-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="8e92c-130">Para preservar a possibilidade de reversão, quando o compilador JIT compila a versão original de uma função, ele considera somente as versões originais de seus chamados para decisões de inlining.</span><span class="sxs-lookup"><span data-stu-id="8e92c-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="8e92c-131">Quando o compilador JIT recompila uma função, ele considera as versões atuais (recompiladas ou originais) do seus receptores de inlining.</span><span class="sxs-lookup"><span data-stu-id="8e92c-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="8e92c-132">Um criador de perfil chama normalmente `RequestReJIT` em resposta à entrada do usuário solicitando que o criador de perfil instrumentar um ou mais métodos.</span><span class="sxs-lookup"><span data-stu-id="8e92c-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="8e92c-133">`RequestReJIT` Normalmente, suspende o tempo de execução para fazer parte de seu trabalho e podem, potencialmente, uma coleta de lixo do gatilho.</span><span class="sxs-lookup"><span data-stu-id="8e92c-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="8e92c-134">Como tal, o criador de perfil deve chamar `RequestReJIT` de um thread ele criou anteriormente e não de um thread criado pelo CLR que está executando um retorno de chamada do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="8e92c-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e92c-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e92c-135">Requirements</span></span>  
 <span data-ttu-id="8e92c-136">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e92c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e92c-137">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e92c-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e92c-138">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e92c-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e92c-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e92c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e92c-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e92c-140">See also</span></span>
- [<span data-ttu-id="8e92c-141">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="8e92c-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="8e92c-142">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8e92c-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="8e92c-143">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8e92c-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
