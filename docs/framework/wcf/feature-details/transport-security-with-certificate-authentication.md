---
title: Segurança de transporte com autenticação de certificado
description: Saiba mais sobre como o WFC usa certificados para autenticação de servidor e cliente ao usar a segurança de transporte.
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 3da1202a5ad3b953470b50dd5924b2ab45f301eb
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244772"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="58391-103">Segurança de transporte com autenticação de certificado</span><span class="sxs-lookup"><span data-stu-id="58391-103">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="58391-104">Este artigo discute o uso de certificados X. 509 para autenticação de servidor e cliente ao usar a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="58391-104">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="58391-105">Para obter mais informações sobre os certificados X.509, confira [Certificados de chave pública X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="58391-105">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="58391-106">Os certificados devem ser emitidos por uma autoridade de certificação, que geralmente é um emissor de certificados de terceiros.</span><span class="sxs-lookup"><span data-stu-id="58391-106">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="58391-107">Em um domínio do Windows Server, Active Directory serviços de certificados podem ser usados para emitir certificados para computadores cliente no domínio.</span><span class="sxs-lookup"><span data-stu-id="58391-107">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="58391-108">Nesse cenário, o serviço é hospedado em Serviços de Informações da Internet (IIS) que é configurado com protocolo SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="58391-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="58391-109">O serviço é configurado com um certificado SSL (X. 509) para permitir que os clientes verifiquem a identidade do servidor.</span><span class="sxs-lookup"><span data-stu-id="58391-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="58391-110">O cliente também é configurado com um certificado X. 509 que permite que o serviço Verifique a identidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="58391-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="58391-111">O certificado do servidor deve ser confiável pelo cliente e o certificado do cliente deve ser confiável pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="58391-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="58391-112">A mecânica real de como o serviço e o cliente verifica a identidade de cada um está além do escopo deste artigo.</span><span class="sxs-lookup"><span data-stu-id="58391-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="58391-113">Para obter mais informações, consulte [assinatura digital](https://en.wikipedia.org/wiki/Digital_signature) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="58391-113">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="58391-114">Esse cenário implementa um padrão de mensagem de solicitação/resposta, conforme ilustrado pelo diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="58391-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="58391-115">![Transferência segura usando certificados](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="58391-115">![Secure transfer using certificates](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="58391-116">Para obter mais informações sobre como usar um certificado com um serviço, consulte [trabalhando com certificados](working-with-certificates.md) e [como configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="58391-116">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="58391-117">A tabela a seguir descreve as várias características do cenário.</span><span class="sxs-lookup"><span data-stu-id="58391-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="58391-118">Característica</span><span class="sxs-lookup"><span data-stu-id="58391-118">Characteristic</span></span>|<span data-ttu-id="58391-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="58391-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="58391-120">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="58391-120">Security Mode</span></span>|<span data-ttu-id="58391-121">Transporte</span><span class="sxs-lookup"><span data-stu-id="58391-121">Transport</span></span>|  
|<span data-ttu-id="58391-122">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="58391-122">Interoperability</span></span>|<span data-ttu-id="58391-123">Com serviços e clientes de serviços Web existentes.</span><span class="sxs-lookup"><span data-stu-id="58391-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="58391-124">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="58391-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="58391-125">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="58391-125">Authentication (Client)</span></span>|<span data-ttu-id="58391-126">Sim (usando um certificado SSL)</span><span class="sxs-lookup"><span data-stu-id="58391-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="58391-127">Sim (usando um certificado X. 509)</span><span class="sxs-lookup"><span data-stu-id="58391-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="58391-128">Integridade dos Dados</span><span class="sxs-lookup"><span data-stu-id="58391-128">Data Integrity</span></span>|<span data-ttu-id="58391-129">Yes</span><span class="sxs-lookup"><span data-stu-id="58391-129">Yes</span></span>|  
|<span data-ttu-id="58391-130">Confidencialidade dos dados</span><span class="sxs-lookup"><span data-stu-id="58391-130">Data Confidentiality</span></span>|<span data-ttu-id="58391-131">Yes</span><span class="sxs-lookup"><span data-stu-id="58391-131">Yes</span></span>|  
|<span data-ttu-id="58391-132">Transporte</span><span class="sxs-lookup"><span data-stu-id="58391-132">Transport</span></span>|<span data-ttu-id="58391-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="58391-133">HTTPS</span></span>|  
|<span data-ttu-id="58391-134">Associação</span><span class="sxs-lookup"><span data-stu-id="58391-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="58391-135">Configurar o serviço</span><span class="sxs-lookup"><span data-stu-id="58391-135">Configure the Service</span></span>  
 <span data-ttu-id="58391-136">Como o serviço nesse cenário é hospedado no IIS, ele é configurado com um arquivo de web.config.</span><span class="sxs-lookup"><span data-stu-id="58391-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="58391-137">O web.config a seguir mostra como configurar o <xref:System.ServiceModel.WSHttpBinding> para usar a segurança de transporte e as credenciais de cliente X. 509.</span><span class="sxs-lookup"><span data-stu-id="58391-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a><span data-ttu-id="58391-138">Configurar o cliente</span><span class="sxs-lookup"><span data-stu-id="58391-138">Configure the Client</span></span>  
 <span data-ttu-id="58391-139">O cliente pode ser configurado no código ou em um arquivo de app.config.</span><span class="sxs-lookup"><span data-stu-id="58391-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="58391-140">O exemplo a seguir mostra como configurar o cliente no código.</span><span class="sxs-lookup"><span data-stu-id="58391-140">The following example shows how to configure the client in code.</span></span>  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 <span data-ttu-id="58391-141">Como alternativa, você pode configurar o cliente em um arquivo de App.config, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="58391-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58391-142">Veja também</span><span class="sxs-lookup"><span data-stu-id="58391-142">See also</span></span>

- [<span data-ttu-id="58391-143">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="58391-143">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="58391-144">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="58391-144">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
