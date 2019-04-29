---
title: <transport> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 5d1ef059f8fde7c41e333571d1c025a9c0c7e03f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788382"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="09f78-102">\<transporte > de \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="09f78-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="09f78-103">Define as propriedades que controlam os parâmetros de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="09f78-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="09f78-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="09f78-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="09f78-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="09f78-105">\<bindings></span></span>  
<span data-ttu-id="09f78-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="09f78-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="09f78-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="09f78-107">\<binding></span></span>  
<span data-ttu-id="09f78-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="09f78-108">\<security></span></span>  
<span data-ttu-id="09f78-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="09f78-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f78-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09f78-110">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09f78-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="09f78-111">Attributes and Elements</span></span>  
 <span data-ttu-id="09f78-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="09f78-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09f78-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="09f78-113">Attributes</span></span>  
  
|<span data-ttu-id="09f78-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="09f78-114">Attribute</span></span>|<span data-ttu-id="09f78-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="09f78-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09f78-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="09f78-116">clientCredentialType</span></span>|<span data-ttu-id="09f78-117">-Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a autenticação HTTP.</span><span class="sxs-lookup"><span data-stu-id="09f78-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="09f78-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="09f78-118">The default is `None`.</span></span> <span data-ttu-id="09f78-119">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="09f78-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="09f78-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="09f78-120">proxyCredentialType</span></span>|<span data-ttu-id="09f78-121">-Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente de dentro de um domínio usando um proxy por meio de HTTP.</span><span class="sxs-lookup"><span data-stu-id="09f78-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="09f78-122">Esse atributo é aplicável somente quando o `mode` atributo do pai `security` elemento é `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="09f78-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="09f78-123">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="09f78-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="09f78-124">território</span><span class="sxs-lookup"><span data-stu-id="09f78-124">realm</span></span>|<span data-ttu-id="09f78-125">Uma cadeia de caracteres que especifica o realm que é usado pelo esquema de autenticação de HTTP para a autenticação básica ou digest.</span><span class="sxs-lookup"><span data-stu-id="09f78-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="09f78-126">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="09f78-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="09f78-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="09f78-127">policyEnforcement</span></span>|<span data-ttu-id="09f78-128">Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposta.</span><span class="sxs-lookup"><span data-stu-id="09f78-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="09f78-129">1.  Nunca – a política de nunca é aplicada (proteção estendida é desabilitada).</span><span class="sxs-lookup"><span data-stu-id="09f78-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="09f78-130">2.  WhenSupported – a política é aplicada somente se o cliente oferece suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="09f78-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="09f78-131">3.  Sempre – a política sempre é aplicada.</span><span class="sxs-lookup"><span data-stu-id="09f78-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="09f78-132">Os clientes que não dão suporte a proteção estendida falharão ao autenticar.</span><span class="sxs-lookup"><span data-stu-id="09f78-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="09f78-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="09f78-133">protectionScenario</span></span>|<span data-ttu-id="09f78-134">Esta enumeração Especifica o cenário de proteção imposto pela política.</span><span class="sxs-lookup"><span data-stu-id="09f78-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="09f78-135">clientCredentialType de atributo</span><span class="sxs-lookup"><span data-stu-id="09f78-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="09f78-136">Valor</span><span class="sxs-lookup"><span data-stu-id="09f78-136">Value</span></span>|<span data-ttu-id="09f78-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="09f78-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="09f78-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09f78-138">None</span></span>|<span data-ttu-id="09f78-139">Mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="09f78-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="09f78-140">Basic</span><span class="sxs-lookup"><span data-stu-id="09f78-140">Basic</span></span>|<span data-ttu-id="09f78-141">Especifica autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="09f78-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="09f78-142">Digest</span><span class="sxs-lookup"><span data-stu-id="09f78-142">Digest</span></span>|<span data-ttu-id="09f78-143">Especifica a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="09f78-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="09f78-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="09f78-144">Ntlm</span></span>|<span data-ttu-id="09f78-145">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="09f78-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="09f78-146">Windows</span><span class="sxs-lookup"><span data-stu-id="09f78-146">Windows</span></span>|<span data-ttu-id="09f78-147">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="09f78-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="09f78-148">proxyCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="09f78-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="09f78-149">Valor</span><span class="sxs-lookup"><span data-stu-id="09f78-149">Value</span></span>|<span data-ttu-id="09f78-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="09f78-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="09f78-151">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09f78-151">None</span></span>|<span data-ttu-id="09f78-152">-Mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="09f78-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="09f78-153">Basic</span><span class="sxs-lookup"><span data-stu-id="09f78-153">Basic</span></span>|<span data-ttu-id="09f78-154">Especifica autenticação básica, conforme definido pelo RFC 2617 – autenticação HTTP: Básica e autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="09f78-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="09f78-155">Digest</span><span class="sxs-lookup"><span data-stu-id="09f78-155">Digest</span></span>|<span data-ttu-id="09f78-156">Especifica a autenticação digest, conforme definido pelo RFC 2617 – autenticação HTTP: Básica e autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="09f78-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="09f78-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="09f78-157">Ntlm</span></span>|<span data-ttu-id="09f78-158">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="09f78-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="09f78-159">Windows</span><span class="sxs-lookup"><span data-stu-id="09f78-159">Windows</span></span>|<span data-ttu-id="09f78-160">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="09f78-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="09f78-161">Certificado</span><span class="sxs-lookup"><span data-stu-id="09f78-161">Certificate</span></span>|<span data-ttu-id="09f78-162">Executa a autenticação de cliente usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="09f78-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="09f78-163">Essa opção só funcionará se o `Mode` atributo do pai `security` elemento é definido como transporte e não funcionará se ele for definido como TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="09f78-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09f78-164">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="09f78-164">Child Elements</span></span>  
 <span data-ttu-id="09f78-165">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09f78-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09f78-166">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="09f78-166">Parent Elements</span></span>  
  
|<span data-ttu-id="09f78-167">Elemento</span><span class="sxs-lookup"><span data-stu-id="09f78-167">Element</span></span>|<span data-ttu-id="09f78-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="09f78-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09f78-169">\<security></span><span class="sxs-lookup"><span data-stu-id="09f78-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="09f78-170">Define os recursos de segurança para o [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="09f78-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09f78-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09f78-171">Example</span></span>  
 <span data-ttu-id="09f78-172">O exemplo a seguir demonstra o uso da segurança de transporte SSL com a associação básica.</span><span class="sxs-lookup"><span data-stu-id="09f78-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="09f78-173">Por padrão, a associação básica oferece suporte à comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="09f78-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="09f78-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09f78-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="09f78-175">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="09f78-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="09f78-176">Associações</span><span class="sxs-lookup"><span data-stu-id="09f78-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="09f78-177">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="09f78-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="09f78-178">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="09f78-178">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="09f78-179">\<binding></span><span class="sxs-lookup"><span data-stu-id="09f78-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
