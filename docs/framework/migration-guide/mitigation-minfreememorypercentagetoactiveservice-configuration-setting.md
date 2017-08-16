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
# <a name="mitigation-minfreememorypercentagetoactiveservice-configuration-setting"></a>Mitigação: configuração minFreeMemoryPercentageToActiveService
No [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], uma exceção será acionada se a memória disponível no servidor Web for menor que a porcentagem especificada pela definição de configuração [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md). No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], essa configuração foi ignorada.  
  
## <a name="impact"></a>Impacto  
 Na maioria dos casos, o impacto de observar a configuração [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) é desejável: ela melhora a estabilidade do sistema, evitando as exceções <xref:System.OutOfMemoryException> que podem ocorrer quando um serviço do WCF (Windows Communication Foundation) é iniciado em um sistema com memória restrita.  
  
 No entanto, em alguns casos, um serviço que iniciava anteriormente com êxito talvez não consiga ser iniciado. Nesse caso, uma mensagem de erro detalhada é exibida:  
  
```console
Memory gates checking failed because the free memory (nnnn bytes) is less than nn% of total memory. As a result, the service will not be available for incoming requests. To resolve this, either reduce the load on the machine or adjust the value of minFreeMemoryPercentageToActivateService on the serviceHostingEnvironment config element.
```
  
## <a name="mitigation"></a>Redução  
 Para reverter para o comportamento anterior em que a configuração [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) foi ignorada, modifique o arquivo web.config da seguinte forma:  
  
```xml
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"   
                           minFreeMemoryPercentageToActivateService="0">  
   <serviceActivations>  
   ...  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

