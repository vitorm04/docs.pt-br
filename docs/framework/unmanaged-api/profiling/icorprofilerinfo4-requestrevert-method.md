---
title: Método ICorProfilerInfo4::RequestRevert
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: c7ced05692e3030bace10dab9a6793a29fac6c26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444829"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="b0843-102">Método ICorProfilerInfo4::RequestRevert</span><span class="sxs-lookup"><span data-stu-id="b0843-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="b0843-103">Reverte todas as instâncias das funções especificadas para suas versões originais.</span><span class="sxs-lookup"><span data-stu-id="b0843-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0843-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0843-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0843-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0843-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="b0843-106">no O número de funções a serem revertidas.</span><span class="sxs-lookup"><span data-stu-id="b0843-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="b0843-107">no Especifica a parte `moduleId` dos pares (`module`, `methodDef`) que identificam as funções a serem revertidas.</span><span class="sxs-lookup"><span data-stu-id="b0843-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="b0843-108">no Especifica a parte `methodId` dos pares (`module`, `methodDef`) que identificam as funções a serem revertidas.</span><span class="sxs-lookup"><span data-stu-id="b0843-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="b0843-109">fora Uma matriz de HRESULTs listada na seção "status HRESULTs" mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="b0843-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="b0843-110">Cada HRESULT indica o êxito ou a falha ao tentar reverter cada função especificada nas matrizes paralelas `moduleIds` e `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="b0843-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0843-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b0843-111">Return Value</span></span>  
 <span data-ttu-id="b0843-112">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="b0843-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b0843-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0843-113">HRESULT</span></span>|<span data-ttu-id="b0843-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0843-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0843-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0843-115">S_OK</span></span>|<span data-ttu-id="b0843-116">Foi feita uma tentativa de reverter todas as solicitações; no entanto, a matriz de status retornada deve ser verificada para determinar quais funções foram revertidas com êxito.</span><span class="sxs-lookup"><span data-stu-id="b0843-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="b0843-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="b0843-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="b0843-118">O criador de perfil deve implementar a interface [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) para que essa chamada seja suportada.</span><span class="sxs-lookup"><span data-stu-id="b0843-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="b0843-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="b0843-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="b0843-120">A recompilação JIT não foi habilitada.</span><span class="sxs-lookup"><span data-stu-id="b0843-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="b0843-121">Você deve habilitar a recompilação JIT durante a inicialização usando o método [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir o sinalizador de `COR_PRF_ENABLE_REJIT`.</span><span class="sxs-lookup"><span data-stu-id="b0843-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="b0843-122">{1&gt;E_INVALIDARG&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b0843-122">E_INVALIDARG</span></span>|<span data-ttu-id="b0843-123">`cFunctions` é 0, ou `moduleIds` ou `methodIds` é `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b0843-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="b0843-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b0843-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b0843-125">O CLR não pôde concluir a solicitação porque ficou sem memória.</span><span class="sxs-lookup"><span data-stu-id="b0843-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="b0843-126">Status HRESULTs</span><span class="sxs-lookup"><span data-stu-id="b0843-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="b0843-127">Matriz de status HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0843-127">Status array HRESULT</span></span>|<span data-ttu-id="b0843-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0843-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="b0843-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0843-129">S_OK</span></span>|<span data-ttu-id="b0843-130">A função correspondente foi revertida com êxito.</span><span class="sxs-lookup"><span data-stu-id="b0843-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="b0843-131">{1&gt;E_INVALIDARG&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b0843-131">E_INVALIDARG</span></span>|<span data-ttu-id="b0843-132">O parâmetro `moduleID` ou `methodDef` é `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b0843-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="b0843-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="b0843-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="b0843-134">O módulo ainda não está totalmente carregado ou está em processo de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="b0843-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="b0843-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="b0843-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="b0843-136">O módulo especificado foi gerado dinamicamente (por exemplo, por `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="b0843-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="b0843-137">Portanto, esse método não dá suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="b0843-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="b0843-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="b0843-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="b0843-139">O CLR não pôde reverter a função especificada porque uma solicitação de recompilação ativa correspondente não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="b0843-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="b0843-140">Ou a recompilação nunca foi solicitada ou a função já foi revertida.</span><span class="sxs-lookup"><span data-stu-id="b0843-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="b0843-141">Outros</span><span class="sxs-lookup"><span data-stu-id="b0843-141">Other</span></span>|<span data-ttu-id="b0843-142">O sistema operacional retornou uma falha fora do controle do CLR.</span><span class="sxs-lookup"><span data-stu-id="b0843-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="b0843-143">Por exemplo, se uma chamada do sistema para alterar a proteção de acesso de uma página de memória falhar, o erro do sistema operacional será exibido.</span><span class="sxs-lookup"><span data-stu-id="b0843-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0843-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0843-144">Remarks</span></span>  
 <span data-ttu-id="b0843-145">Na próxima vez que qualquer uma das instâncias de função revereted forem chamadas, as versões originais das funções serão executadas.</span><span class="sxs-lookup"><span data-stu-id="b0843-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="b0843-146">Se uma função já estiver em execução, ela concluirá a execução da versão que está em execução.</span><span class="sxs-lookup"><span data-stu-id="b0843-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0843-147">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0843-147">Requirements</span></span>  
 <span data-ttu-id="b0843-148">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0843-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0843-149">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b0843-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0843-150">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0843-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0843-151">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0843-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0843-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0843-152">See also</span></span>

- [<span data-ttu-id="b0843-153">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="b0843-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b0843-154">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b0843-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b0843-155">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b0843-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
