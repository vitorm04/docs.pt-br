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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176494"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="b48fc-102">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="b48fc-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="b48fc-103">Habilita hosts não gerenciados para carregar o tempo de execução do idioma comum (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="b48fc-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="b48fc-104">O [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) e `CorBindToRuntimeEx` as funções executam a mesma operação, mas a `CorBindToRuntimeEx` função permite definir sinalizadores para especificar o comportamento da CLR.</span><span class="sxs-lookup"><span data-stu-id="b48fc-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="b48fc-105">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="b48fc-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="b48fc-106">Esta função leva um conjunto de parâmetros que permitem que um host faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b48fc-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="b48fc-107">Especifique a versão do tempo de execução que será carregada.</span><span class="sxs-lookup"><span data-stu-id="b48fc-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="b48fc-108">Indique se a compilação do servidor ou da estação de trabalho deve ser carregada.</span><span class="sxs-lookup"><span data-stu-id="b48fc-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="b48fc-109">Controle se a coleta simultânea de lixo ou a coleta de lixo não simultânea é feita.</span><span class="sxs-lookup"><span data-stu-id="b48fc-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b48fc-110">A coleta de lixo simultânea não é suportada em aplicativos que executam o emulador WOW64 x86 em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamada iA-64).</span><span class="sxs-lookup"><span data-stu-id="b48fc-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="b48fc-111">Para obter mais informações sobre como usar o WOW64 em sistemas Windows de 64 [bits, consulte Executando aplicativos de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="b48fc-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="b48fc-112">Controle se os conjuntos são carregados como neutros em domínio.</span><span class="sxs-lookup"><span data-stu-id="b48fc-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="b48fc-113">Obtenha um ponteiro de interface para um [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) que pode ser usado para definir opções adicionais para configurar uma instância do CLR antes de ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="b48fc-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b48fc-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b48fc-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b48fc-115">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b48fc-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="b48fc-116">[em] Uma seqüência descrevendo a versão do CLR que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="b48fc-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="b48fc-117">Um número de versão no Quadro .NET consiste em quatro partes separadas por períodos: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="b48fc-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="b48fc-118">A seqüência passou como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número da versão (por exemplo, "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="b48fc-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="b48fc-119">Algumas versões do CLR são instaladas com uma declaração de política que especifica compatibilidade com versões anteriores da CLR.</span><span class="sxs-lookup"><span data-stu-id="b48fc-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="b48fc-120">Por padrão, o shim `pwszVersion` de inicialização avalia contra as instruções de diretiva e carrega a versão mais recente do tempo de execução compatível com a versão que está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="b48fc-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="b48fc-121">Um host pode forçar o shim a pular a `pwszVersion` avaliação da diretiva `STARTUP_LOADER_SAFEMODE` e `startupFlags` carregar a versão exata especificada, passando um valor para o parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="b48fc-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="b48fc-122">Se o chamador `pwszVersion`especificar nulo para , `CorBindToRuntimeEx` identificar o conjunto de tempos de execução instalados cujos números de versão são inferiores ao tempo de execução .NET Framework 4 e carregar a versão mais recente do tempo de execução a partir desse conjunto.</span><span class="sxs-lookup"><span data-stu-id="b48fc-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="b48fc-123">Ele não carregará o .NET Framework 4 ou posterior, e falhará se nenhuma versão anterior estiver instalada.</span><span class="sxs-lookup"><span data-stu-id="b48fc-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="b48fc-124">Observe que a passagem nula não dá ao host nenhum controle sobre qual versão do tempo de execução é carregada.</span><span class="sxs-lookup"><span data-stu-id="b48fc-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="b48fc-125">Embora essa abordagem possa ser apropriada em alguns cenários, é fortemente recomendável que o host forneça uma versão específica para carregar.</span><span class="sxs-lookup"><span data-stu-id="b48fc-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="b48fc-126">[em] Uma seqüência que especifica se deve carregar o servidor ou a compilação da estação de trabalho da CLR.</span><span class="sxs-lookup"><span data-stu-id="b48fc-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="b48fc-127">Os valores válidos são `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="b48fc-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="b48fc-128">A compilação do servidor é otimizada para tirar proveito de vários processadores para coleta de lixo, e a construção da estação de trabalho é otimizada para aplicativos clientes em execução em uma máquina de processador único.</span><span class="sxs-lookup"><span data-stu-id="b48fc-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="b48fc-129">Se `pwszBuildFlavor` estiver definido como nulo, a construção da estação de trabalho está carregada.</span><span class="sxs-lookup"><span data-stu-id="b48fc-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="b48fc-130">Ao ser executado em uma máquina de processador único, a `pwszBuildFlavor` compilação `svr`da estação de trabalho está sempre carregada, mesmo que esteja configurada para .</span><span class="sxs-lookup"><span data-stu-id="b48fc-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="b48fc-131">No entanto, `pwszBuildFlavor` `svr` se for definida a coleta de lixo `startupFlags` simultânea (veja a descrição do parâmetro), a compilação do servidor será carregada.</span><span class="sxs-lookup"><span data-stu-id="b48fc-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="b48fc-132">[em] Uma combinação de valores da [enumeração STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="b48fc-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="b48fc-133">Essas bandeiras controlam a coleta simultânea de lixo, `pwszVersion` o código neutro de domínio e o comportamento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b48fc-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="b48fc-134">O padrão é um único domínio se nenhum sinalizador for definido.</span><span class="sxs-lookup"><span data-stu-id="b48fc-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="b48fc-135">Os seguintes valores são válidos:</span><span class="sxs-lookup"><span data-stu-id="b48fc-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="b48fc-136">Para descrições dessas bandeiras, consulte a [enumeração STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="b48fc-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="b48fc-137">[em] A `CLSID` coclasse que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou a interface [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b48fc-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="b48fc-138">Os valores suportados são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="b48fc-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="b48fc-139">[em] A `IID` da interface solicitada `rclsid`de .</span><span class="sxs-lookup"><span data-stu-id="b48fc-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="b48fc-140">Os valores suportados são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="b48fc-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="b48fc-141">[fora] O ponteiro de `riid`interface retornado para .</span><span class="sxs-lookup"><span data-stu-id="b48fc-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b48fc-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="b48fc-142">Remarks</span></span>  
 <span data-ttu-id="b48fc-143">Se `pwszVersion` especificar uma versão em tempo `CorBindToRuntimeEx` de execução que não existe, retorna um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="b48fc-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="b48fc-144">Contexto de execução e fluxo da identidade do Windows</span><span class="sxs-lookup"><span data-stu-id="b48fc-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="b48fc-145">Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> objeto não flui através de pontos assíncronos, como novos segmentos, pools de segmentos ou retornos de tempo.</span><span class="sxs-lookup"><span data-stu-id="b48fc-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="b48fc-146">Na versão 2.0 do CLR, um <xref:System.Threading.ExecutionContext> objeto envolve algumas informações sobre o segmento em execução atualmente e flui-o através de qualquer ponto assíncrono, mas não através dos limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b48fc-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="b48fc-147">Da mesma <xref:System.Security.Principal.WindowsIdentity> forma, o objeto também flui através de qualquer ponto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b48fc-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="b48fc-148">Portanto, a representação atual no segmento, se houver, também flui.</span><span class="sxs-lookup"><span data-stu-id="b48fc-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="b48fc-149">Você pode alterar o fluxo de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="b48fc-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="b48fc-150">Modificando as <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo por segmento <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A>(ver <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> os métodos e métodos).</span><span class="sxs-lookup"><span data-stu-id="b48fc-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="b48fc-151">Alterando o modo padrão do processo para o <xref:System.Security.Principal.WindowsIdentity> modo de compatibilidade da versão 1, onde <xref:System.Threading.ExecutionContext> o objeto não flui em nenhum ponto assíncrono, independentemente das configurações do segmento atual.</span><span class="sxs-lookup"><span data-stu-id="b48fc-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="b48fc-152">A forma como você altera o modo padrão depende se você usa um executável gerenciado ou uma interface de hospedagem não gerenciada para carregar o CLR:</span><span class="sxs-lookup"><span data-stu-id="b48fc-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="b48fc-153">Para executáveis gerenciados, você `enabled` deve definir o atributo do `true`elemento [ \<legacySPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) para .</span><span class="sxs-lookup"><span data-stu-id="b48fc-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="b48fc-154">Para interfaces de hospedagem `STARTUP_LEGACY_IMPERSONATION` não gerenciadas, defina o sinalizador no parâmetro ao `startupFlags` chamar a `CorBindToRuntimeEx` função.</span><span class="sxs-lookup"><span data-stu-id="b48fc-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="b48fc-155">O modo de compatibilidade da versão 1 aplica-se a todo o processo e a todos os domínios do aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="b48fc-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b48fc-156">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b48fc-156">Requirements</span></span>  
 <span data-ttu-id="b48fc-157">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b48fc-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b48fc-158">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b48fc-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b48fc-159">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b48fc-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b48fc-160">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b48fc-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48fc-161">Confira também</span><span class="sxs-lookup"><span data-stu-id="b48fc-161">See also</span></span>

- [<span data-ttu-id="b48fc-162">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="b48fc-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="b48fc-163">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="b48fc-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="b48fc-164">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="b48fc-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="b48fc-165">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b48fc-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="b48fc-166">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b48fc-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="b48fc-167">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="b48fc-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
