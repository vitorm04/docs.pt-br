---
title: Como recuperar metadados através de uma associação não MEX
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: a006795c87a2ae845d03db90dce296692c4339fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186443"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Como recuperar metadados através de uma associação não MEX
Este tópico descreve como recuperar metadados de um ponto final Do MEX sobre uma vinculação não-MEX. O código nesta amostra é baseado na amostra Deponto de Ponto Final de [Metadados Personalizados.](../samples/custom-secure-metadata-endpoint.md)  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>Para recuperar metadados sobre uma vinculação não-MEX  
  
1. Determine a vinculação usada pelo ponto final do MEX. Para os serviços da Windows Communication Foundation (WCF), você pode determinar a vinculação do MEX acessando o arquivo de configuração do serviço. Neste caso, a vinculação MEX é definida na seguinte configuração de serviço.  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. No arquivo de configuração do cliente, configure a mesma vinculação personalizada. Aqui o cliente também `clientCredentials` define um comportamento para fornecer um certificado para usar para autenticar o serviço ao solicitar metadados do ponto final do MEX. Ao usar o Svcutil.exe para solicitar metadados em uma vinculação personalizada, você deve adicionar a configuração de ponto final do MEX ao arquivo de configuração de Svcutil.exe (Svcutil.exe.config), e o nome da configuração do ponto final deve corresponder ao esquema URI do endereço de o ponto final MEX, conforme mostrado no código a seguir.  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>
    </system.serviceModel>  
    ```  
  
3. Crie `MetadataExchangeClient` um `GetMetadata`e chame. Há duas maneiras de fazer isso: você pode especificar a vinculação personalizada na configuração, ou pode especificar a vinculação personalizada em código, como mostrado no exemplo a seguir.  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. Crie `WsdlImporter` um `ImportAllEndpoints`e chame, conforme mostrado no código a seguir.  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. Neste ponto, você tem uma coleção de pontos finais de serviço. Para obter mais informações sobre a importação de metadados, consulte [Como importar metadados em pontos finais de serviço](../feature-details/how-to-import-metadata-into-service-endpoints.md).  
  
## <a name="see-also"></a>Confira também

- [Metadados](../feature-details/metadata.md)
