---
title: Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: aea88430d8f83234a1568bcaf433c2a75492e23a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195922"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="97499-102">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="97499-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="97499-103">Esta seção descreve as interfaces que os hosts não gerenciados podem usar para integrar o Common Language Runtime (CLR) no .NET Framework 4, .NET Framework 4,5 e versões posteriores em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="97499-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="97499-104">Essas interfaces fornecem métodos para um host configurar e carregar o tempo de execução em um processo.</span><span class="sxs-lookup"><span data-stu-id="97499-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="97499-105">A partir do .NET Framework 4, todas as interfaces de hospedagem têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="97499-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="97499-106">Eles usam o gerenciamento de tempo de vida (`AddRef` e `Release`), encapsulamento (contexto implícito) e `QueryInterface` de COM.</span><span class="sxs-lookup"><span data-stu-id="97499-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="97499-107">Eles não usam tipos COM, como `BSTR`, `SAFEARRAY`ou `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="97499-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="97499-108">Não há modelos de apartamento, agregação ou ativação de registro que usam a [função CoCreateInstance](https://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="97499-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](https://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97499-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="97499-109">In This Section</span></span>  
 [<span data-ttu-id="97499-110">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="97499-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="97499-111">Fornece métodos que inspecionam o uso de memória e CPU de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97499-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="97499-112">Interface ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="97499-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="97499-113">Permite que o host especifique o Gerenciador de domínio de aplicativo que será usado para inicializar o domínio de aplicativo padrão e para especificar as propriedades de inicialização.</span><span class="sxs-lookup"><span data-stu-id="97499-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="97499-114">Interface ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="97499-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="97499-115">Fornece o método [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) , que permite que um host defina o tamanho do segmento de coleta de lixo e o tamanho máximo da geração 0 do sistema de coleta de lixo com valores maiores que `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="97499-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="97499-116">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="97499-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="97499-117">Fornece métodos que retornam uma versão específica do CLR, listam todos os CLRs instalados, listam todos os tempos de execução em processo, retornam a interface de ativação e detectam a versão do CLR usada para compilar um assembly.</span><span class="sxs-lookup"><span data-stu-id="97499-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="97499-118">Interface ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="97499-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="97499-119">Fornece o método [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) que fornece uma interface CLR baseada em critérios de política, assembly gerenciado, versão e arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="97499-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="97499-120">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="97499-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="97499-121">Fornece métodos que retornam informações sobre um tempo de execução específico, incluindo versão, diretório e status de carregamento.</span><span class="sxs-lookup"><span data-stu-id="97499-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="97499-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="97499-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="97499-123">Fornece funções estáticas globais básicas para assinar assemblies com nomes fortes.</span><span class="sxs-lookup"><span data-stu-id="97499-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="97499-124">Todos os métodos [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) retornam o padrão com HResults.</span><span class="sxs-lookup"><span data-stu-id="97499-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="97499-125">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="97499-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="97499-126">Fornece a capacidade de criar nomes fortes usando o grupo SHA-2 de algoritmos de hash seguro (SHA-256, SHA-384 e SHA-512).</span><span class="sxs-lookup"><span data-stu-id="97499-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="97499-127">Interface ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="97499-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="97499-128">Fornece toda a funcionalidade da [interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Além disso, o fornece métodos que permitem que as anulações de thread sejam atrasadas no thread atual.</span><span class="sxs-lookup"><span data-stu-id="97499-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="97499-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="97499-129">Related Sections</span></span>  
 [<span data-ttu-id="97499-130">Interfaces e coclasses de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="97499-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="97499-131">Descreve as interfaces de hospedagem fornecidas com as versões 1,0 e 1,1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97499-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="97499-132">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="97499-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="97499-133">Descreve as interfaces de hospedagem fornecidas com as .NET Framework versões 2,0, 3,0 e 3,5.</span><span class="sxs-lookup"><span data-stu-id="97499-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="97499-134">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="97499-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="97499-135">Apresenta a hospedagem no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97499-135">Introduces hosting in the .NET Framework.</span></span>
