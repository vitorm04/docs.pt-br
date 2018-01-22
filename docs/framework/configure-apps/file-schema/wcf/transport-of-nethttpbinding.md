---
title: '&lt;transporte&gt; de &lt;netHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 870e08f644f58d49f0165e1f97279adcf2e5445a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a><span data-ttu-id="61429-102">&lt;transporte&gt; de &lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="61429-102">&lt;transport&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="61429-103">Define as propriedades que controlam os parâmetros de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="61429-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="61429-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="61429-104">\<system.serviceModel></span></span>  
<span data-ttu-id="61429-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="61429-105">\<bindings></span></span>  
<span data-ttu-id="61429-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="61429-106">\<netHttpBinding></span></span>  
<span data-ttu-id="61429-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="61429-107">\<binding></span></span>  
<span data-ttu-id="61429-108">\<security></span><span class="sxs-lookup"><span data-stu-id="61429-108">\<security></span></span>  
<span data-ttu-id="61429-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="61429-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61429-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61429-110">Syntax</span></span>  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
        </extendedProtectionPolicy>  
      </transport>  
    </security>  
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61429-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="61429-111">Attributes and Elements</span></span>  
 <span data-ttu-id="61429-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="61429-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61429-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="61429-113">Attributes</span></span>  
  
|<span data-ttu-id="61429-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="61429-114">Attribute</span></span>|<span data-ttu-id="61429-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="61429-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61429-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="61429-116">clientCredentialType</span></span>|<span data-ttu-id="61429-117">-Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a autenticação HTTP.</span><span class="sxs-lookup"><span data-stu-id="61429-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="61429-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="61429-118">The default is `None`.</span></span> <span data-ttu-id="61429-119">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="61429-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="61429-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="61429-120">proxyCredentialType</span></span>|<span data-ttu-id="61429-121">-Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente de dentro de um domínio usando um proxy via HTTP.</span><span class="sxs-lookup"><span data-stu-id="61429-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="61429-122">Esse atributo é aplicável somente quando o `mode` atributo do pai `security` elemento `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="61429-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="61429-123">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="61429-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="61429-124">território</span><span class="sxs-lookup"><span data-stu-id="61429-124">realm</span></span>|<span data-ttu-id="61429-125">Uma cadeia de caracteres que especifica o domínio que é usado pelo esquema de autenticação de HTTP para autenticação básica ou digest.</span><span class="sxs-lookup"><span data-stu-id="61429-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="61429-126">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="61429-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="61429-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="61429-127">policyEnforcement</span></span>|<span data-ttu-id="61429-128">Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> devem ser impostas.</span><span class="sxs-lookup"><span data-stu-id="61429-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="61429-129">1.  Nunca – a política é aplicada nunca (proteção estendida é desabilitada).</span><span class="sxs-lookup"><span data-stu-id="61429-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="61429-130">2.  WhenSupported – a política será aplicada somente se o cliente oferece suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="61429-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="61429-131">3.  Sempre – a política sempre é aplicada.</span><span class="sxs-lookup"><span data-stu-id="61429-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="61429-132">Os clientes que não oferecem suporte a proteção estendida falhará ao autenticar.</span><span class="sxs-lookup"><span data-stu-id="61429-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="61429-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="61429-133">protectionScenario</span></span>|<span data-ttu-id="61429-134">Esta enumeração Especifica o cenário de proteção aplicado pela política.</span><span class="sxs-lookup"><span data-stu-id="61429-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="61429-135">clientCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="61429-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="61429-136">Valor</span><span class="sxs-lookup"><span data-stu-id="61429-136">Value</span></span>|<span data-ttu-id="61429-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="61429-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="61429-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="61429-138">None</span></span>|<span data-ttu-id="61429-139">As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="61429-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="61429-140">Basic</span><span class="sxs-lookup"><span data-stu-id="61429-140">Basic</span></span>|<span data-ttu-id="61429-141">Especifica autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="61429-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="61429-142">Digest</span><span class="sxs-lookup"><span data-stu-id="61429-142">Digest</span></span>|<span data-ttu-id="61429-143">Especifica a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="61429-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="61429-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="61429-144">Ntlm</span></span>|<span data-ttu-id="61429-145">Especifica a autenticação NTLM quando possível, e se a falha de autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="61429-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="61429-146">Windows</span><span class="sxs-lookup"><span data-stu-id="61429-146">Windows</span></span>|<span data-ttu-id="61429-147">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="61429-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="61429-148">proxyCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="61429-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="61429-149">Valor</span><span class="sxs-lookup"><span data-stu-id="61429-149">Value</span></span>|<span data-ttu-id="61429-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="61429-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="61429-151">Nenhum</span><span class="sxs-lookup"><span data-stu-id="61429-151">None</span></span>|<span data-ttu-id="61429-152">-Mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="61429-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="61429-153">Basic</span><span class="sxs-lookup"><span data-stu-id="61429-153">Basic</span></span>|<span data-ttu-id="61429-154">Especifica a autenticação básica, conforme definido por RFC 2617 – autenticação HTTP: Basic e a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="61429-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="61429-155">Digest</span><span class="sxs-lookup"><span data-stu-id="61429-155">Digest</span></span>|<span data-ttu-id="61429-156">Especifica a autenticação digest, conforme definido por RFC 2617 – autenticação HTTP: Basic e a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="61429-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="61429-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="61429-157">Ntlm</span></span>|<span data-ttu-id="61429-158">Especifica a autenticação NTLM quando possível, e se a falha de autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="61429-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="61429-159">Windows</span><span class="sxs-lookup"><span data-stu-id="61429-159">Windows</span></span>|<span data-ttu-id="61429-160">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="61429-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="61429-161">certificado</span><span class="sxs-lookup"><span data-stu-id="61429-161">Certificate</span></span>|<span data-ttu-id="61429-162">Executa a autenticação de cliente usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="61429-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="61429-163">Essa opção só funcionará se o `Mode` atributo do pai `security` elemento é definido como transporte e não funcionará se ele está definido como TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="61429-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61429-164">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="61429-164">Child Elements</span></span>  
 <span data-ttu-id="61429-165">Nenhum</span><span class="sxs-lookup"><span data-stu-id="61429-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61429-166">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="61429-166">Parent Elements</span></span>  
  
|<span data-ttu-id="61429-167">Elemento</span><span class="sxs-lookup"><span data-stu-id="61429-167">Element</span></span>|<span data-ttu-id="61429-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="61429-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61429-169">\<security></span><span class="sxs-lookup"><span data-stu-id="61429-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="61429-170">Define os recursos de segurança para o [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="61429-170">Defines the security capabilities for the [\<netHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61429-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61429-171">Example</span></span>  
 <span data-ttu-id="61429-172">O exemplo a seguir demonstra o uso da segurança de transporte SSL com a associação básica.</span><span class="sxs-lookup"><span data-stu-id="61429-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="61429-173">Por padrão, a associação básica oferece suporte à comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="61429-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61429-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61429-174">See Also</span></span>  
 <span data-ttu-id="61429-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span><span class="sxs-lookup"><span data-stu-id="61429-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="61429-176">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="61429-176">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="61429-177">Associações</span><span class="sxs-lookup"><span data-stu-id="61429-177">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="61429-178">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="61429-178">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="61429-179">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="61429-179">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="61429-180">\<binding></span><span class="sxs-lookup"><span data-stu-id="61429-180">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
