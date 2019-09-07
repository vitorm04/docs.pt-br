---
title: <message> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: bce80d96b1bcec0d580f2de3fe88d5fd6ad0a3b5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400271"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="4b2c1-102">\<> de mensagem \<de BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="4b2c1-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="4b2c1-103">Define as configurações de segurança em nível de mensagem do [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4b2c1-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="4b2c1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b2c1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4b2c1-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4b2c1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4b2c1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4b2c1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4b2c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4b2c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="4b2c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="4b2c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4b2c1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4b2c1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="4b2c1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de mensagem**</span><span class="sxs-lookup"><span data-stu-id="4b2c1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b2c1-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b2c1-111">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b2c1-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4b2c1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4b2c1-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="4b2c1-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b2c1-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4b2c1-114">Attributes</span></span>  
  
|<span data-ttu-id="4b2c1-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="4b2c1-115">Attribute</span></span>|<span data-ttu-id="4b2c1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b2c1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b2c1-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="4b2c1-117">algorithmSuite</span></span>|<span data-ttu-id="4b2c1-118">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="4b2c1-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, que especifica os algoritmos e os tamanhos de chave.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="4b2c1-120">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="4b2c1-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="4b2c1-121">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-121">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="4b2c1-122">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="4b2c1-122">clientCredentialType</span></span>|<span data-ttu-id="4b2c1-123">Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a segurança baseada em mensagem.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-123">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="4b2c1-124">O padrão é `UserName`.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-124">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="4b2c1-125">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="4b2c1-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4b2c1-126">Valor</span><span class="sxs-lookup"><span data-stu-id="4b2c1-126">Value</span></span>|<span data-ttu-id="4b2c1-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b2c1-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b2c1-128">UserName</span><span class="sxs-lookup"><span data-stu-id="4b2c1-128">UserName</span></span>|<span data-ttu-id="4b2c1-129">-Requer que o cliente seja autenticado no servidor com uma credencial de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-129">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="4b2c1-130">Essa credencial precisa ser especificada usando o [ \<> ClientCredentials](clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="4b2c1-130">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="4b2c1-131">-O WCF não dá suporte ao envio de um resumo de senha ou à derivação de chaves usando senhas e usando essas chaves para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-131">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="4b2c1-132">Portanto, o WCF impõe que o transporte seja protegido ao usar credenciais de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-132">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="4b2c1-133">Para o `basicHttpBinding`, isso requer a configuração de um canal SSL.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-133">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="4b2c1-134">Certificate</span><span class="sxs-lookup"><span data-stu-id="4b2c1-134">Certificate</span></span>|<span data-ttu-id="4b2c1-135">Requer que o cliente seja autenticado no servidor usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-135">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="4b2c1-136">Nesse caso, a credencial do cliente precisa ser especificada usando [ \<ClientCredentials >](clientcredentials.md) e o [ \<> clientCertificate](clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="4b2c1-136">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="4b2c1-137">Além disso, ao usar o modo de segurança de mensagem, o cliente precisa ser provisionado com o certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-137">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="4b2c1-138">Nesse caso, a credencial de serviço precisa ser especificada <xref:System.ServiceModel.Description.ClientCredentials> usando o `ClientCredentials` elemento Class ou Behavior e especificando o certificado de serviço usando o [ \<>](servicecertificate-of-servicecredentials.md)do Service-Certificate.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-138">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b2c1-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4b2c1-139">Child Elements</span></span>  
 <span data-ttu-id="4b2c1-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4b2c1-140">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b2c1-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4b2c1-141">Parent Elements</span></span>  
  
|<span data-ttu-id="4b2c1-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="4b2c1-142">Element</span></span>|<span data-ttu-id="4b2c1-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b2c1-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b2c1-144">\<security></span><span class="sxs-lookup"><span data-stu-id="4b2c1-144">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="4b2c1-145">Define os recursos de segurança para o [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4b2c1-145">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4b2c1-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4b2c1-146">Example</span></span>  
 <span data-ttu-id="4b2c1-147">Este exemplo demonstra como implementar um aplicativo que usa a basicHttpBinding e a segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-147">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="4b2c1-148">No exemplo de configuração a seguir para um serviço, a definição do ponto de extremidade especifica basicHttpBinding e faz referência `Binding1`a uma configuração de associação denominada.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-148">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="4b2c1-149">O certificado que o serviço usa para se autenticar para o cliente é definido na `behaviors` seção do arquivo de configuração sob o `serviceCredentials` elemento.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-149">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="4b2c1-150">O modo de validação que se aplica ao certificado que o cliente usa para se autenticar para o serviço também é definido `behaviors` na seção sob `clientCertificate` o elemento.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-150">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="4b2c1-151">Os mesmos detalhes de ligação e segurança são especificados no arquivo de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="4b2c1-151">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service -->
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
      <binding name="Binding1">
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
  
## <a name="see-also"></a><span data-ttu-id="4b2c1-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b2c1-152">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="4b2c1-153">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4b2c1-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4b2c1-154">Associações</span><span class="sxs-lookup"><span data-stu-id="4b2c1-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4b2c1-155">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="4b2c1-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4b2c1-156">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4b2c1-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4b2c1-157">\<binding></span><span class="sxs-lookup"><span data-stu-id="4b2c1-157">\<binding></span></span>](../../../misc/binding.md)
