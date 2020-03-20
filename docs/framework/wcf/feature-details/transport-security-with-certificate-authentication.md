---
title: Segurança de transporte com autenticação de certificado
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: ad2f0922afbd94e1699b383cf2fc9762771b637d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184326"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="9a07f-102">Segurança de transporte com autenticação de certificado</span><span class="sxs-lookup"><span data-stu-id="9a07f-102">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="9a07f-103">Este artigo discute o uso de certificados X.509 para autenticação de servidor e cliente ao usar a segurança do transporte.</span><span class="sxs-lookup"><span data-stu-id="9a07f-103">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="9a07f-104">Para obter mais informações sobre os certificados X.509, confira [Certificados de chave pública X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="9a07f-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="9a07f-105">Os certificados devem ser emitidos por uma autoridade de certificação, que muitas vezes é um emissor terceirizado de certificados.</span><span class="sxs-lookup"><span data-stu-id="9a07f-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="9a07f-106">Em um domínio do Windows Server, os Serviços de Certificado de Diretório Ativo podem ser usados para emitir certificados para computadores clientes no domínio.</span><span class="sxs-lookup"><span data-stu-id="9a07f-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="9a07f-107">Neste cenário, o serviço está hospedado no Internet Information Services (IIS), que é configurado com Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="9a07f-107">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="9a07f-108">O serviço é configurado com um certificado SSL (X.509) para permitir que os clientes verifiquem a identidade do servidor.</span><span class="sxs-lookup"><span data-stu-id="9a07f-108">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="9a07f-109">O cliente também é configurado com um certificado X.509 que permite que o serviço verifique a identidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="9a07f-109">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="9a07f-110">O certificado do servidor deve ser confiável pelo cliente e o certificado do cliente deve ser confiável pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="9a07f-110">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="9a07f-111">A mecânica real de como o serviço e o cliente verificam a identidade uns dos outros está além do escopo deste artigo.</span><span class="sxs-lookup"><span data-stu-id="9a07f-111">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="9a07f-112">Para obter mais informações, consulte [Assinatura Digital](https://en.wikipedia.org/wiki/Digital_signature) na Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="9a07f-112">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="9a07f-113">Este cenário implementa um padrão de mensagem de solicitação/resposta ilustrado pelo diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="9a07f-113">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="9a07f-114">![Transferência segura usando certificados](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="9a07f-114">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="9a07f-115">Para obter mais informações sobre como usar um certificado com um serviço, consulte [Trabalhando com Certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) e [Como: Configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="9a07f-115">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="9a07f-116">A tabela a seguir descreve as várias características do cenário.</span><span class="sxs-lookup"><span data-stu-id="9a07f-116">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="9a07f-117">Característica</span><span class="sxs-lookup"><span data-stu-id="9a07f-117">Characteristic</span></span>|<span data-ttu-id="9a07f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a07f-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9a07f-119">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="9a07f-119">Security Mode</span></span>|<span data-ttu-id="9a07f-120">Transporte</span><span class="sxs-lookup"><span data-stu-id="9a07f-120">Transport</span></span>|  
|<span data-ttu-id="9a07f-121">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="9a07f-121">Interoperability</span></span>|<span data-ttu-id="9a07f-122">Com clientes e serviços de serviços web existentes.</span><span class="sxs-lookup"><span data-stu-id="9a07f-122">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="9a07f-123">Autenticação (Servidor)</span><span class="sxs-lookup"><span data-stu-id="9a07f-123">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="9a07f-124">Autenticação (Cliente)</span><span class="sxs-lookup"><span data-stu-id="9a07f-124">Authentication (Client)</span></span>|<span data-ttu-id="9a07f-125">Sim (usando um certificado SSL)</span><span class="sxs-lookup"><span data-stu-id="9a07f-125">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="9a07f-126">Sim (usando um certificado X.509)</span><span class="sxs-lookup"><span data-stu-id="9a07f-126">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="9a07f-127">Integridade dos Dados</span><span class="sxs-lookup"><span data-stu-id="9a07f-127">Data Integrity</span></span>|<span data-ttu-id="9a07f-128">Sim</span><span class="sxs-lookup"><span data-stu-id="9a07f-128">Yes</span></span>|  
|<span data-ttu-id="9a07f-129">Confidencialidade de dados</span><span class="sxs-lookup"><span data-stu-id="9a07f-129">Data Confidentiality</span></span>|<span data-ttu-id="9a07f-130">Sim</span><span class="sxs-lookup"><span data-stu-id="9a07f-130">Yes</span></span>|  
|<span data-ttu-id="9a07f-131">Transporte</span><span class="sxs-lookup"><span data-stu-id="9a07f-131">Transport</span></span>|<span data-ttu-id="9a07f-132">HTTPS</span><span class="sxs-lookup"><span data-stu-id="9a07f-132">HTTPS</span></span>|  
|<span data-ttu-id="9a07f-133">Associação</span><span class="sxs-lookup"><span data-stu-id="9a07f-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="9a07f-134">Configure o Serviço</span><span class="sxs-lookup"><span data-stu-id="9a07f-134">Configure the Service</span></span>  
 <span data-ttu-id="9a07f-135">Uma vez que o serviço neste cenário está hospedado no IIS, ele é configurado com um arquivo web.config.</span><span class="sxs-lookup"><span data-stu-id="9a07f-135">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="9a07f-136">A web.config a seguir mostra <xref:System.ServiceModel.WSHttpBinding> como configurar a segurança de transporte e as credenciais do cliente X.509.</span><span class="sxs-lookup"><span data-stu-id="9a07f-136">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="9a07f-137">Configure o Cliente</span><span class="sxs-lookup"><span data-stu-id="9a07f-137">Configure the Client</span></span>  
 <span data-ttu-id="9a07f-138">O cliente pode ser configurado em código ou em um arquivo app.config.</span><span class="sxs-lookup"><span data-stu-id="9a07f-138">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="9a07f-139">O exemplo a seguir mostra como configurar o cliente em código.</span><span class="sxs-lookup"><span data-stu-id="9a07f-139">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="9a07f-140">Alternativamente, você pode configurar o cliente em um arquivo App.config, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9a07f-140">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a07f-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="9a07f-141">See also</span></span>

- [<span data-ttu-id="9a07f-142">Visão geral da segurança</span><span class="sxs-lookup"><span data-stu-id="9a07f-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="9a07f-143">[Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9a07f-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
