---
title: Função CorBindToRuntimeEx
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
ms.openlocfilehash: dcf2ce8bdb7cec1f567e548ff3314e160fffe9fd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616626"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="181c2-102">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="181c2-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="181c2-103">Permite que hosts não gerenciados carreguem o Common Language Runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="181c2-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="181c2-104">O [CorBindToRuntime](corbindtoruntime-function.md) e as `CorBindToRuntimeEx` funções executam a mesma operação, mas a `CorBindToRuntimeEx` função permite que você defina sinalizadores para especificar o comportamento do CLR.</span><span class="sxs-lookup"><span data-stu-id="181c2-104">The [CorBindToRuntime](corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="181c2-105">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="181c2-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="181c2-106">Essa função usa um conjunto de parâmetros que permitem que um host faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="181c2-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="181c2-107">Especifique a versão do tempo de execução que será carregada.</span><span class="sxs-lookup"><span data-stu-id="181c2-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="181c2-108">Indique se a compilação do servidor ou da estação de trabalho deve ser carregada.</span><span class="sxs-lookup"><span data-stu-id="181c2-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="181c2-109">Controle se a coleta de lixo simultânea ou a coleta de lixo não simultânea está concluída.</span><span class="sxs-lookup"><span data-stu-id="181c2-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="181c2-110">Não há suporte para a coleta de lixo simultânea em aplicativos que executam o emulador x86 WOW64 em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamada IA-64).</span><span class="sxs-lookup"><span data-stu-id="181c2-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="181c2-111">Para obter mais informações sobre como usar o WOW64 em sistemas Windows de 64 bits, consulte [executando aplicativos de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="181c2-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="181c2-112">Controlar se os assemblies são carregados como domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="181c2-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="181c2-113">Obtenha um ponteiro de interface para um [ICorRuntimeHost](icorruntimehost-interface.md) que possa ser usado para definir opções adicionais para configurar uma instância do CLR antes que ela seja iniciada.</span><span class="sxs-lookup"><span data-stu-id="181c2-113">Obtain an interface pointer to an [ICorRuntimeHost](icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="181c2-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="181c2-114">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,
    [in]  LPCWSTR      pwszBuildFlavor,
    [in]  DWORD        startupFlags,
    [in]  REFCLSID     rclsid,
    [in]  REFIID       riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="181c2-115">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="181c2-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="181c2-116">no Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="181c2-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="181c2-117">Um número de versão no .NET Framework consiste em quatro partes separadas por pontos: *Major. Minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="181c2-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="181c2-118">A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número de versão (por exemplo, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="181c2-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="181c2-119">Algumas versões do CLR são instaladas com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="181c2-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="181c2-120">Por padrão, o Shim de inicialização `pwszVersion` é avaliado em relação a instruções de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="181c2-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="181c2-121">Um host pode forçar o Shim a ignorar a avaliação da política e carregar a versão exata especificada no `pwszVersion` passando um valor de `STARTUP_LOADER_SAFEMODE` para o `startupFlags` parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="181c2-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="181c2-122">Se o chamador especificar NULL para `pwszVersion` , `CorBindToRuntimeEx` o identificará o conjunto de tempos de execução instalados cujos números de versão são menores do que o tempo de execução do .NET Framework 4 e carregará a versão mais recente do tempo de execução desse conjunto.</span><span class="sxs-lookup"><span data-stu-id="181c2-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="181c2-123">Ele não carregará o .NET Framework 4 ou posterior e falhará se nenhuma versão anterior estiver instalada.</span><span class="sxs-lookup"><span data-stu-id="181c2-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="181c2-124">Observe que a passagem de NULL fornece ao host nenhum controle sobre qual versão do tempo de execução é carregada.</span><span class="sxs-lookup"><span data-stu-id="181c2-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="181c2-125">Embora essa abordagem possa ser apropriada em alguns cenários, é altamente recomendável que o host forneça uma versão específica para carregar.</span><span class="sxs-lookup"><span data-stu-id="181c2-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="181c2-126">no Uma cadeia de caracteres que especifica se o servidor ou a compilação da estação de trabalho do CLR deve ser carregada.</span><span class="sxs-lookup"><span data-stu-id="181c2-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="181c2-127">Os valores válidos são `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="181c2-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="181c2-128">A compilação do servidor é otimizada para aproveitar vários processadores para coletas de lixo e a compilação da estação de trabalho é otimizada para aplicativos cliente em execução em um computador com um único processador.</span><span class="sxs-lookup"><span data-stu-id="181c2-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="181c2-129">Se `pwszBuildFlavor` é definido como NULL, a compilação da estação de trabalho é carregada.</span><span class="sxs-lookup"><span data-stu-id="181c2-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="181c2-130">Durante a execução em um computador com um único processador, a compilação da estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` estiver definida como `svr` .</span><span class="sxs-lookup"><span data-stu-id="181c2-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="181c2-131">No entanto, se `pwszBuildFlavor` for definido como `svr` e a coleta de lixo simultânea for especificada (consulte a descrição do `startupFlags` parâmetro), a compilação do servidor será carregada.</span><span class="sxs-lookup"><span data-stu-id="181c2-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="181c2-132">no Uma combinação de valores da enumeração [STARTUP_FLAGS](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="181c2-132">[in] A combination of values of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="181c2-133">Esses sinalizadores controlam a coleta de lixo simultânea, o código de domínio neutro e o comportamento do `pwszVersion` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="181c2-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="181c2-134">O padrão é domínio único se nenhum sinalizador for definido.</span><span class="sxs-lookup"><span data-stu-id="181c2-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="181c2-135">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="181c2-135">The following values are valid:</span></span>  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="181c2-136">Para obter descrições desses sinalizadores, consulte a enumeração [STARTUP_FLAGS](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="181c2-136">For descriptions of these flags, see the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="181c2-137">no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="181c2-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="181c2-138">Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="181c2-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="181c2-139">no O `IID` da interface solicitada de `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="181c2-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="181c2-140">Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="181c2-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="181c2-141">fora O ponteiro de interface retornado para `riid` .</span><span class="sxs-lookup"><span data-stu-id="181c2-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="181c2-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="181c2-142">Remarks</span></span>  
 <span data-ttu-id="181c2-143">Se `pwszVersion` o especificar uma versão de tempo de execução que não existe, `CorBindToRuntimeEx` o retornará um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="181c2-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="181c2-144">Contexto de execução e fluxo de identidade do Windows</span><span class="sxs-lookup"><span data-stu-id="181c2-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="181c2-145">Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> objeto não flui em pontos assíncronos, como novos threads, pools de threads ou retornos de chamada de temporizador.</span><span class="sxs-lookup"><span data-stu-id="181c2-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="181c2-146">Na versão 2,0 do CLR, um <xref:System.Threading.ExecutionContext> objeto encapsula algumas informações sobre o thread em execução no momento e o flui em qualquer ponto assíncrono, mas não entre os limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="181c2-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="181c2-147">Da mesma forma, o <xref:System.Security.Principal.WindowsIdentity> objeto também flui em qualquer ponto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="181c2-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="181c2-148">Portanto, a representação atual no thread, se houver, flui também.</span><span class="sxs-lookup"><span data-stu-id="181c2-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="181c2-149">Você pode alterar o fluxo de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="181c2-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="181c2-150">Modificando as <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo em uma base por thread (consulte os <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> métodos, e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="181c2-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="181c2-151">Alterando o modo padrão do processo para o modo de compatibilidade da versão 1, em que o <xref:System.Security.Principal.WindowsIdentity> objeto não flui em nenhum ponto assíncrono, independentemente das <xref:System.Threading.ExecutionContext> configurações no thread atual.</span><span class="sxs-lookup"><span data-stu-id="181c2-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="181c2-152">A maneira como você altera o modo padrão depende se você usa um executável gerenciado ou uma interface de hospedagem não gerenciada para carregar o CLR:</span><span class="sxs-lookup"><span data-stu-id="181c2-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="181c2-153">Para executáveis gerenciados, você deve definir o `enabled` atributo do elemento de [ \<>legacyImpersonationPolicy](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) como `true` .</span><span class="sxs-lookup"><span data-stu-id="181c2-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="181c2-154">Para interfaces de hospedagem não gerenciadas, defina o `STARTUP_LEGACY_IMPERSONATION` sinalizador no `startupFlags` parâmetro ao chamar a `CorBindToRuntimeEx` função.</span><span class="sxs-lookup"><span data-stu-id="181c2-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="181c2-155">O modo de compatibilidade da versão 1 se aplica a todo o processo e a todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="181c2-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="181c2-156">Requisitos</span><span class="sxs-lookup"><span data-stu-id="181c2-156">Requirements</span></span>  
 <span data-ttu-id="181c2-157">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="181c2-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="181c2-158">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="181c2-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="181c2-159">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="181c2-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="181c2-160">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="181c2-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="181c2-161">Veja também</span><span class="sxs-lookup"><span data-stu-id="181c2-161">See also</span></span>

- [<span data-ttu-id="181c2-162">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="181c2-162">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="181c2-163">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="181c2-163">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="181c2-164">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="181c2-164">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="181c2-165">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="181c2-165">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="181c2-166">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="181c2-166">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="181c2-167">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="181c2-167">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
