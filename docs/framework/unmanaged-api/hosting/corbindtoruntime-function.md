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
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176507"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="dd8b4-102">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="dd8b4-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="dd8b4-103">Habilita hosts não gerenciados para carregar o tempo de execução do idioma comum (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="dd8b4-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd8b4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd8b4-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd8b4-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd8b4-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="dd8b4-107">[em] Uma seqüência descrevendo a versão do CLR que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="dd8b4-108">Um número de versão no Quadro .NET consiste em quatro partes separadas por períodos: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="dd8b4-109">A seqüência passou como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número da versão (por exemplo, "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="dd8b4-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="dd8b4-110">Algumas versões do CLR são instaladas com uma declaração de política que especifica compatibilidade com versões anteriores da CLR.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="dd8b4-111">Por padrão, o shim `pwszVersion` de inicialização avalia contra as instruções de diretiva e carrega a versão mais recente do tempo de execução compatível com a versão que está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="dd8b4-112">Um host pode forçar o shim a pular a `pwszVersion` avaliação da diretiva `STARTUP_LOADER_SAFEMODE` e `flags` carregar a versão exata especificada, passando um valor para o parâmetro, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="dd8b4-113">Se o chamador `pwszVersion`especificar nulo para , a versão mais recente do tempo de execução será carregada.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="dd8b4-114">Passar nulo não dá ao host controle sobre qual versão do tempo de execução é carregada.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="dd8b4-115">Embora essa abordagem possa ser apropriada em alguns cenários, é fortemente recomendável que o host forneça uma versão específica para carregar.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="dd8b4-116">[em] Uma seqüência que especifica se deve carregar o servidor ou a compilação da estação de trabalho da CLR.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="dd8b4-117">Os valores válidos são `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="dd8b4-118">A compilação do servidor é otimizada para tirar proveito de vários processadores para coleta de lixo, e a construção da estação de trabalho é otimizada para aplicativos clientes em execução em uma máquina de processador único.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="dd8b4-119">Se `pwszBuildFlavor` estiver definido como nulo, a construção da estação de trabalho está carregada.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="dd8b4-120">Ao ser executado em uma máquina de processador único, a `pwszBuildFlavor` compilação `svr`da estação de trabalho está sempre carregada, mesmo que esteja configurada para .</span><span class="sxs-lookup"><span data-stu-id="dd8b4-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="dd8b4-121">No entanto, `pwszBuildFlavor` `svr` se for definida a coleta de lixo `flags` simultânea (veja a descrição do parâmetro), a compilação do servidor será carregada.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="dd8b4-122">[em] A `CLSID` coclasse que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou a interface [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="dd8b4-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="dd8b4-123">Os valores suportados são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="dd8b4-124">[em] A `IID` da interface solicitada `rclsid`de .</span><span class="sxs-lookup"><span data-stu-id="dd8b4-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="dd8b4-125">Os valores suportados são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="dd8b4-126">[fora] O ponteiro de `riid`interface retornado para .</span><span class="sxs-lookup"><span data-stu-id="dd8b4-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd8b4-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd8b4-127">Remarks</span></span>  
 <span data-ttu-id="dd8b4-128">Se `pwszVersion` especificar uma versão em tempo `CorBindToRuntimeEx` de execução que não existe, retorna um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="dd8b4-129">Contexto de execução e fluxo da identidade do Windows</span><span class="sxs-lookup"><span data-stu-id="dd8b4-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="dd8b4-130">Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> objeto não flui através de pontos assíncronos, como novos segmentos, pools de segmentos ou retornos de tempo.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="dd8b4-131">Na versão 2.0 do CLR, um <xref:System.Threading.ExecutionContext> objeto envolve algumas informações sobre o segmento em execução atualmente e flui-o através de qualquer ponto assíncrono, mas não através dos limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="dd8b4-132">Da mesma <xref:System.Security.Principal.WindowsIdentity> forma, o objeto também flui através de qualquer ponto assíncrono.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="dd8b4-133">Portanto, a representação atual no segmento, se houver, também flui.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="dd8b4-134">Você pode alterar o fluxo de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="dd8b4-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="dd8b4-135">Modificando as <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo por segmento <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A>(ver <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> os métodos e métodos).</span><span class="sxs-lookup"><span data-stu-id="dd8b4-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="dd8b4-136">Alterando o modo padrão do processo para o <xref:System.Security.Principal.WindowsIdentity> modo de compatibilidade da versão 1, onde <xref:System.Threading.ExecutionContext> o objeto não flui em nenhum ponto assíncrono, independentemente das configurações do segmento atual.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="dd8b4-137">A forma como você altera o modo padrão depende se você usa um executável gerenciado ou uma interface de hospedagem não gerenciada para carregar o CLR:</span><span class="sxs-lookup"><span data-stu-id="dd8b4-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="dd8b4-138">Para executáveis gerenciados, você `enabled` deve definir o atributo do `true`elemento [ \<legacySPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) para .</span><span class="sxs-lookup"><span data-stu-id="dd8b4-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="dd8b4-139">Para interfaces de hospedagem `STARTUP_LEGACY_IMPERSONATION` não gerenciadas, defina o sinalizador no parâmetro ao `flags` chamar a `CorBindToRuntimeEx` função.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="dd8b4-140">O modo de compatibilidade da versão 1 aplica-se a todo o processo e a todos os domínios do aplicativo no processo.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd8b4-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd8b4-141">Remarks</span></span>  
 <span data-ttu-id="dd8b4-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` e executar a mesma `CorBindToRuntimeEx` operação, mas a função permite definir sinalizadores para especificar o comportamento da CLR.</span><span class="sxs-lookup"><span data-stu-id="dd8b4-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd8b4-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd8b4-143">Requirements</span></span>  
 <span data-ttu-id="dd8b4-144">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd8b4-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd8b4-145">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dd8b4-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd8b4-146">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="dd8b4-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd8b4-147">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd8b4-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8b4-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd8b4-148">See also</span></span>

- [<span data-ttu-id="dd8b4-149">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="dd8b4-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="dd8b4-150">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="dd8b4-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="dd8b4-151">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="dd8b4-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="dd8b4-152">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="dd8b4-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="dd8b4-153">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="dd8b4-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="dd8b4-154">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="dd8b4-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
