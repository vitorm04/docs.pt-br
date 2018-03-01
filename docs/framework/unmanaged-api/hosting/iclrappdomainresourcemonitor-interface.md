---
title: Interface ICLRAppDomainResourceMonitor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1bebd39fce4f6aa6f570b3af348332bf7bcc87ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="0b0f0-102">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="0b0f0-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="0b0f0-103">Fornece métodos que Inspecione a memória e a utilização da CPU de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b0f0-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b0f0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0b0f0-104">Methods</span></span>  
  
|<span data-ttu-id="0b0f0-105">Método</span><span class="sxs-lookup"><span data-stu-id="0b0f0-105">Method</span></span>|<span data-ttu-id="0b0f0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b0f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b0f0-107">Método GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="0b0f0-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="0b0f0-108">Obtém o tamanho total, em bytes, de todas as alocações de memória que foram feitas pelo domínio do aplicativo desde que ele foi criado, sem subtrair a memória foi coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="0b0f0-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="0b0f0-109">Método GetCurrentSurvived</span><span class="sxs-lookup"><span data-stu-id="0b0f0-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="0b0f0-110">Obtém o número de bytes que sobreviveram o última completo, bloqueio de coleta de lixo e que são referenciados pelo domínio do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="0b0f0-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="0b0f0-111">Método GetCurrentCpuTime</span><span class="sxs-lookup"><span data-stu-id="0b0f0-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="0b0f0-112">Obtém o tempo total do processador que foi usado por todos os threads em execução no domínio de aplicativo atual, desde que o domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="0b0f0-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b0f0-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b0f0-113">Remarks</span></span>  
 <span data-ttu-id="0b0f0-114">O `ICLRAppDomainResourceMonitor` interface fornece funcionalidade semelhante para as seguintes propriedades gerenciadas:</span><span class="sxs-lookup"><span data-stu-id="0b0f0-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="0b0f0-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b0f0-115">Requirements</span></span>  
 <span data-ttu-id="0b0f0-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b0f0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b0f0-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0b0f0-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0b0f0-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0b0f0-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b0f0-119">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b0f0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0f0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b0f0-120">See Also</span></span>  
 [<span data-ttu-id="0b0f0-121">\<appDomainResourceMonitoring > elemento</span><span class="sxs-lookup"><span data-stu-id="0b0f0-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [<span data-ttu-id="0b0f0-122">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0b0f0-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="0b0f0-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="0b0f0-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="0b0f0-124">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="0b0f0-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
