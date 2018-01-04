---
title: "Método ICorProfilerInfo4::RequestRevert"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestRevert
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f0bf926bc6ba458745231bc17ce20dbe5cdbd1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="3c792-102">Método ICorProfilerInfo4::RequestRevert</span><span class="sxs-lookup"><span data-stu-id="3c792-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="3c792-103">Reverte todas as instâncias das funções especificadas para suas versões originais.</span><span class="sxs-lookup"><span data-stu-id="3c792-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c792-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c792-104">Syntax</span></span>  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c792-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c792-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="3c792-106">[in] O número de funções para reverter.</span><span class="sxs-lookup"><span data-stu-id="3c792-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="3c792-107">[in] Especifica o `moduleId` parte das (`module`, `methodDef`) pares que identificam as funções para ser revertido.</span><span class="sxs-lookup"><span data-stu-id="3c792-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="3c792-108">[in] Especifica o `methodId` parte das (`module`, `methodDef`) pares que identificam as funções para ser revertido.</span><span class="sxs-lookup"><span data-stu-id="3c792-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="3c792-109">[out] Uma matriz de HRESULTs listadas na seção "Status HRESULTs" mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="3c792-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="3c792-110">Cada HRESULT indica o êxito ou falha da tentativa de reverter a cada função especificada nas matrizes paralelas `moduleIds` e `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="3c792-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c792-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3c792-111">Return Value</span></span>  
 <span data-ttu-id="3c792-112">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="3c792-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3c792-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c792-113">HRESULT</span></span>|<span data-ttu-id="3c792-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c792-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3c792-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c792-115">S_OK</span></span>|<span data-ttu-id="3c792-116">Foi feita uma tentativa para reverter todas as solicitações; No entanto, a matriz de status retornado deve ser verificada para determinar quais funções foram revertidas com êxito.</span><span class="sxs-lookup"><span data-stu-id="3c792-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="3c792-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="3c792-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="3c792-118">O criador de perfil deve implementar o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface para a chamada com suporte.</span><span class="sxs-lookup"><span data-stu-id="3c792-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="3c792-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="3c792-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="3c792-120">Recompilação de JIT não foi habilitada.</span><span class="sxs-lookup"><span data-stu-id="3c792-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="3c792-121">Você deve habilitar recompilação JIT durante a inicialização por meio de [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir o `COR_PRF_ENABLE_REJIT` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="3c792-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="3c792-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3c792-122">E_INVALIDARG</span></span>|<span data-ttu-id="3c792-123">`cFunctions`é 0, ou `moduleIds` ou `methodIds` é `NULL`.</span><span class="sxs-lookup"><span data-stu-id="3c792-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="3c792-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3c792-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3c792-125">O CLR não pôde concluir a solicitação porque ele ficou sem memória.</span><span class="sxs-lookup"><span data-stu-id="3c792-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="3c792-126">Status HRESULTS</span><span class="sxs-lookup"><span data-stu-id="3c792-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="3c792-127">Matriz de status de HRESULT</span><span class="sxs-lookup"><span data-stu-id="3c792-127">Status array HRESULT</span></span>|<span data-ttu-id="3c792-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c792-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="3c792-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="3c792-129">S_OK</span></span>|<span data-ttu-id="3c792-130">A função correspondente foi revertida com êxito.</span><span class="sxs-lookup"><span data-stu-id="3c792-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="3c792-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3c792-131">E_INVALIDARG</span></span>|<span data-ttu-id="3c792-132">O parâmetro `moduleID` ou `methodDef` é `NULL`.</span><span class="sxs-lookup"><span data-stu-id="3c792-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="3c792-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="3c792-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="3c792-134">O módulo ainda não foi totalmente carregado ou ele está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="3c792-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="3c792-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="3c792-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="3c792-136">O módulo especificado foi gerado dinamicamente (por exemplo, `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="3c792-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="3c792-137">Portanto, ele não é suportado por este método.</span><span class="sxs-lookup"><span data-stu-id="3c792-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="3c792-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="3c792-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="3c792-139">O CLR não foi possível reverter a função especificada, pois uma solicitação de recompilação active correspondente não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="3c792-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="3c792-140">Ou a recompilação nunca foi solicitada ou a função já foi revertida.</span><span class="sxs-lookup"><span data-stu-id="3c792-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="3c792-141">Outros</span><span class="sxs-lookup"><span data-stu-id="3c792-141">Other</span></span>|<span data-ttu-id="3c792-142">O sistema operacional retornou uma falha de fora do controle do CLR.</span><span class="sxs-lookup"><span data-stu-id="3c792-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="3c792-143">Por exemplo, se uma chamada do sistema para alterar a proteção de acesso de uma página de memória falhar, será exibido o erro do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="3c792-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c792-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c792-144">Remarks</span></span>  
 <span data-ttu-id="3c792-145">Na próxima vez que nenhuma das instâncias de função revereted são chamadas, as versões originais das funções serão executadas.</span><span class="sxs-lookup"><span data-stu-id="3c792-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="3c792-146">Se uma função estiver sendo executado, ele terminará executando a versão que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="3c792-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c792-147">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c792-147">Requirements</span></span>  
 <span data-ttu-id="3c792-148">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c792-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c792-149">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c792-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c792-150">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c792-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c792-151">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c792-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c792-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c792-152">See Also</span></span>  
 [<span data-ttu-id="3c792-153">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="3c792-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="3c792-154">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3c792-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="3c792-155">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="3c792-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
