---
title: Como configurar uma associação de intercâmbio de WS-Metadata
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 0596e91204a2a9dbaed2fdbe85387ec3785fd3db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Como configurar uma associação de intercâmbio de WS-Metadata
Este tópico explicará como configurar um personalizado WS-Metadata exchange associação. Windows Communication Foundation (WCF) inclui quatro associações de metadados definidos pelo sistema, mas você pode publicar metadados usando a associação que você deseja. Neste tópico mostram como publicar metadados usando o `wsHttpBinding`. Essa associação oferece a opção de exposição de metadados de forma segura. O código neste artigo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Usando um arquivo de configuração  
  
1.  No arquivo de configuração do serviço, adicionar um comportamento de serviço que contém o `serviceMetadata` marca:  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Adicionar um `behaviorConfiguration` atributo à marca do serviço que faz referência a esse novo comportamento:  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  Adicionar um ponto de extremidade de metadados especificando mex como o endereço `wsHttpBinding` como a associação e <xref:System.ServiceModel.Description.IMetadataExchange> do contrato:  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  Para verificar se o ponto de extremidade de troca de metadados é trabalho corretamente adicionar uma marca de ponto de extremidade no arquivo de configuração do cliente:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  No método de Main () do cliente, crie um novo <xref:System.ServiceModel.Description.MetadataExchangeClient> instância, defina seu <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> propriedade `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, percorrer a coleção de metadados retornados:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Configurar o código  
  
1.  Criar um <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> instância de associação:  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  Criar um <xref:System.ServiceModel.ServiceHost> instância:  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  Adicione um ponto de extremidade de serviço e adicione um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  Adicionar um ponto de extremidade de troca de metadados, especificando o <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> criado anteriormente:  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  Para verificar se o ponto de extremidade de troca de metadados está funcionando corretamente, adicione uma marca de ponto de extremidade no arquivo de configuração do cliente:  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  No método de Main () do cliente, crie um novo <xref:System.ServiceModel.Description.MetadataExchangeClient> instância, defina o <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> propriedade `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, percorrer a coleção de metadados retornados:  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Comportamento de publicação de metadados](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [Recuperar metadados](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [Metadados](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Publicando metadados](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [Publicando pontos de extremidade de metadados](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
