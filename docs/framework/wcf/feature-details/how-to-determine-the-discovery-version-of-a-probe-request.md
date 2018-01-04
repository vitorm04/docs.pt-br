---
title: "Como determinar a versão de descoberta de uma solicitação de investigação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f51f48d6eefcc0f8ae5129526477d6e2a5b2385
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>Como determinar a versão de descoberta de uma solicitação de investigação
Um proxy de descoberta pode expor vários pontos de extremidade de descoberta usando versões diferentes de descoberta. Quando um UDP multicast investigação solicitação chega no proxy que do proxy deve responder com uma mensagem de supressão multicast. Para fazer isso seria necessário saber a versão de descoberta da solicitação.  
  
### <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Para determinar a versão de uma solicitação de investigação de descoberta  
  
1.  O método que responde a uma solicitação de investigação (por exemplo <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A>) usar estático <xref:System.ServiceModel.OperationContext.Current%2A> propriedade para pesquisar um <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> conforme mostrado no código a seguir.  
  
    ```  
    DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();  
    // Access the discovery version from the DiscoveryOperationContextExtension  
    doce.DiscoveryVersion;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>  
 [Implementando um proxy de descoberta](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [Exemplo de Proxy de descoberta](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
