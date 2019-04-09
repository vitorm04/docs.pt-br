---
title: Segurança de transporte com autenticação de certificado
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: a348fb7989a83ec9ee7903bd38896bedcf86ce3a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074528"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="df96f-102">Segurança de transporte com autenticação de certificado</span><span class="sxs-lookup"><span data-stu-id="df96f-102">Transport Security with Certificate Authentication</span></span>
<span data-ttu-id="df96f-103">Este tópico discute usando certificados X.509 para autenticação de cliente e servidor ao usar a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="df96f-103">This topic discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="df96f-104">Para obter mais informações sobre os certificados X.509, confira [Certificados de chave pública X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="df96f-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="df96f-105">Certificados devem ser emitidos por uma autoridade de certificação, que é geralmente um emissor de terceiros de certificados.</span><span class="sxs-lookup"><span data-stu-id="df96f-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="df96f-106">Em um domínio do Windows Server, Active Directory Certificate Services pode ser usado para emitir certificados para computadores cliente no domínio.</span><span class="sxs-lookup"><span data-stu-id="df96f-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="df96f-107">Para obter mais informações, consulte [serviços de certificados do Windows 2008 R2](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span><span class="sxs-lookup"><span data-stu-id="df96f-107">For more information see [Windows 2008 R2 Certificate Services](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span></span> <span data-ttu-id="df96f-108">Nesse cenário, o serviço está hospedado em serviços de informações da Internet (IIS) que é configurado com Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="df96f-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="df96f-109">O serviço está configurado com um certificado SSL (X.509) para permitir que os clientes verificar a identidade do servidor.</span><span class="sxs-lookup"><span data-stu-id="df96f-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="df96f-110">O cliente também é configurado com um certificado X.509 que permite que o serviço verificar a identidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="df96f-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="df96f-111">O certificado do servidor deve ser confiável pelo cliente e o certificado do cliente deve ser confiável pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="df96f-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="df96f-112">A mecânica real de como o serviço e o cliente verifica a identidade um do outro está além do escopo deste tópico.</span><span class="sxs-lookup"><span data-stu-id="df96f-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this topic.</span></span> <span data-ttu-id="df96f-113">Para obter mais informações, consulte [Assinatura Digital na Wikipédia](https://go.microsoft.com/fwlink/?LinkId=253157).</span><span class="sxs-lookup"><span data-stu-id="df96f-113">For more information see [Digital Signature on Wikipedia](https://go.microsoft.com/fwlink/?LinkId=253157).</span></span>  
  
 <span data-ttu-id="df96f-114">Esse cenário implementa um padrão de mensagem de solicitação/resposta, conforme ilustrado pelo diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="df96f-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="df96f-115">![Transferência segura usando certificados](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="df96f-115">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="df96f-116">Para obter mais informações sobre como usar um certificado com um serviço, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) e [como: Configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="df96f-116">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="df96f-117">A tabela a seguir descreve várias características do cenário.</span><span class="sxs-lookup"><span data-stu-id="df96f-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="df96f-118">Característica</span><span class="sxs-lookup"><span data-stu-id="df96f-118">Characteristic</span></span>|<span data-ttu-id="df96f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="df96f-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="df96f-120">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="df96f-120">Security Mode</span></span>|<span data-ttu-id="df96f-121">Transporte</span><span class="sxs-lookup"><span data-stu-id="df96f-121">Transport</span></span>|  
|<span data-ttu-id="df96f-122">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="df96f-122">Interoperability</span></span>|<span data-ttu-id="df96f-123">Com serviços e clientes de serviço Web existentes.</span><span class="sxs-lookup"><span data-stu-id="df96f-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="df96f-124">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="df96f-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="df96f-125">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="df96f-125">Authentication (Client)</span></span>|<span data-ttu-id="df96f-126">Sim (usando um certificado SSL)</span><span class="sxs-lookup"><span data-stu-id="df96f-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="df96f-127">Sim (usando um certificado x. 509)</span><span class="sxs-lookup"><span data-stu-id="df96f-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="df96f-128">Integridade de dados</span><span class="sxs-lookup"><span data-stu-id="df96f-128">Data Integrity</span></span>|<span data-ttu-id="df96f-129">Sim</span><span class="sxs-lookup"><span data-stu-id="df96f-129">Yes</span></span>|  
|<span data-ttu-id="df96f-130">Confidencialidade de dados</span><span class="sxs-lookup"><span data-stu-id="df96f-130">Data Confidentiality</span></span>|<span data-ttu-id="df96f-131">Sim</span><span class="sxs-lookup"><span data-stu-id="df96f-131">Yes</span></span>|  
|<span data-ttu-id="df96f-132">Transporte</span><span class="sxs-lookup"><span data-stu-id="df96f-132">Transport</span></span>|<span data-ttu-id="df96f-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="df96f-133">HTTPS</span></span>|  
|<span data-ttu-id="df96f-134">Associação</span><span class="sxs-lookup"><span data-stu-id="df96f-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="df96f-135">Configurar o serviço</span><span class="sxs-lookup"><span data-stu-id="df96f-135">Configure the Service</span></span>  
 <span data-ttu-id="df96f-136">Uma vez que o serviço nesse cenário é hospedado no IIS, ele é configurado com um arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="df96f-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="df96f-137">O Web. config seguinte mostra como configurar o <xref:System.ServiceModel.WSHttpBinding> usar segurança de transporte e as credenciais do cliente x. 509.</span><span class="sxs-lookup"><span data-stu-id="df96f-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="df96f-138">Configurar o cliente</span><span class="sxs-lookup"><span data-stu-id="df96f-138">Configure the Client</span></span>  
 <span data-ttu-id="df96f-139">O cliente pode ser configurado no código ou em um arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="df96f-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="df96f-140">O exemplo a seguir mostra como configurar o cliente no código.</span><span class="sxs-lookup"><span data-stu-id="df96f-140">The following example shows how to configure the client in code.</span></span>  
  
```vb  
// Create the binding.  
WSHttpBinding myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
EndpointAddress ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
CalculatorClient cc =  
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
  
 <span data-ttu-id="df96f-141">Como alternativa, você pode configurar o cliente em um arquivo App. config, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="df96f-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df96f-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df96f-142">See also</span></span>

- [<span data-ttu-id="df96f-143">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="df96f-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="df96f-144">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="df96f-144">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
