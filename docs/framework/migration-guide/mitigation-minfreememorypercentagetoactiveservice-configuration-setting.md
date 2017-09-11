---
title: "Mitigação: configuração minFreeMemoryPercentageToActiveService"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7875f26-0da8-4afe-9846-7a21778f757b
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f7f228890476d45517a21bc09806538139c5e389
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-minfreememorypercentagetoactiveservice-configuration-setting"></a><span data-ttu-id="3569a-102">Mitigação: configuração minFreeMemoryPercentageToActiveService</span><span class="sxs-lookup"><span data-stu-id="3569a-102">Mitigation: minFreeMemoryPercentageToActiveService Configuration Setting</span></span>
<span data-ttu-id="3569a-103">No [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], uma exceção será acionada se a memória disponível no servidor Web for menor que a porcentagem especificada pela definição de configuração [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).</span><span class="sxs-lookup"><span data-stu-id="3569a-103">In the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], an exception is thrown if the available memory on the web server is less than the percentage specified by the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) configuration setting.</span></span> <span data-ttu-id="3569a-104">No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], essa configuração foi ignorada.</span><span class="sxs-lookup"><span data-stu-id="3569a-104">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], this setting was ignored.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3569a-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="3569a-105">Impact</span></span>  
 <span data-ttu-id="3569a-106">Na maioria dos casos, o impacto de observar a configuração [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) é desejável: ela melhora a estabilidade do sistema, evitando as exceções <xref:System.OutOfMemoryException> que podem ocorrer quando um serviço do WCF (Windows Communication Foundation) é iniciado em um sistema com memória restrita.</span><span class="sxs-lookup"><span data-stu-id="3569a-106">In most cases, the impact of observing the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) setting is desirable: It improves system stability by preventing the <xref:System.OutOfMemoryException> exceptions that can occur when a Windows Communication Foundation (WCF) service is started on a system that has constrained memory.</span></span>  
  
 <span data-ttu-id="3569a-107">No entanto, em alguns casos, um serviço que iniciava anteriormente com êxito talvez não consiga ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="3569a-107">However, in some cases, a service that previously started successfully may be unable to start.</span></span> <span data-ttu-id="3569a-108">Nesse caso, uma mensagem de erro detalhada é exibida:</span><span class="sxs-lookup"><span data-stu-id="3569a-108">In that case, a detailed error message appears:</span></span>  
  
```console
Memory gates checking failed because the free memory (nnnn bytes) is less than nn% of total memory. As a result, the service will not be available for incoming requests. To resolve this, either reduce the load on the machine or adjust the value of minFreeMemoryPercentageToActivateService on the serviceHostingEnvironment config element.
```
  
## <a name="mitigation"></a><span data-ttu-id="3569a-109">Redução</span><span class="sxs-lookup"><span data-stu-id="3569a-109">Mitigation</span></span>  
 <span data-ttu-id="3569a-110">Para reverter para o comportamento anterior em que a configuração [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) foi ignorada, modifique o arquivo web.config da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="3569a-110">To revert to the previous behavior where the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) setting was ignored, modify the web.config file as follows:</span></span>  
  
```xml
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"   
                           minFreeMemoryPercentageToActivateService="0">  
   <serviceActivations>  
   ...  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3569a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3569a-111">See Also</span></span>  
 [<span data-ttu-id="3569a-112">Alterações no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3569a-112">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

