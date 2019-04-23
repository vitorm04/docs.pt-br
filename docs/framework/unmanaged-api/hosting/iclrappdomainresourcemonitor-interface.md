---
title: Interface ICLRAppDomainResourceMonitor
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15bdbc001838e3d13a9789c8f54daa80f3b6ef9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219818"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="7ebdb-102">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="7ebdb-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="7ebdb-103">Fornece métodos que inspecionam a memória e uso da CPU de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ebdb-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ebdb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7ebdb-104">Methods</span></span>  
  
|<span data-ttu-id="7ebdb-105">Método</span><span class="sxs-lookup"><span data-stu-id="7ebdb-105">Method</span></span>|<span data-ttu-id="7ebdb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ebdb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ebdb-107">Método GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="7ebdb-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="7ebdb-108">Obtém o tamanho total, em bytes, de todas as alocações de memória que foram feitas pelo domínio do aplicativo, pois ele foi criado, sem subtrair a memória que foi coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="7ebdb-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="7ebdb-109">Método GetCurrentSurvived</span><span class="sxs-lookup"><span data-stu-id="7ebdb-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="7ebdb-110">Obtém o número de bytes que sobreviveram o última completo, bloqueio de coleta de lixo e que são referenciados pelo domínio do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="7ebdb-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="7ebdb-111">Método GetCurrentCpuTime</span><span class="sxs-lookup"><span data-stu-id="7ebdb-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="7ebdb-112">Obtém o tempo total do processador que foi usado por todos os threads durante a execução no domínio do aplicativo atual, desde que o domínio do aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="7ebdb-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ebdb-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ebdb-113">Remarks</span></span>  
 <span data-ttu-id="7ebdb-114">O `ICLRAppDomainResourceMonitor` interface fornece funcionalidade semelhante para as seguintes propriedades gerenciadas:</span><span class="sxs-lookup"><span data-stu-id="7ebdb-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="7ebdb-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ebdb-115">Requirements</span></span>  
 <span data-ttu-id="7ebdb-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ebdb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ebdb-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7ebdb-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7ebdb-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7ebdb-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ebdb-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ebdb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebdb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ebdb-120">See also</span></span>

- [<span data-ttu-id="7ebdb-121">\<appDomainResourceMonitoring > elemento</span><span class="sxs-lookup"><span data-stu-id="7ebdb-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="7ebdb-122">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="7ebdb-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="7ebdb-123">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="7ebdb-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7ebdb-124">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="7ebdb-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
