---
title: <message> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 62b1793d18ddc8edc1f55b02137c4e0a9f7327d2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738964"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="45f5a-102">\<message> de \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="45f5a-102">\<message> of \<netHttpBinding></span></span>
<span data-ttu-id="45f5a-103">Define as configurações de segurança em nível de mensagem do [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="45f5a-103">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="45f5a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45f5a-104">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45f5a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="45f5a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="45f5a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="45f5a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45f5a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="45f5a-107">Attributes</span></span>  
  
|<span data-ttu-id="45f5a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="45f5a-108">Attribute</span></span>|<span data-ttu-id="45f5a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="45f5a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45f5a-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="45f5a-110">algorithmSuite</span></span>|<span data-ttu-id="45f5a-111">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="45f5a-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="45f5a-112">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> , que especifica os algoritmos e os tamanhos de chave.</span><span class="sxs-lookup"><span data-stu-id="45f5a-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="45f5a-113">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="45f5a-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="45f5a-114">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="45f5a-114">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="45f5a-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="45f5a-115">clientCredentialType</span></span>|<span data-ttu-id="45f5a-116">Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a segurança baseada em mensagem.</span><span class="sxs-lookup"><span data-stu-id="45f5a-116">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="45f5a-117">O padrão é `UserName`.</span><span class="sxs-lookup"><span data-stu-id="45f5a-117">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="45f5a-118">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="45f5a-118">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="45f5a-119">Valor</span><span class="sxs-lookup"><span data-stu-id="45f5a-119">Value</span></span>|<span data-ttu-id="45f5a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="45f5a-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45f5a-121">UserName</span><span class="sxs-lookup"><span data-stu-id="45f5a-121">UserName</span></span>|<span data-ttu-id="45f5a-122">-Requer que o cliente seja autenticado no servidor com uma credencial de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="45f5a-122">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="45f5a-123">Essa credencial precisa ser especificada usando o `clientCredentials` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="45f5a-123">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="45f5a-124">-O WCF não dá suporte ao envio de um resumo de senha ou à derivação de chaves usando senhas e usando essas chaves para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="45f5a-124">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="45f5a-125">Portanto, o WCF impõe que o transporte seja protegido ao usar credenciais de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="45f5a-125">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="45f5a-126">Para o `basicHttpBinding` , isso requer a configuração de um canal SSL.</span><span class="sxs-lookup"><span data-stu-id="45f5a-126">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="45f5a-127">Certificado</span><span class="sxs-lookup"><span data-stu-id="45f5a-127">Certificate</span></span>|<span data-ttu-id="45f5a-128">Requer que o cliente seja autenticado no servidor usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="45f5a-128">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="45f5a-129">Nesse caso, a credencial do cliente precisa ser especificada usando <`clientCredentials`> e a `clientCertificate`> de <.</span><span class="sxs-lookup"><span data-stu-id="45f5a-129">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="45f5a-130">Além disso, ao usar o modo de segurança de mensagem, o cliente precisa ser provisionado com o certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="45f5a-130">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="45f5a-131">Nesse caso, a credencial de serviço precisa ser especificada usando o <xref:System.ServiceModel.Description.ClientCredentials> `ClientCredentials` elemento de classe ou comportamento e especificando o certificado de serviço usando o \<serviceCertificate> elemento de ServiceCredentials.</span><span class="sxs-lookup"><span data-stu-id="45f5a-131">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45f5a-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="45f5a-132">Child Elements</span></span>  
 <span data-ttu-id="45f5a-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="45f5a-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45f5a-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="45f5a-134">Parent Elements</span></span>  
  
|<span data-ttu-id="45f5a-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="45f5a-135">Element</span></span>|<span data-ttu-id="45f5a-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="45f5a-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45f5a-137"><`security`> elemento de <`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="45f5a-137"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="45f5a-138">Define os recursos de segurança para o `netHttpBinding` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="45f5a-138">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45f5a-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45f5a-139">Example</span></span>  
 <span data-ttu-id="45f5a-140">Este exemplo demonstra como implementar um aplicativo que usa a basicHttpBinding e a segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="45f5a-140">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="45f5a-141">No exemplo de configuração a seguir para um serviço, a definição do ponto de extremidade especifica basicHttpBinding e faz referência a uma configuração de associação denominada `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="45f5a-141">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="45f5a-142">O certificado que o serviço usa para se autenticar para o cliente é definido na `behaviors` seção do arquivo de configuração sob o `serviceCredentials` elemento.</span><span class="sxs-lookup"><span data-stu-id="45f5a-142">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="45f5a-143">O modo de validação que se aplica ao certificado que o cliente usa para se autenticar para o serviço também é definido na `behaviors` seção sob o `clientCertificate` elemento.</span><span class="sxs-lookup"><span data-stu-id="45f5a-143">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="45f5a-144">Os mesmos detalhes de ligação e segurança são especificados no arquivo de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="45f5a-144">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- This configuration defines the SecurityMode as Message and
           the clientCredentialType as Certificate. -->
      <binding name="Binding1" >
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
                 is in the user's Trusted People store, then it will be trusted without performing a
                 validation of the certificate's issuer chain. This setting is used here for convenience so that the
                 sample can be run without having to have certificates issued by a certification authority (CA).
                 This setting is less secure than the default, ChainTrust. The security implications of this
                 setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="45f5a-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="45f5a-145">See also</span></span>

- [<span data-ttu-id="45f5a-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="45f5a-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="45f5a-147">Associações</span><span class="sxs-lookup"><span data-stu-id="45f5a-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="45f5a-148">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="45f5a-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="45f5a-149">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="45f5a-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
