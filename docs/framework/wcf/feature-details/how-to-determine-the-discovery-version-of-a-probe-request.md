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
ms.openlocfilehash: 383d96e661ca7872108b40f69be86ef4e1ca63b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
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
