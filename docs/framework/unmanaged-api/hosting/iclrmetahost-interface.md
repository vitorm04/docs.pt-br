---
title: Interface ICLRMetaHost
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1b189b79a02f04b7f795ff2524441f12b053cec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143943"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="53d46-102">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="53d46-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="53d46-103">Fornece métodos que retornam uma versão específica do common language runtime (CLR) com base em seu número de versão, listam todos os CLRs instalados, listam todos os tempos de execução que são carregados em um processo especificado, descobrir a versão do CLR usada para compilar um assembly, sair de um processo com um desligamento limpo do tempo de execução e a associação de consulta herdada da API.</span><span class="sxs-lookup"><span data-stu-id="53d46-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53d46-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="53d46-104">Methods</span></span>  
  
|<span data-ttu-id="53d46-105">Método</span><span class="sxs-lookup"><span data-stu-id="53d46-105">Method</span></span>|<span data-ttu-id="53d46-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="53d46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53d46-107">Método EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="53d46-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="53d46-108">Retorna uma enumeração que contém um válido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ponteiro de interface para cada versão do CLR que é instalado em um computador.</span><span class="sxs-lookup"><span data-stu-id="53d46-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="53d46-109">Método EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="53d46-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="53d46-110">Retorna uma enumeração que contém um válido [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ponteiro de interface para cada CLR que é carregado em um determinado processo.</span><span class="sxs-lookup"><span data-stu-id="53d46-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="53d46-111">Esse método substitui [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="53d46-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="53d46-112">Método ExitProcess</span><span class="sxs-lookup"><span data-stu-id="53d46-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="53d46-113">Tenta desligar normalmente o carregados todos os tempos de execução e, em seguida, encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="53d46-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="53d46-114">Substitui o [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="53d46-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="53d46-115">Método GetRuntime</span><span class="sxs-lookup"><span data-stu-id="53d46-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="53d46-116">Obtém o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que corresponde a uma versão específica do CLR.</span><span class="sxs-lookup"><span data-stu-id="53d46-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="53d46-117">Esse método substitui o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) função usada com o [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sinalizador.</span><span class="sxs-lookup"><span data-stu-id="53d46-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="53d46-118">Método GetVersionFromFile</span><span class="sxs-lookup"><span data-stu-id="53d46-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="53d46-119">Obtém do .NET Framework compilação versão original do assembly (armazenado nos metadados), dado seu caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="53d46-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="53d46-120">Esse método substitui [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="53d46-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="53d46-121">Método QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="53d46-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="53d46-122">Retorna uma interface que representa um tempo de execução para o qual política de ativação herdados foi associada, por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo o [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) entrada do arquivo de configuração, pelo uso direto de APIs de ativação herdadas, ou chamando o [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="53d46-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="53d46-123">Método RequestRuntimeLoadedNotification</span><span class="sxs-lookup"><span data-stu-id="53d46-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="53d46-124">Garante que um retorno de chamada para o ponteiro de função especificado quando uma versão do CLR é carregado pela primeira vez, mas ainda não foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="53d46-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="53d46-125">Esse método substitui [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="53d46-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53d46-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="53d46-126">Remarks</span></span>  
 <span data-ttu-id="53d46-127">A única maneira de obter uma instância dessa interface é chamando o [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funcionam da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="53d46-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="53d46-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53d46-128">Requirements</span></span>  
 <span data-ttu-id="53d46-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53d46-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53d46-130">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="53d46-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="53d46-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="53d46-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="53d46-132">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="53d46-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="53d46-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53d46-133">See also</span></span>

- [<span data-ttu-id="53d46-134">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="53d46-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="53d46-135">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="53d46-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
