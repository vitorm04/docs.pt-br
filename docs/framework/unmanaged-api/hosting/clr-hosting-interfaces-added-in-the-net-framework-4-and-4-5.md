---
title: Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9086502968fb9046237e77b76b4038a9f32f4ef
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253085"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="bed8c-102">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="bed8c-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="bed8c-103">Esta seção descreve as interfaces não gerenciadas hosts podem usar para integrar o common language runtime (CLR) a [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]e em versões posteriores em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bed8c-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], and later versions into their applications.</span></span> <span data-ttu-id="bed8c-104">Essas interfaces fornecem métodos para um host configurar e carregar o tempo de execução em um processo.</span><span class="sxs-lookup"><span data-stu-id="bed8c-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="bed8c-105">Começando com o [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], hospedagem de todas as interfaces têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="bed8c-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
-   <span data-ttu-id="bed8c-106">Usar o gerenciamento da vida útil (`AddRef` e `Release`), o encapsulamento (contexto implícito) e `QueryInterface` de COM.</span><span class="sxs-lookup"><span data-stu-id="bed8c-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
-   <span data-ttu-id="bed8c-107">Há não use tipos COM como `BSTR`, `SAFEARRAY`, ou `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="bed8c-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
-   <span data-ttu-id="bed8c-108">Não há nenhum modelos apartment, agregação ou ativação do registro que usam o [função CoCreateInstance](https://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="bed8c-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](https://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bed8c-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bed8c-109">In This Section</span></span>  
 [<span data-ttu-id="bed8c-110">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="bed8c-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="bed8c-111">Fornece métodos que inspecionam a memória e uso da CPU de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bed8c-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="bed8c-112">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="bed8c-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="bed8c-113">Permite que o host especificar o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar propriedades de inicialização.</span><span class="sxs-lookup"><span data-stu-id="bed8c-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="bed8c-114">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="bed8c-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="bed8c-115">Fornece o [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) método, que permite que um host definir o tamanho do segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0 para valores maiores que `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="bed8c-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="bed8c-116">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="bed8c-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="bed8c-117">Fornece métodos que retornam uma versão específica do CLR, listam todos os CLRs instalados, listam todos os tempos de execução no processo, retornam a interface de ativação e descobrir a versão do CLR usada para compilar um assembly.</span><span class="sxs-lookup"><span data-stu-id="bed8c-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="bed8c-118">Interface ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="bed8c-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="bed8c-119">Fornece o [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método que fornece uma interface CLR com base em critérios de política, assembly gerenciado, versão e arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="bed8c-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="bed8c-120">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="bed8c-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="bed8c-121">Fornece métodos que retornam informações sobre um tempo de execução específica, incluindo a versão, o diretório e o status de carga.</span><span class="sxs-lookup"><span data-stu-id="bed8c-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="bed8c-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bed8c-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="bed8c-123">Fornece funções estáticas globais de básicas para assinar assemblies com nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="bed8c-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="bed8c-124">Todos os [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) métodos retornam HRESULTs de COM padrão.</span><span class="sxs-lookup"><span data-stu-id="bed8c-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="bed8c-125">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="bed8c-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="bed8c-126">Fornece a capacidade de criar usando o grupo de SHA-2 de algoritmos de Hash seguro (SHA-256, SHA-384 e SHA-512) de nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="bed8c-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="bed8c-127">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="bed8c-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="bed8c-128">Fornece a funcionalidade dos [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Além disso, fornece métodos que permitem que as anulações de thread para ser atrasado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="bed8c-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bed8c-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="bed8c-129">Related Sections</span></span>  
 [<span data-ttu-id="bed8c-130">Interfaces e coclasses de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="bed8c-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="bed8c-131">Descreve as interfaces de hospedagem fornecidas com as versões do .NET Framework 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="bed8c-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="bed8c-132">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="bed8c-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="bed8c-133">Descreve as interfaces de hospedagem fornecidas com as versões do .NET Framework 2.0, 3.0 e 3.5.</span><span class="sxs-lookup"><span data-stu-id="bed8c-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="bed8c-134">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="bed8c-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="bed8c-135">Apresenta a hospedagem do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bed8c-135">Introduces hosting in the .NET Framework.</span></span>
