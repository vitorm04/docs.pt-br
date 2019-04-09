---
title: Método ICLRProfiling::AttachProfiler
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e3898fb836409df3b685d985d0d72ab63230a93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174168"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="500ee-102">Método ICLRProfiling::AttachProfiler</span><span class="sxs-lookup"><span data-stu-id="500ee-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="500ee-103">Anexa o criador de perfil especificado para o processo especificado.</span><span class="sxs-lookup"><span data-stu-id="500ee-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="500ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="500ee-104">Syntax</span></span>  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="500ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="500ee-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="500ee-106">[in] A ID do processo do processo ao qual o criador de perfil deve ser anexado.</span><span class="sxs-lookup"><span data-stu-id="500ee-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="500ee-107">Em um computador de 64 bits, número de bits do processo de criação de perfil deve corresponder ao número de bits do processo de gatilho que está chamando `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="500ee-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="500ee-108">Se a conta de usuário sob a qual `AttachProfiler` é chamado tem privilégios administrativos, o processo de destino pode ser qualquer processo no sistema.</span><span class="sxs-lookup"><span data-stu-id="500ee-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="500ee-109">Caso contrário, o processo de destino deve ser de propriedade da mesma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="500ee-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="500ee-110">[in] A duração de tempo, em milissegundos, para `AttachProfiler` para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="500ee-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="500ee-111">O processo de gatilho deve passar um tempo limite que é conhecido por ser suficiente para o criador de perfil específica concluir sua inicialização.</span><span class="sxs-lookup"><span data-stu-id="500ee-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="500ee-112">[in] Um ponteiro para o CLSID do criador de perfil a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="500ee-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="500ee-113">O processo de gatilho pode reutilizar essa memória após `AttachProfiler` retorna.</span><span class="sxs-lookup"><span data-stu-id="500ee-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="500ee-114">[in] O caminho completo para o arquivo DLL do criador de perfil a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="500ee-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="500ee-115">Essa cadeia de caracteres deve conter não mais do que 260 caracteres, incluindo o terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="500ee-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="500ee-116">Se `wszProfilerPath` é nulo ou uma cadeia de caracteres vazia, o common language runtime (CLR) tenta encontrar o local do arquivo DLL do criador de perfil ao procurar no Registro CLSID que `pClsidProfiler` aponta.</span><span class="sxs-lookup"><span data-stu-id="500ee-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="500ee-117">[in] Um ponteiro para dados a serem passados para o criador de perfil, o [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="500ee-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="500ee-118">O processo de gatilho pode reutilizar essa memória após `AttachProfiler` retorna.</span><span class="sxs-lookup"><span data-stu-id="500ee-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="500ee-119">Se `pvClientData` for nulo, `cbClientData` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="500ee-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="500ee-120">[in] O tamanho, em bytes, dos dados que `pvClientData` aponta.</span><span class="sxs-lookup"><span data-stu-id="500ee-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="500ee-121">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="500ee-121">Return Value</span></span>  
 <span data-ttu-id="500ee-122">Esse método retorna os HRESULTs a seguir.</span><span class="sxs-lookup"><span data-stu-id="500ee-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="500ee-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="500ee-123">HRESULT</span></span>|<span data-ttu-id="500ee-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="500ee-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="500ee-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="500ee-125">S_OK</span></span>|<span data-ttu-id="500ee-126">O criador de perfil especificado foi anexado com êxito o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="500ee-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="500ee-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="500ee-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="500ee-128">Já existe um criador de perfil ativas ou anexando ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="500ee-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="500ee-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="500ee-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="500ee-130">O criador de perfil especificado não oferece suporte para o anexo.</span><span class="sxs-lookup"><span data-stu-id="500ee-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="500ee-131">O processo de gatilho pode tentar anexar um criador de perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="500ee-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="500ee-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="500ee-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="500ee-133">Não é possível solicitar um anexo do criador de perfil, porque a versão do processo de destino é incompatível com o processo atual que está chamando `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="500ee-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="500ee-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="500ee-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="500ee-135">O usuário do processo de gatilho não tem acesso ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="500ee-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="500ee-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="500ee-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="500ee-137">O usuário do processo de gatilho não tem os privilégios necessários para anexar um criador de perfil ao processo de destino fornecido.</span><span class="sxs-lookup"><span data-stu-id="500ee-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="500ee-138">O log de eventos do aplicativo pode conter mais informações.</span><span class="sxs-lookup"><span data-stu-id="500ee-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="500ee-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="500ee-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="500ee-140">Ocorreu uma falha ao se comunicar com o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="500ee-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="500ee-141">Isso normalmente acontece se o processo de destino estava sendo desligado.</span><span class="sxs-lookup"><span data-stu-id="500ee-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="500ee-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="500ee-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="500ee-143">O processo de destino não existe ou não está em execução um CLR que dá suporte ao anexo.</span><span class="sxs-lookup"><span data-stu-id="500ee-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="500ee-144">Isso pode indicar que o CLR foi descarregado desde a chamada para o método de enumeração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="500ee-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="500ee-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="500ee-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="500ee-146">O tempo limite expirou sem início para carregar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="500ee-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="500ee-147">Você pode repetir a operação de anexação.</span><span class="sxs-lookup"><span data-stu-id="500ee-147">You can retry the attach operation.</span></span> <span data-ttu-id="500ee-148">Tempos limite ocorre quando um finalizador no processo de destino é executado por um período maior que o valor de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="500ee-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="500ee-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="500ee-149">E_INVALIDARG</span></span>|<span data-ttu-id="500ee-150">Um ou mais parâmetros possuem valores inválidos.</span><span class="sxs-lookup"><span data-stu-id="500ee-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="500ee-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="500ee-151">E_FAIL</span></span>|<span data-ttu-id="500ee-152">Ocorreu falha de alguns outra, não especificada.</span><span class="sxs-lookup"><span data-stu-id="500ee-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="500ee-153">Outros códigos de erro</span><span class="sxs-lookup"><span data-stu-id="500ee-153">Other error codes</span></span>|<span data-ttu-id="500ee-154">Se o criador de perfil [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) método retorna um HRESULT que indica falha, `AttachProfiler` Retorna ou mesmo HRESULT.</span><span class="sxs-lookup"><span data-stu-id="500ee-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="500ee-155">Nesse caso, E_NOTIMPL é convertido em CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="500ee-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="500ee-156">Comentários</span><span class="sxs-lookup"><span data-stu-id="500ee-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="500ee-157">Gerenciamento de memória</span><span class="sxs-lookup"><span data-stu-id="500ee-157">Memory Management</span></span>  
 <span data-ttu-id="500ee-158">Manter com as convenções de COM, o chamador de `AttachProfiler` (por exemplo, o código do gatilho criado pelo desenvolvedor do criador de perfil) é responsável por alocar e desalocar a memória para os dados que o `pvClientData` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="500ee-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="500ee-159">Quando o CLR executa o `AttachProfiler` chamada, ele faz uma cópia da memória que `pvClientData` aponta para e a transmite para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="500ee-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="500ee-160">Quando o CLR dentro do processo de destino recebe sua própria cópia da `pvClientData` bloco, ele passa o bloco para o criador de perfil por meio de `InitializeForAttach` método e, em seguida, desaloca sua cópia do `pvClientData` bloco do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="500ee-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="500ee-161">Requisitos</span><span class="sxs-lookup"><span data-stu-id="500ee-161">Requirements</span></span>  
 <span data-ttu-id="500ee-162">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="500ee-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="500ee-163">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="500ee-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="500ee-164">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="500ee-164">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="500ee-165">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="500ee-165">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="500ee-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="500ee-166">See also</span></span>

- [<span data-ttu-id="500ee-167">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="500ee-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="500ee-168">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="500ee-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="500ee-169">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="500ee-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="500ee-170">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="500ee-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
