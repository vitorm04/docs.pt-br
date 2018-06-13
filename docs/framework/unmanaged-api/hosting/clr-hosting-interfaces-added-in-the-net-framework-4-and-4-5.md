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
ms.openlocfilehash: 982f5780a40dd8cbce02ec33f7e6f77589cd3717
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435790"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="95413-102">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="95413-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="95413-103">Esta seção descreve as interfaces não gerenciadas hosts podem usar para integrar o common language runtime (CLR) a [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]e em versões posteriores em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="95413-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], and later versions into their applications.</span></span> <span data-ttu-id="95413-104">Essas interfaces fornecem métodos para um host configurar e carregar o tempo de execução em um processo.</span><span class="sxs-lookup"><span data-stu-id="95413-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="95413-105">Começando com o [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], hospedagem de todas as interfaces têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="95413-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
-   <span data-ttu-id="95413-106">Eles usam o gerenciamento de vida útil (`AddRef` e `Release`), encapsulamento (contexto implícito) e `QueryInterface` de COM.</span><span class="sxs-lookup"><span data-stu-id="95413-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
-   <span data-ttu-id="95413-107">Há não usa tipos COM como `BSTR`, `SAFEARRAY`, ou `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="95413-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
-   <span data-ttu-id="95413-108">Não existem modelos apartment, agregação ou a ativação do registro que usam o [função CoCreateInstance](http://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="95413-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](http://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95413-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="95413-109">In This Section</span></span>  
 [<span data-ttu-id="95413-110">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="95413-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="95413-111">Fornece métodos que Inspecione a memória e a utilização da CPU de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95413-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="95413-112">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="95413-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="95413-113">Permite que o host especificar o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar propriedades de inicialização.</span><span class="sxs-lookup"><span data-stu-id="95413-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="95413-114">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="95413-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="95413-115">Fornece o [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) método, o que permite que um host definir o tamanho do segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0 como valores maior `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="95413-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="95413-116">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="95413-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="95413-117">Fornece métodos que retornam uma versão específica do CLR, listam todos os CLRs instalados, listam de todos os tempos de execução no processo, retornam a interface de ativação e descobrir a versão CLR usada para compilar um assembly.</span><span class="sxs-lookup"><span data-stu-id="95413-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="95413-118">Interface ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="95413-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="95413-119">Fornece o [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método que fornece uma interface CLR com base em critérios de política, assembly gerenciado, versão e arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="95413-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="95413-120">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="95413-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="95413-121">Fornece métodos que retornam informações sobre um tempo de execução específica, incluindo a versão, o diretório e o status de carga.</span><span class="sxs-lookup"><span data-stu-id="95413-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="95413-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="95413-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="95413-123">Fornece funções estáticas globais de básicas para assinar assemblies com nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="95413-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="95413-124">Todos os [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) métodos retornam os HRESULTs COM padrão.</span><span class="sxs-lookup"><span data-stu-id="95413-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="95413-125">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="95413-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="95413-126">Fornece a capacidade de criar nomes de alta segurança usando o grupo de SHA-2 de algoritmos de Hash seguro (SHA-256, SHA-384 e SHA-512).</span><span class="sxs-lookup"><span data-stu-id="95413-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="95413-127">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="95413-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="95413-128">Fornece toda a funcionalidade do [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Além disso, fornece métodos que permitem cancelamentos do thread para ser atrasado no thread atual.</span><span class="sxs-lookup"><span data-stu-id="95413-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="95413-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="95413-129">Related Sections</span></span>  
 [<span data-ttu-id="95413-130">Interfaces e coclasses de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="95413-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="95413-131">Descreve as interfaces de hospedagem fornecidas com as versões do .NET Framework 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="95413-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="95413-132">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="95413-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="95413-133">Descreve as interfaces de hospedagem fornecidas com as versões do .NET Framework 2.0, 3.0 e 3.5.</span><span class="sxs-lookup"><span data-stu-id="95413-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="95413-134">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="95413-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="95413-135">Apresenta a hospedagem do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95413-135">Introduces hosting in the .NET Framework.</span></span>
