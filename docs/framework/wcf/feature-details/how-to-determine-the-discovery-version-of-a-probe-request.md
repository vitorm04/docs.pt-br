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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ff5d45997456c12d0292176771ad3c332f6c043
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 [Implementando um Proxy de descoberta](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 [Exemplo de Proxy de descoberta](../../../../docs/framework/wcf/samples/discovery-proxy-sample.md)
