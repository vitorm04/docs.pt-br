---
title: "&lt;extensões&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcfe5c44-04ef-4a20-96a5-90bfadf39623
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 34acc21230650fe5b8da2f81fd176c253c57f69d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltextensionsgt"></a><span data-ttu-id="b43a0-102">&lt;extensões&gt;</span><span class="sxs-lookup"><span data-stu-id="b43a0-102">&lt;extensions&gt;</span></span>
<span data-ttu-id="b43a0-103">Este elemento de configuração contém uma coleção de elementos XML que contêm metadados personalizados a serem publicados juntamente com os metadados detectável padrão (EPR, ContractTypeName, BindingName, escopo e ListenURI).</span><span class="sxs-lookup"><span data-stu-id="b43a0-103">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="b43a0-104">Este é um exemplo do uso desse elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="b43a0-104">The following is an example of using this configuration element.</span></span>  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enable="true">  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b43a0-105">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b43a0-105">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
