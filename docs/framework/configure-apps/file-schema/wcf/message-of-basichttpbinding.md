---
title: '&lt;mensagem&gt; de &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 8c3519e2db12e34d9f2bd03689e0e9684c5792ae
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151274"
---
# <a name="ltmessagegt-of-ltbasichttpbindinggt"></a><span data-ttu-id="b7e9e-102">&lt;mensagem&gt; de &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="b7e9e-102">&lt;message&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="b7e9e-103">Define as configurações de segurança em nível de mensagem do [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="b7e9e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7e9e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7e9e-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="b7e9e-105">\<bindings></span></span>  
<span data-ttu-id="b7e9e-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b7e9e-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="b7e9e-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b7e9e-107">\<binding></span></span>  
<span data-ttu-id="b7e9e-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="b7e9e-108">\<security></span></span>  
<span data-ttu-id="b7e9e-109">\<message></span><span class="sxs-lookup"><span data-stu-id="b7e9e-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e9e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7e9e-110">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7e9e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7e9e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b7e9e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7e9e-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7e9e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7e9e-113">Attributes</span></span>  
  
|<span data-ttu-id="b7e9e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7e9e-114">Attribute</span></span>|<span data-ttu-id="b7e9e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e9e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7e9e-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="b7e9e-116">algorithmSuite</span></span>|<span data-ttu-id="b7e9e-117">Define a mensagem de algoritmos de criptografia e encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="b7e9e-118">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, que especifica os algoritmos e os tamanhos de chave.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="b7e9e-119">Esses algoritmos são mapeados para aqueles especificados na especificação da linguagem de política de segurança (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="b7e9e-120">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="b7e9e-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b7e9e-121">clientCredentialType</span></span>|<span data-ttu-id="b7e9e-122">Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a segurança baseada em mensagem.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="b7e9e-123">O padrão é `UserName`.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b7e9e-124">clientCredentialType de atributo</span><span class="sxs-lookup"><span data-stu-id="b7e9e-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b7e9e-125">Valor</span><span class="sxs-lookup"><span data-stu-id="b7e9e-125">Value</span></span>|<span data-ttu-id="b7e9e-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e9e-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b7e9e-127">UserName</span><span class="sxs-lookup"><span data-stu-id="b7e9e-127">UserName</span></span>|<span data-ttu-id="b7e9e-128">-Requer que o cliente seja autenticado para o servidor com uma credencial de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="b7e9e-129">Essa credencial precisa ser especificado usando o [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-129">This credential needs to be specified using the [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span></span><br /><span data-ttu-id="b7e9e-130">-WCF não oferece suporte para enviar um resumo de senha ou derivação de chaves usando senhas e essas chaves para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="b7e9e-131">Portanto, o WCF impõe que o transporte ser protegidos ao usar as credenciais de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="b7e9e-132">Para o `basicHttpBinding`, isso requer configuração de um canal SSL.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="b7e9e-133">Certificado</span><span class="sxs-lookup"><span data-stu-id="b7e9e-133">Certificate</span></span>|<span data-ttu-id="b7e9e-134">Requer que o cliente seja autenticado para o servidor usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="b7e9e-135">A credencial do cliente nesse caso, deve ser especificado usando [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) e o [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-135">The client credential in this case needs to be specified using [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) and the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="b7e9e-136">Além disso, ao usar o modo de segurança de mensagem, o cliente precisa ser provisionado com o certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="b7e9e-137">A credencial de serviço neste caso deve ser especificado usando <xref:System.ServiceModel.Description.ClientCredentials> classe ou `ClientCredentials` elemento de comportamento e especificando o serviço de certificado usando o [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7e9e-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7e9e-138">Child Elements</span></span>  
 <span data-ttu-id="b7e9e-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b7e9e-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7e9e-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7e9e-140">Parent Elements</span></span>  
  
|<span data-ttu-id="b7e9e-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7e9e-141">Element</span></span>|<span data-ttu-id="b7e9e-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e9e-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7e9e-143">\<security></span><span class="sxs-lookup"><span data-stu-id="b7e9e-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="b7e9e-144">Define os recursos de segurança para o [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b7e9e-144">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7e9e-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7e9e-145">Example</span></span>  
 <span data-ttu-id="b7e9e-146">Este exemplo demonstra como implementar um aplicativo que usa a segurança basicHttpBinding e a mensagem.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="b7e9e-147">No seguinte exemplo de configuração para um serviço, a definição de ponto de extremidade Especifica o basicHttpBinding e faz referência a uma configuração de ligação nomeada `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="b7e9e-148">O certificado que o serviço usa para se autenticar para o cliente é definido `behaviors` seção do arquivo de configuração sob o `serviceCredentials` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="b7e9e-149">O modo de validação que se aplica ao certificado que o cliente usa para autenticar-se com o serviço também é definido `behaviors` seção sob o `clientCertificate` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="b7e9e-150">Os mesmos detalhes de associação e segurança são especificados no arquivo de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="b7e9e-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7e9e-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7e9e-151">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpMessageSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>  
 [<span data-ttu-id="b7e9e-152">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b7e9e-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b7e9e-153">Associações</span><span class="sxs-lookup"><span data-stu-id="b7e9e-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b7e9e-154">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="b7e9e-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b7e9e-155">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b7e9e-155">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="b7e9e-156">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b7e9e-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
