---
title: Como configurar uma associação de intercâmbio de WS-Metadata
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 6459e3f0cf0ab72af8027bd6802a0e7aa574aece
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635793"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Como configurar uma associação de intercâmbio de WS-Metadata

Este artigo explica como configurar uma vinculação personalizada de troca WS-Metadata. O Windows Communication Foundation (WCF) inclui quatro vinculações de metadados definidas pelo sistema, mas você pode publicar metadados usando qualquer vinculação desejada. Este artigo mostra como publicar metadados usando o `wsHttpBinding`. Essa vinculação lhe dá a opção de expor metadados de forma segura. O código deste artigo é baseado no [Getting Started](../samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Usando um arquivo de configuração  
  
1. No arquivo de configuração do serviço, adicione `serviceMetadata` um comportamento de serviço que contenha a tag:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Adicione `behaviorConfiguration` um atributo à tag de serviço que faz referência a esse novo comportamento:  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. Adicione um ponto final de metadados especificando mex como endereço, `wsHttpBinding` como a vinculação e <xref:System.ServiceModel.Description.IMetadataExchange> como contrato:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Para verificar se o ponto final da troca de metadados está funcionando corretamente, adicione uma tag endpoint no arquivo de configuração do cliente:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. No método Principal() do cliente, <xref:System.ServiceModel.Description.MetadataExchangeClient> crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> nova `true`instância, <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> defina sua propriedade para, ligue e, em seguida, iteraatravés da coleta de metadados devolvidos:  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Configuração por código  
  
1. Criar <xref:System.ServiceModel.WSHttpBinding> uma instância vinculante:  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. Criar <xref:System.ServiceModel.ServiceHost> uma instância:  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Adicione um ponto final <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de serviço e adicione uma instância:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Adicionar um ponto final de troca <xref:System.ServiceModel.WSHttpBinding> de metadados, especificando o criado anteriormente:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Para verificar se o ponto final da troca de metadados está funcionando corretamente, adicione uma tag endpoint no arquivo de configuração do cliente:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. No método Principal() do cliente, <xref:System.ServiceModel.Description.MetadataExchangeClient> crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> nova `true`instância, <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> defina a propriedade para, ligue e, em seguida, iteraatravés da coleta de metadados devolvidos:  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Confira também

- [Comportamento de publicação de metadados](../samples/metadata-publishing-behavior.md)
- [Recuperar metadados](../samples/retrieve-metadata.md)
- [Metadados](../feature-details/metadata.md)
- [Publicando metadados](../feature-details/publishing-metadata.md)
- [Publicando pontos de extremidade de metadados](../publishing-metadata-endpoints.md)
