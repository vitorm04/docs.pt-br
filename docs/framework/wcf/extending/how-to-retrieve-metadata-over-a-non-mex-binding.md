---
title: 'Como: recuperar metadados através de uma associação não MEX'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 6cd6e0ce5dc287c826179c152b989b5f7842bb6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795577"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="638a6-102">Como: recuperar metadados através de uma associação não MEX</span><span class="sxs-lookup"><span data-stu-id="638a6-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="638a6-103">Este tópico descreve como recuperar metadados de um ponto de extremidade MEX em uma associação não MEX.</span><span class="sxs-lookup"><span data-stu-id="638a6-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="638a6-104">O código neste exemplo é baseado no exemplo de [ponto de extremidade de metadados seguro personalizado](../samples/custom-secure-metadata-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="638a6-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="638a6-105">Para recuperar metadados em uma associação não-MEX</span><span class="sxs-lookup"><span data-stu-id="638a6-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="638a6-106">Determine a associação usada pelo ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="638a6-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="638a6-107">Para serviços de Windows Communication Foundation (WCF), você pode determinar a associação MEX acessando o arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="638a6-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="638a6-108">Nesse caso, a associação MEX é definida na configuração de serviço a seguir.</span><span class="sxs-lookup"><span data-stu-id="638a6-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
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
  
2. <span data-ttu-id="638a6-109">No arquivo de configuração do cliente, configure a mesma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="638a6-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="638a6-110">Aqui, o cliente também define `clientCredentials` um comportamento para fornecer um certificado a ser usado para autenticar o serviço ao solicitar metadados do ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="638a6-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="638a6-111">Ao usar svcutil. exe para solicitar metadados em uma associação personalizada, você deve adicionar a configuração do ponto de extremidade MEX ao arquivo de configuração para SvcUtil. exe (svcutil. exe. config) e o nome da configuração do ponto de extremidade deve corresponder ao esquema de URI do endereço de o ponto de extremidade MEX, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="638a6-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
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
  
3. <span data-ttu-id="638a6-112">Crie uma `MetadataExchangeClient` chamada `GetMetadata`e.</span><span class="sxs-lookup"><span data-stu-id="638a6-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="638a6-113">Há duas maneiras de fazer isso: você pode especificar a associação personalizada na configuração ou pode especificar a associação personalizada no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="638a6-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
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
  
4. <span data-ttu-id="638a6-114">Crie um `WsdlImporter` e chame `ImportAllEndpoints`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="638a6-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="638a6-115">Neste ponto, você tem uma coleção de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="638a6-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="638a6-116">Para obter mais informações sobre como importar metadados [, consulte Como: Importe metadados em pontos de extremidade](../feature-details/how-to-import-metadata-into-service-endpoints.md)de serviço.</span><span class="sxs-lookup"><span data-stu-id="638a6-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638a6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="638a6-117">See also</span></span>

- [<span data-ttu-id="638a6-118">Metadados</span><span class="sxs-lookup"><span data-stu-id="638a6-118">Metadata</span></span>](../feature-details/metadata.md)
