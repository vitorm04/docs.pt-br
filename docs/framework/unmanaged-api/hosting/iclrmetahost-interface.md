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
ms.openlocfilehash: 391adc6f9fe55ad7ca527ea416956ab013a27b15
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703730"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="b9613-102">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="b9613-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="b9613-103">Fornece métodos que retornam uma versão específica do Common Language Runtime (CLR) com base em seu número de versão, listar todos os CLRs instalados, listar todos os tempos de execução que são carregados em um processo especificado, descobrir a versão do CLR usada para compilar um assembly, sair de um processo com um desligamento de tempo de execução limpo e consultar Associação de API herdada.</span><span class="sxs-lookup"><span data-stu-id="b9613-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9613-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b9613-104">Methods</span></span>  
  
|<span data-ttu-id="b9613-105">Método</span><span class="sxs-lookup"><span data-stu-id="b9613-105">Method</span></span>|<span data-ttu-id="b9613-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9613-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9613-107">Método EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="b9613-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="b9613-108">Retorna uma enumeração que contém um ponteiro de interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) válido para cada versão do CLR instalada em um computador.</span><span class="sxs-lookup"><span data-stu-id="b9613-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="b9613-109">Método EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="b9613-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="b9613-110">Retorna uma enumeração que contém um ponteiro de interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) válido para cada CLR que é carregado em um determinado processo.</span><span class="sxs-lookup"><span data-stu-id="b9613-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="b9613-111">Esse método substitui [GetVersionFromProcess](getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="b9613-111">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="b9613-112">Método ExitProcess</span><span class="sxs-lookup"><span data-stu-id="b9613-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="b9613-113">Tenta desligar todos os tempos de execução carregados normalmente e, em seguida, encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="b9613-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="b9613-114">Substitui a função [CorExitProcess](corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b9613-114">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="b9613-115">Método GetRuntime</span><span class="sxs-lookup"><span data-stu-id="b9613-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="b9613-116">Obtém a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) que corresponde a uma versão CLR específica.</span><span class="sxs-lookup"><span data-stu-id="b9613-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="b9613-117">Esse método substitui a função [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) usada com o sinalizador [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b9613-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="b9613-118">Método GetVersionFromFile</span><span class="sxs-lookup"><span data-stu-id="b9613-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="b9613-119">Obtém a versão de compilação de .NET Framework original do assembly (armazenada nos metadados), dado seu caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="b9613-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="b9613-120">Esse método substitui [GetFileVersion](getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="b9613-120">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="b9613-121">Método QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="b9613-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="b9613-122">Retorna uma interface que representa um tempo de execução ao qual a política de ativação herdada foi associada, por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo na entrada do arquivo de configuração do [ \< elemento de> de inicialização](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , usando o uso direto das APIs de ativação herdadas ou chamando o método [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b9613-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="b9613-123">Método RequestRuntimeLoadedNotification</span><span class="sxs-lookup"><span data-stu-id="b9613-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="b9613-124">Garante um retorno de chamada para o ponteiro de função especificado quando uma versão do CLR é carregada pela primeira vez, mas ainda não foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="b9613-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="b9613-125">Esse método substitui [LockClrVersion](lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="b9613-125">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9613-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9613-126">Remarks</span></span>  
 <span data-ttu-id="b9613-127">A única maneira de obter uma instância dessa interface é chamando a função [CLRCreateInstance](clrcreateinstance-function.md) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b9613-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b9613-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9613-128">Requirements</span></span>  
 <span data-ttu-id="b9613-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9613-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9613-130">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b9613-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b9613-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9613-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9613-132">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9613-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9613-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="b9613-133">See also</span></span>

- [<span data-ttu-id="b9613-134">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b9613-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="b9613-135">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="b9613-135">Hosting</span></span>](index.md)
