---
title: 'Como: recuperar metadados através de uma associação não MEX'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 4a127e3e2283050018705c85606bd7c03c36de8b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345944"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="c655e-102">Como: recuperar metadados através de uma associação não MEX</span><span class="sxs-lookup"><span data-stu-id="c655e-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="c655e-103">Este tópico descreve como recuperar metadados de um ponto de extremidade MEX ao longo de uma associação não MEX.</span><span class="sxs-lookup"><span data-stu-id="c655e-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="c655e-104">O código neste exemplo é baseado na [ponto de extremidade do personalizado proteger metadados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="c655e-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="c655e-105">Para recuperar metadados sobre uma associação não MEX</span><span class="sxs-lookup"><span data-stu-id="c655e-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="c655e-106">Determine a associação usada pelo ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="c655e-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="c655e-107">Para serviços do Windows Communication Foundation (WCF), você pode determinar a associação MEX acessando o arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="c655e-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="c655e-108">Nesse caso, a associação MEX é definida na configuração de serviço a seguir.</span><span class="sxs-lookup"><span data-stu-id="c655e-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
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
  
2. <span data-ttu-id="c655e-109">No arquivo de configuração do cliente, configure a mesma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c655e-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="c655e-110">Aqui o cliente também define um `clientCredentials` comportamento para fornecer um certificado a ser usado para autenticar o serviço ao solicitar metadados do ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="c655e-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="c655e-111">Ao usar Svcutil.exe para solicitar os metadados sobre uma ligação personalizada, você deve adicionar a configuração de ponto de extremidade MEX para o arquivo de configuração para Svcutil.exe (svcutil) e o nome da configuração do ponto de extremidade deve corresponder ao esquema URI do endereço do o ponto de extremidade MEX, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c655e-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
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
  
3. <span data-ttu-id="c655e-112">Criar uma `MetadataExchangeClient` e chamar `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="c655e-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="c655e-113">Há duas maneiras de fazer isso: você pode especificar a associação personalizada na configuração, ou você pode especificar a ligação personalizada no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c655e-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```  
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
  
4. <span data-ttu-id="c655e-114">Criar uma `WsdlImporter` e chamar `ImportAllEndpoints`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c655e-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="c655e-115">Neste ponto, você tem uma coleção de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="c655e-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="c655e-116">Para obter mais informações sobre como importar metadados, consulte [como: Importar metadados para pontos de extremidade de serviço](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="c655e-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c655e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c655e-117">See also</span></span>

- [<span data-ttu-id="c655e-118">Metadados</span><span class="sxs-lookup"><span data-stu-id="c655e-118">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
