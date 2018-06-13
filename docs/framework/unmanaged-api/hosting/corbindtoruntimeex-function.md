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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75df07148ddb69ad6a062c80ec9b279e2f36e03e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435975"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="f148c-102">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="f148c-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="f148c-103">Habilita a hosts não gerenciados para carregar o common language runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="f148c-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="f148c-104">O [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) e `CorBindToRuntimeEx` funções executam a mesma operação, mas o `CorBindToRuntimeEx` função permite que você defina os sinalizadores para especificar o comportamento do CLR.</span><span class="sxs-lookup"><span data-stu-id="f148c-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="f148c-105">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f148c-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
 <span data-ttu-id="f148c-106">Essa função usa um conjunto de parâmetros que permitem que um host fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f148c-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
-   <span data-ttu-id="f148c-107">Especifique a versão do tempo de execução que será carregada.</span><span class="sxs-lookup"><span data-stu-id="f148c-107">Specify the version of the runtime that will be loaded.</span></span>  
  
-   <span data-ttu-id="f148c-108">Indique se a compilação do servidor ou estação de trabalho deve ser carregada.</span><span class="sxs-lookup"><span data-stu-id="f148c-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
-   <span data-ttu-id="f148c-109">Controle se a coleta de lixo simultânea ou coleta de lixo não simultânea é feita.</span><span class="sxs-lookup"><span data-stu-id="f148c-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f148c-110">Não há suporte para a coleta de lixo simultânea em aplicativos em execução o WOW64 x86 emulador em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamado de IA-64).</span><span class="sxs-lookup"><span data-stu-id="f148c-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="f148c-111">Para obter mais informações sobre como usar o WOW64 em sistemas de 64 bits do Windows, consulte [aplicativos em execução de 32 bits](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="f148c-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
-   <span data-ttu-id="f148c-112">Controle se os assemblies são carregados como domínios neutros.</span><span class="sxs-lookup"><span data-stu-id="f148c-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
-   <span data-ttu-id="f148c-113">Obter um ponteiro de interface para um [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) que pode ser usado para definir opções adicionais para configurar uma instância do CLR para ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="f148c-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f148c-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f148c-114">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f148c-115">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f148c-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="f148c-116">[in] Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="f148c-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="f148c-117">Um número de versão do .NET Framework consiste em quatro partes separadas por pontos: *Revision*.</span><span class="sxs-lookup"><span data-stu-id="f148c-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="f148c-118">A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido as primeiras três partes do número de versão (por exemplo, "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="f148c-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="f148c-119">Algumas versões do CLR são instalados com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="f148c-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="f148c-120">Por padrão, a correção de inicialização avalia `pwszVersion` em declarações de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="f148c-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="f148c-121">Um host pode forçar a correção para ignorar a avaliação de política e carregar a versão exata especificada no `pwszVersion` passando um valor de `STARTUP_LOADER_SAFEMODE` para o `startupFlags` parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="f148c-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="f148c-122">Se o chamador especificar null para `pwszVersion`, `CorBindToRuntimeEx` identifica o conjunto de tempo de execução instalado cujos números de versão são menores do que o tempo de execução do .NET Framework 4 e carrega a versão mais recente do tempo de execução do conjunto.</span><span class="sxs-lookup"><span data-stu-id="f148c-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="f148c-123">Ele não é possível carregar o .NET Framework 4 ou posterior e falhará se nenhuma versão anterior instalada.</span><span class="sxs-lookup"><span data-stu-id="f148c-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="f148c-124">Observe que passar null não oferece o host nenhum controle sobre qual versão do tempo de execução é carregado.</span><span class="sxs-lookup"><span data-stu-id="f148c-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="f148c-125">Embora essa abordagem pode ser apropriada em alguns cenários, é altamente recomendável que o host de fornece uma versão específica para carregar.</span><span class="sxs-lookup"><span data-stu-id="f148c-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="f148c-126">[in] Uma cadeia de caracteres que especifica se a carga do servidor ou a compilação de estação de trabalho do CLR.</span><span class="sxs-lookup"><span data-stu-id="f148c-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="f148c-127">Os valores válidos são `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="f148c-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="f148c-128">A compilação do servidor é otimizada para tirar proveito de vários processadores para coletas de lixo e a compilação de estação de trabalho é otimizada para aplicativos de cliente em execução em um computador com processador único.</span><span class="sxs-lookup"><span data-stu-id="f148c-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="f148c-129">Se `pwszBuildFlavor` for definido como null, a compilação de estação de trabalho está carregada.</span><span class="sxs-lookup"><span data-stu-id="f148c-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="f148c-130">Quando em execução em um computador com processador único, a compilação de estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` é definido como `svr`.</span><span class="sxs-lookup"><span data-stu-id="f148c-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="f148c-131">No entanto, se `pwszBuildFlavor` é definido como `svr` e coleta de lixo simultânea for especificada (consulte a descrição do `startupFlags` parâmetro), a compilação do servidor é carregada.</span><span class="sxs-lookup"><span data-stu-id="f148c-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="f148c-132">[in] Uma combinação de valores de [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="f148c-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="f148c-133">Esses sinalizadores de coleta de lixo simultânea, código de domínio neutro e o comportamento de controlam de `pwszVersion` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f148c-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="f148c-134">O padrão é o único domínio se nenhum sinalizador for definido.</span><span class="sxs-lookup"><span data-stu-id="f148c-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="f148c-135">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="f148c-135">The following values are valid:</span></span>  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="f148c-136">Para obter descrições desses sinalizadores, consulte o [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="f148c-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="f148c-137">[in] O `CLSID` da coclass que implemente tanto o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f148c-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="f148c-138">Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="f148c-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="f148c-139">[in] O `IID` da interface solicitada de `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="f148c-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="f148c-140">Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="f148c-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f148c-141">[out] O ponteiro de interface retornado para `riid`.</span><span class="sxs-lookup"><span data-stu-id="f148c-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f148c-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="f148c-142">Remarks</span></span>  
 <span data-ttu-id="f148c-143">Se `pwszVersion` Especifica uma versão de tempo de execução que não existe, `CorBindToRuntimeEx` retorna um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="f148c-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="f148c-144">Contexto de execução e o fluxo de identidade do Windows</span><span class="sxs-lookup"><span data-stu-id="f148c-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="f148c-145">Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> não fluxo do objeto pelos pontos assíncronos como novos threads, pools de threads ou retornos de chamada timer.</span><span class="sxs-lookup"><span data-stu-id="f148c-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="f148c-146">Na versão 2.0 do CLR, um <xref:System.Threading.ExecutionContext> objeto envolve algumas informações sobre o thread em execução no momento e fluxos de em qualquer ponto assíncrono, mas não nos limites do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f148c-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="f148c-147">Da mesma forma, o <xref:System.Security.Principal.WindowsIdentity> objeto também passa em qualquer ponto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f148c-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="f148c-148">Portanto, a representação atual no thread, se houver, fluxos muito.</span><span class="sxs-lookup"><span data-stu-id="f148c-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="f148c-149">Você pode alterar o fluxo de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="f148c-149">You can alter the flow in two ways:</span></span>  
  
1.  <span data-ttu-id="f148c-150">Modificando o <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo em uma base por thread (consulte o <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> métodos).</span><span class="sxs-lookup"><span data-stu-id="f148c-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2.  <span data-ttu-id="f148c-151">Alterando o modo de processo padrão para o modo de compatibilidade de versão 1, onde o <xref:System.Security.Principal.WindowsIdentity> não fluxo do objeto em qualquer ponto assíncrono, independentemente do <xref:System.Threading.ExecutionContext> configurações no thread atual.</span><span class="sxs-lookup"><span data-stu-id="f148c-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="f148c-152">Como alterar o modo padrão depende se você usar uma interface de hospedagem não gerenciada ou um executável gerenciado para carregar o CLR:</span><span class="sxs-lookup"><span data-stu-id="f148c-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1.  <span data-ttu-id="f148c-153">Executáveis gerenciados, você deve definir o `enabled` atributo do [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elemento `true`.</span><span class="sxs-lookup"><span data-stu-id="f148c-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2.  <span data-ttu-id="f148c-154">Para não gerenciado interfaces de hospedagem, defina o `STARTUP_LEGACY_IMPERSONATION` sinalizador no `startupFlags` parâmetro ao chamar o `CorBindToRuntimeEx` função.</span><span class="sxs-lookup"><span data-stu-id="f148c-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="f148c-155">O modo de compatibilidade de versão 1 se aplica a todo o processo e todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="f148c-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f148c-156">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f148c-156">Requirements</span></span>  
 <span data-ttu-id="f148c-157">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f148c-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f148c-158">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f148c-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f148c-159">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f148c-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f148c-160">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f148c-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f148c-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f148c-161">See Also</span></span>  
 [<span data-ttu-id="f148c-162">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="f148c-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="f148c-163">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="f148c-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="f148c-164">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="f148c-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="f148c-165">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f148c-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="f148c-166">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f148c-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="f148c-167">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="f148c-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
