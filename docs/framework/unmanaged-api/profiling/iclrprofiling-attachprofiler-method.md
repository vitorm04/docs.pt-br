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
ms.openlocfilehash: 48ac09e1862ae58e79707235e891f72920de1251
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500553"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="bd97a-102">Método ICLRProfiling::AttachProfiler</span><span class="sxs-lookup"><span data-stu-id="bd97a-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="bd97a-103">Anexa o criador de perfil especificado ao processo especificado.</span><span class="sxs-lookup"><span data-stu-id="bd97a-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd97a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd97a-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd97a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd97a-105">Parameters</span></span>

- `dwProfileeProcessID`

  <span data-ttu-id="bd97a-106">\[no] a ID do processo do processo ao qual o criador de perfil deve ser anexado.</span><span class="sxs-lookup"><span data-stu-id="bd97a-106">\[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="bd97a-107">Em um computador de 64 bits, o bit de execução do processo de perfil deve corresponder ao bit de execução do processo de gatilho que está chamando `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="bd97a-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="bd97a-108">Se a conta de usuário sob a qual o `AttachProfiler` é chamado tiver privilégios administrativos, o processo de destino poderá ser qualquer processo no sistema.</span><span class="sxs-lookup"><span data-stu-id="bd97a-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="bd97a-109">Caso contrário, o processo de destino deve ser de propriedade da mesma conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="bd97a-109">Otherwise, the target process must be owned by the same user account.</span></span>

- `dwMillisecondsMax`

  <span data-ttu-id="bd97a-110">\[em] o tempo de duração, em milissegundos, para `AttachProfiler` concluir.</span><span class="sxs-lookup"><span data-stu-id="bd97a-110">\[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="bd97a-111">O processo de disparo deve passar um tempo limite que é conhecido como suficiente para que o criador de perfil específico conclua sua inicialização.</span><span class="sxs-lookup"><span data-stu-id="bd97a-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>
  
- `pClsidProfiler`

  <span data-ttu-id="bd97a-112">\[in] um ponteiro para o CLSID do criador de perfil a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="bd97a-112">\[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="bd97a-113">O processo de disparo pode reutilizar essa memória após o `AttachProfiler` retorno.</span><span class="sxs-lookup"><span data-stu-id="bd97a-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>

- `wszProfilerPath`

  <span data-ttu-id="bd97a-114">\[in] o caminho completo para o arquivo DLL do criador de perfil a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="bd97a-114">\[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="bd97a-115">Essa cadeia de caracteres deve conter no máximo 260 caracteres, incluindo o terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="bd97a-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="bd97a-116">Se `wszProfilerPath` for nulo ou uma cadeia de caracteres vazia, o Common Language Runtime (CLR) tentará localizar o local do arquivo DLL do criador de perfil procurando no registro para o CLSID que `pClsidProfiler` aponta para.</span><span class="sxs-lookup"><span data-stu-id="bd97a-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>

- `pvClientData`

  <span data-ttu-id="bd97a-117">\[in] um ponteiro para os dados a serem passados para o criador de perfil pelo método [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bd97a-117">\[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="bd97a-118">O processo de disparo pode reutilizar essa memória após o `AttachProfiler` retorno.</span><span class="sxs-lookup"><span data-stu-id="bd97a-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="bd97a-119">Se `pvClientData` for NULL, `cbClientData` deverá ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="bd97a-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>

- `cbClientData`

  <span data-ttu-id="bd97a-120">\[em] o tamanho, em bytes, dos dados que `pvClientData` aponta para.</span><span class="sxs-lookup"><span data-stu-id="bd97a-120">\[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd97a-121">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="bd97a-121">Return Value</span></span>  
 <span data-ttu-id="bd97a-122">Esse método retorna os HRESULTs a seguir.</span><span class="sxs-lookup"><span data-stu-id="bd97a-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="bd97a-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd97a-123">HRESULT</span></span>|<span data-ttu-id="bd97a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd97a-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd97a-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd97a-125">S_OK</span></span>|<span data-ttu-id="bd97a-126">O criador de perfil especificado foi anexado com êxito ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bd97a-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="bd97a-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="bd97a-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="bd97a-128">Já existe um criador de perfil ativo ou anexando ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bd97a-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="bd97a-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="bd97a-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="bd97a-130">O criador de perfil especificado não oferece suporte a anexos.</span><span class="sxs-lookup"><span data-stu-id="bd97a-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="bd97a-131">O processo de disparo pode tentar anexar um criador de perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="bd97a-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="bd97a-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="bd97a-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="bd97a-133">Não é possível solicitar um anexo do criador de perfil porque a versão do processo de destino é incompatível com o processo atual que está chamando `AttachProfiler` .</span><span class="sxs-lookup"><span data-stu-id="bd97a-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="bd97a-134">HRESULT_FROM_WIN32 (ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="bd97a-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="bd97a-135">O usuário do processo de gatilho não tem acesso ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bd97a-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="bd97a-136">HRESULT_FROM_WIN32 (ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="bd97a-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="bd97a-137">O usuário do processo de gatilho não tem os privilégios necessários para anexar um criador de perfil ao processo de destino fornecido.</span><span class="sxs-lookup"><span data-stu-id="bd97a-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="bd97a-138">O log de eventos do aplicativo pode conter mais informações.</span><span class="sxs-lookup"><span data-stu-id="bd97a-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="bd97a-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="bd97a-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="bd97a-140">Ocorreu uma falha ao se comunicar com o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bd97a-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="bd97a-141">Isso geralmente acontece se o processo de destino estava sendo desligado.</span><span class="sxs-lookup"><span data-stu-id="bd97a-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="bd97a-142">HRESULT_FROM_WIN32 (ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="bd97a-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="bd97a-143">O processo de destino não existe ou não está executando um CLR que ofereça suporte a anexos.</span><span class="sxs-lookup"><span data-stu-id="bd97a-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="bd97a-144">Isso pode indicar que o CLR foi descarregado desde a chamada para o método de enumeração de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bd97a-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="bd97a-145">HRESULT_FROM_WIN32 (ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="bd97a-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="bd97a-146">O tempo limite expirou sem começar a carregar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="bd97a-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="bd97a-147">Você pode repetir a operação de anexação.</span><span class="sxs-lookup"><span data-stu-id="bd97a-147">You can retry the attach operation.</span></span> <span data-ttu-id="bd97a-148">Os tempos limite ocorrem quando um finalizador no processo de destino é executado por um tempo maior do que o valor de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bd97a-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="bd97a-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bd97a-149">E_INVALIDARG</span></span>|<span data-ttu-id="bd97a-150">Um ou mais parâmetros têm valores inválidos.</span><span class="sxs-lookup"><span data-stu-id="bd97a-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="bd97a-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd97a-151">E_FAIL</span></span>|<span data-ttu-id="bd97a-152">Ocorreu alguma outra falha não especificada.</span><span class="sxs-lookup"><span data-stu-id="bd97a-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="bd97a-153">Outros códigos de erro</span><span class="sxs-lookup"><span data-stu-id="bd97a-153">Other error codes</span></span>|<span data-ttu-id="bd97a-154">Se o método [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) do criador de perfil retornar um HRESULT que indica falha, `AttachProfiler` retornará esse mesmo HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bd97a-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="bd97a-155">Nesse caso, E_NOTIMPL é convertida em CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="bd97a-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd97a-156">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd97a-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="bd97a-157">Gerenciamento de memória</span><span class="sxs-lookup"><span data-stu-id="bd97a-157">Memory Management</span></span>  
 <span data-ttu-id="bd97a-158">Ao manter as convenções com, o chamador de `AttachProfiler` (por exemplo, o código de gatilho criado pelo desenvolvedor do criador de perfil) é responsável por alocar e desalocar a memória para os dados aos quais o `pvClientData` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="bd97a-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="bd97a-159">Quando o CLR executa a `AttachProfiler` chamada, ele faz uma cópia da memória que `pvClientData` aponta para e a transmite para o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bd97a-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="bd97a-160">Quando o CLR dentro do processo de destino recebe sua própria cópia do `pvClientData` bloco, ele passa o bloco para o criador de perfil por meio do `InitializeForAttach` método e, em seguida, desaloca sua cópia do `pvClientData` bloco do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="bd97a-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd97a-161">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd97a-161">Requirements</span></span>  
 <span data-ttu-id="bd97a-162">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd97a-162">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd97a-163">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bd97a-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd97a-164">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd97a-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd97a-165">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd97a-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd97a-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="bd97a-166">See also</span></span>

- [<span data-ttu-id="bd97a-167">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bd97a-167">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="bd97a-168">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="bd97a-168">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="bd97a-169">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="bd97a-169">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="bd97a-170">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="bd97a-170">Profiling</span></span>](index.md)
