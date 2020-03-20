---
title: Função CorBindToRuntimeHost
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176481"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="0de64-102">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0de64-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="0de64-103">Permite que os hosts carreguem uma versão especificada do tempo de execução do idioma comum (CLR) em um processo.</span><span class="sxs-lookup"><span data-stu-id="0de64-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="0de64-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="0de64-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de64-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0de64-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,
    [in] LPCWSTR       pwszBuildFlavor,
    [in] LPCWSTR       pwszHostConfigFile,
    [in] VOID*         pReserved,
    [in] DWORD         startupFlags,
    [in] REFCLSID      rclsid,
    [in] REFIID        riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0de64-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="0de64-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="0de64-107">[em] Uma string que descreve a versão do CLR que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="0de64-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="0de64-108">Um número de versão no Quadro .NET consiste em quatro partes separadas por períodos: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="0de64-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="0de64-109">A seqüência passou como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número da versão (por exemplo, "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="0de64-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="0de64-110">Algumas versões do CLR são instaladas com uma declaração de política que especifica compatibilidade com versões anteriores da CLR.</span><span class="sxs-lookup"><span data-stu-id="0de64-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="0de64-111">Por padrão, o shim `pwszVersion` de inicialização avalia contra as instruções de diretiva e carrega a versão mais recente do tempo de execução compatível com a versão que está sendo solicitada.</span><span class="sxs-lookup"><span data-stu-id="0de64-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="0de64-112">Um host pode forçar o shim a pular a `pwszVersion` avaliação da diretiva e `startupFlags` carregar a versão exata especificada, passando um valor de STARTUP_LOADER_SAFEMODE para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0de64-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="0de64-113">Se `pwszVersion` `null,` for o método não carregar nenhuma versão do CLR.</span><span class="sxs-lookup"><span data-stu-id="0de64-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="0de64-114">Em vez disso, ele retorna CLR_E_SHIM_RUNTIMELOAD, o que indica que ele não conseguiu carregar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0de64-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="0de64-115">[em] Uma seqüência que especifica se deve carregar o servidor ou a compilação da estação de trabalho da CLR.</span><span class="sxs-lookup"><span data-stu-id="0de64-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="0de64-116">Os valores válidos são `svr` e `wks`.</span><span class="sxs-lookup"><span data-stu-id="0de64-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="0de64-117">A compilação do servidor é otimizada para tirar proveito de vários processadores para coleta de lixo, e a construção da estação de trabalho é otimizada para aplicativos clientes em execução em uma máquina de processador único.</span><span class="sxs-lookup"><span data-stu-id="0de64-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="0de64-118">Se `pwszBuildFlavor` estiver definido como nulo, a construção da estação de trabalho está carregada.</span><span class="sxs-lookup"><span data-stu-id="0de64-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="0de64-119">Ao ser executado em uma máquina de processador único, a `pwszBuildFlavor` compilação `svr`da estação de trabalho está sempre carregada, mesmo que esteja configurada para .</span><span class="sxs-lookup"><span data-stu-id="0de64-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="0de64-120">No entanto, `pwszBuildFlavor` `svr` se for definida a coleta de lixo `startupFlags` simultânea (veja a descrição do parâmetro), a compilação do servidor será carregada.</span><span class="sxs-lookup"><span data-stu-id="0de64-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0de64-121">A coleta de lixo simultânea não é suportada em aplicativos que executam o emulador WOW64 x86 em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamada iA-64).</span><span class="sxs-lookup"><span data-stu-id="0de64-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="0de64-122">Para obter mais informações sobre como usar o WOW64 em sistemas Windows de 64 [bits, consulte Executando aplicativos de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="0de64-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="0de64-123">[em] O nome de um arquivo de configuração host que especifica a versão do CLR para carregar.</span><span class="sxs-lookup"><span data-stu-id="0de64-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="0de64-124">Se o nome do arquivo não incluir um caminho totalmente qualificado, o arquivo é assumido como sendo no mesmo diretório que o executável que está fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="0de64-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="0de64-125">[em] Reservado para a extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="0de64-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="0de64-126">[em] Um conjunto de bandeiras que controla a coleta de lixo `pwszVersion` simultânea, o código neutro de domínio e o comportamento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0de64-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="0de64-127">O padrão é um único domínio se nenhum sinalizador for definido.</span><span class="sxs-lookup"><span data-stu-id="0de64-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="0de64-128">Para obter uma lista de valores suportados, consulte a [enumeração STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0de64-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="0de64-129">[em] A `CLSID` coclasse que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou a interface [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="0de64-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="0de64-130">Os valores suportados são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0de64-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="0de64-131">[em] A `IID` interface que você está solicitando.</span><span class="sxs-lookup"><span data-stu-id="0de64-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="0de64-132">Os valores suportados são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0de64-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0de64-133">[fora] Um ponteiro de interface para a versão do tempo de execução que foi carregado.</span><span class="sxs-lookup"><span data-stu-id="0de64-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de64-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0de64-134">Requirements</span></span>  
 <span data-ttu-id="0de64-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0de64-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de64-136">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="0de64-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0de64-137">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0de64-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0de64-138">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0de64-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de64-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="0de64-139">See also</span></span>

- [<span data-ttu-id="0de64-140">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="0de64-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="0de64-141">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="0de64-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="0de64-142">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="0de64-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="0de64-143">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="0de64-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="0de64-144">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0de64-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="0de64-145">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="0de64-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
