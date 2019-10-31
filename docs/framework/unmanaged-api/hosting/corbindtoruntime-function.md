---
title: Função CorBindToRuntime
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 9d4b8bb7d5b3da15f665849c8d18c3a10dbe600b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138305"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="9cfaa-102">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="9cfaa-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="9cfaa-103">Permite que hosts não gerenciados carreguem o Common Language Runtime (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="9cfaa-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cfaa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9cfaa-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cfaa-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9cfaa-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="9cfaa-107">no Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="9cfaa-108">Um número de versão no .NET Framework consiste em quatro partes separadas por pontos: *Major. Minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="9cfaa-109">A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número de versão (por exemplo, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="9cfaa-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="9cfaa-110">Algumas versões do CLR são instaladas com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="9cfaa-111">Por padrão, o Shim de inicialização avalia `pwszVersion` em relação a instruções de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="9cfaa-112">Um host pode forçar o Shim a ignorar a avaliação da política e carregar a versão exata especificada em `pwszVersion` passando um valor de `STARTUP_LOADER_SAFEMODE` para o parâmetro `flags`, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="9cfaa-113">Se o chamador especificar NULL para `pwszVersion`, a versão mais recente do tempo de execução será carregada.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="9cfaa-114">A passagem de NULL fornece ao host nenhum controle sobre qual versão do tempo de execução está carregada.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="9cfaa-115">Embora essa abordagem possa ser apropriada em alguns cenários, é altamente recomendável que o host forneça uma versão específica para carregar.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="9cfaa-116">no Uma cadeia de caracteres que especifica se o servidor ou a compilação da estação de trabalho do CLR deve ser carregada.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="9cfaa-117">Os valores válidos são `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="9cfaa-118">A compilação do servidor é otimizada para aproveitar vários processadores para coletas de lixo e a compilação da estação de trabalho é otimizada para aplicativos cliente em execução em um computador com um único processador.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="9cfaa-119">Se `pwszBuildFlavor` for definido como NULL, a compilação da estação de trabalho será carregada.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="9cfaa-120">Durante a execução em um computador com um único processador, a compilação da estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` estiver definida como `svr`.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="9cfaa-121">No entanto, se `pwszBuildFlavor` for definido como `svr` e a coleta de lixo simultânea for especificada (consulte a descrição do parâmetro `flags`), a compilação do servidor será carregada.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9cfaa-122">no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9cfaa-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9cfaa-123">Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9cfaa-124">no A `IID` da interface solicitada do `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="9cfaa-125">Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9cfaa-126">fora O ponteiro de interface retornado para `riid`.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cfaa-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="9cfaa-127">Remarks</span></span>  
 <span data-ttu-id="9cfaa-128">Se `pwszVersion` especificar uma versão de tempo de execução que não existe, `CorBindToRuntimeEx` retornará um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="9cfaa-129">Contexto de execução e fluxo de identidade do Windows</span><span class="sxs-lookup"><span data-stu-id="9cfaa-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="9cfaa-130">Na versão 1 do CLR, o objeto <xref:System.Security.Principal.WindowsIdentity> não flui em pontos assíncronos, como novos threads, pools de threads ou retornos de chamada de temporizador.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="9cfaa-131">Na versão 2,0 do CLR, um objeto <xref:System.Threading.ExecutionContext> encapsula algumas informações sobre o thread em execução no momento e o flui em qualquer ponto assíncrono, mas não entre os limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="9cfaa-132">Da mesma forma, o objeto <xref:System.Security.Principal.WindowsIdentity> também flui em qualquer ponto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="9cfaa-133">Portanto, a representação atual no thread, se houver, flui também.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="9cfaa-134">Você pode alterar o fluxo de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="9cfaa-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="9cfaa-135">Modificando as configurações de <xref:System.Threading.ExecutionContext> para suprimir o fluxo por thread (consulte os métodos <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>).</span><span class="sxs-lookup"><span data-stu-id="9cfaa-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="9cfaa-136">Alterando o modo padrão do processo para o modo de compatibilidade da versão 1, em que o objeto <xref:System.Security.Principal.WindowsIdentity> não flui em nenhum ponto assíncrono, independentemente das configurações de <xref:System.Threading.ExecutionContext> no thread atual.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="9cfaa-137">A maneira como você altera o modo padrão depende se você usa um executável gerenciado ou uma interface de hospedagem não gerenciada para carregar o CLR:</span><span class="sxs-lookup"><span data-stu-id="9cfaa-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="9cfaa-138">Para executáveis gerenciados, você deve definir o atributo `enabled` do elemento [\<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) como `true`.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="9cfaa-139">Para interfaces de hospedagem não gerenciadas, defina o sinalizador `STARTUP_LEGACY_IMPERSONATION` no parâmetro `flags` ao chamar a função `CorBindToRuntimeEx`.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="9cfaa-140">O modo de compatibilidade da versão 1 se aplica a todo o processo e a todos os domínios de aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cfaa-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="9cfaa-141">Remarks</span></span>  
 <span data-ttu-id="9cfaa-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e `CorBindToRuntime` executam a mesma operação, mas a função `CorBindToRuntimeEx` permite que você defina sinalizadores para especificar o comportamento do CLR.</span><span class="sxs-lookup"><span data-stu-id="9cfaa-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cfaa-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9cfaa-143">Requirements</span></span>  
 <span data-ttu-id="9cfaa-144">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cfaa-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cfaa-145">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9cfaa-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cfaa-146">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9cfaa-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cfaa-147">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cfaa-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfaa-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cfaa-148">See also</span></span>

- [<span data-ttu-id="9cfaa-149">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="9cfaa-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9cfaa-150">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="9cfaa-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="9cfaa-151">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="9cfaa-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9cfaa-152">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9cfaa-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="9cfaa-153">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9cfaa-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9cfaa-154">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="9cfaa-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
