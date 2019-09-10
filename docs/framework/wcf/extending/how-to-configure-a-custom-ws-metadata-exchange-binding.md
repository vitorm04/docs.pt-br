---
title: 'Como: configurar uma associação personalizada do WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: b4a4005a23c8c74edecb00475669e019b50a17af
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851228"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Como: configurar uma associação personalizada do WS-Metadata Exchange
Este tópico explicará como configurar uma associação de troca personalizada de WS-Metadata. O Windows Communication Foundation (WCF) inclui quatro associações de metadados definidas pelo sistema, mas você pode publicar metadados usando qualquer associação desejada. Este tópico mostrará como publicar metadados usando o `wsHttpBinding`. Essa associação oferece a opção de expor metadados de forma segura. O código neste artigo se baseia na [introdução](../samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Usando um arquivo de configuração  
  
1. No arquivo de configuração do serviço, adicione um comportamento de serviço que contenha a `serviceMetadata` marca:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Adicione um `behaviorConfiguration` atributo à marca de serviço que faz referência a esse novo comportamento:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. Adicione um ponto de extremidade de metadados especificando mex como `wsHttpBinding` o endereço, como a <xref:System.ServiceModel.Description.IMetadataExchange> associação e como o contrato:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Para verificar se o ponto de extremidade de troca de metadados está funcionando corretamente, adicione uma marca de ponto de extremidade no arquivo de configuração do cliente:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. No método Main () do cliente, crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient> nova instância, defina sua <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> Propriedade como `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, itere pela coleção de metadados retornada:  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Configurando por código  
  
1. Criar uma <xref:System.ServiceModel.WSHttpBinding> instância de associação:  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. Criar uma <xref:System.ServiceModel.ServiceHost> instância:  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Adicione um ponto de extremidade de serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e adicione uma instância:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Adicione um ponto de extremidade de troca de <xref:System.ServiceModel.WSHttpBinding> metadados, especificando o criado anteriormente:  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Para verificar se o ponto de extremidade de troca de metadados está funcionando corretamente, adicione uma marca de ponto de extremidade no arquivo de configuração do cliente:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. No método Main () do cliente, crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient> nova instância, defina a <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> Propriedade como `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, itere pela coleção de metadados retornada:  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Comportamento de publicação de metadados](../samples/metadata-publishing-behavior.md)
- [Recuperar metadados](../samples/retrieve-metadata.md)
- [Metadados](../feature-details/metadata.md)
- [Publicando metadados](../feature-details/publishing-metadata.md)
- [Publicando pontos de extremidade de metadados](../publishing-metadata-endpoints.md)
