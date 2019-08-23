---
title: <transport> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: af5852c3c7850f91686d50294c8846f85574e909
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918631"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="11dec-102">\<> de transporte \<de BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="11dec-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="11dec-103">Define as propriedades que controlam os parâmetros de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="11dec-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="11dec-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="11dec-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="11dec-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="11dec-105">\<bindings></span></span>  
<span data-ttu-id="11dec-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="11dec-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="11dec-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="11dec-107">\<binding></span></span>  
<span data-ttu-id="11dec-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="11dec-108">\<security></span></span>  
<span data-ttu-id="11dec-109">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="11dec-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11dec-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11dec-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11dec-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="11dec-111">Attributes and Elements</span></span>  
 <span data-ttu-id="11dec-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="11dec-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11dec-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="11dec-113">Attributes</span></span>  
  
|<span data-ttu-id="11dec-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="11dec-114">Attribute</span></span>|<span data-ttu-id="11dec-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="11dec-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11dec-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="11dec-116">clientCredentialType</span></span>|<span data-ttu-id="11dec-117">-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a autenticação HTTP.</span><span class="sxs-lookup"><span data-stu-id="11dec-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="11dec-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="11dec-118">The default is `None`.</span></span> <span data-ttu-id="11dec-119">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="11dec-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="11dec-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="11dec-120">proxyCredentialType</span></span>|<span data-ttu-id="11dec-121">-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente de dentro de um domínio usando um proxy sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="11dec-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="11dec-122">Esse atributo é aplicável somente quando o `mode` atributo do elemento pai `security` é `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="11dec-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="11dec-123">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="11dec-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="11dec-124">territórios</span><span class="sxs-lookup"><span data-stu-id="11dec-124">realm</span></span>|<span data-ttu-id="11dec-125">Uma cadeia de caracteres que especifica o realm usado pelo esquema de autenticação HTTP para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="11dec-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="11dec-126">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="11dec-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="11dec-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="11dec-127">policyEnforcement</span></span>|<span data-ttu-id="11dec-128">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="11dec-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="11dec-129">1.  Nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="11dec-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="11dec-130">2.  WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="11dec-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="11dec-131">3.  Sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="11dec-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="11dec-132">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="11dec-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="11dec-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="11dec-133">protectionScenario</span></span>|<span data-ttu-id="11dec-134">Essa enumeração Especifica o cenário de proteção imposto pela política.</span><span class="sxs-lookup"><span data-stu-id="11dec-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="11dec-135">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="11dec-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="11dec-136">Valor</span><span class="sxs-lookup"><span data-stu-id="11dec-136">Value</span></span>|<span data-ttu-id="11dec-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="11dec-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11dec-138">Nenhum</span><span class="sxs-lookup"><span data-stu-id="11dec-138">None</span></span>|<span data-ttu-id="11dec-139">As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="11dec-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="11dec-140">Basic</span><span class="sxs-lookup"><span data-stu-id="11dec-140">Basic</span></span>|<span data-ttu-id="11dec-141">Especifica autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="11dec-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="11dec-142">Digest</span><span class="sxs-lookup"><span data-stu-id="11dec-142">Digest</span></span>|<span data-ttu-id="11dec-143">Especifica a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="11dec-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="11dec-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="11dec-144">Ntlm</span></span>|<span data-ttu-id="11dec-145">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="11dec-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="11dec-146">Windows</span><span class="sxs-lookup"><span data-stu-id="11dec-146">Windows</span></span>|<span data-ttu-id="11dec-147">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="11dec-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="11dec-148">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="11dec-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="11dec-149">Valor</span><span class="sxs-lookup"><span data-stu-id="11dec-149">Value</span></span>|<span data-ttu-id="11dec-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="11dec-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11dec-151">Nenhum</span><span class="sxs-lookup"><span data-stu-id="11dec-151">None</span></span>|<span data-ttu-id="11dec-152">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="11dec-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="11dec-153">Basic</span><span class="sxs-lookup"><span data-stu-id="11dec-153">Basic</span></span>|<span data-ttu-id="11dec-154">Especifica a autenticação básica, conforme definido pela RFC 2617 – autenticação HTTP: Autenticação básica e resumida.</span><span class="sxs-lookup"><span data-stu-id="11dec-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="11dec-155">Digest</span><span class="sxs-lookup"><span data-stu-id="11dec-155">Digest</span></span>|<span data-ttu-id="11dec-156">Especifica a autenticação Digest, conforme definido pela RFC 2617 – autenticação HTTP: Autenticação básica e resumida.</span><span class="sxs-lookup"><span data-stu-id="11dec-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="11dec-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="11dec-157">Ntlm</span></span>|<span data-ttu-id="11dec-158">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="11dec-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="11dec-159">Windows</span><span class="sxs-lookup"><span data-stu-id="11dec-159">Windows</span></span>|<span data-ttu-id="11dec-160">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="11dec-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="11dec-161">Certificate</span><span class="sxs-lookup"><span data-stu-id="11dec-161">Certificate</span></span>|<span data-ttu-id="11dec-162">Executa a autenticação de cliente usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="11dec-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="11dec-163">Essa opção só funcionará se `Mode` o atributo do elemento `security` pai estiver definido como transporte e não funcionará se estiver definido como TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="11dec-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11dec-164">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="11dec-164">Child Elements</span></span>  
 <span data-ttu-id="11dec-165">Nenhum</span><span class="sxs-lookup"><span data-stu-id="11dec-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11dec-166">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="11dec-166">Parent Elements</span></span>  
  
|<span data-ttu-id="11dec-167">Elemento</span><span class="sxs-lookup"><span data-stu-id="11dec-167">Element</span></span>|<span data-ttu-id="11dec-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="11dec-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11dec-169">\<security></span><span class="sxs-lookup"><span data-stu-id="11dec-169">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="11dec-170">Define os recursos de segurança para o [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="11dec-170">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="11dec-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11dec-171">Example</span></span>  
 <span data-ttu-id="11dec-172">O exemplo a seguir demonstra o uso de segurança de transporte SSL com a associação básica.</span><span class="sxs-lookup"><span data-stu-id="11dec-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="11dec-173">Por padrão, a associação básica dá suporte à comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="11dec-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11dec-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11dec-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="11dec-175">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="11dec-175">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="11dec-176">Associações</span><span class="sxs-lookup"><span data-stu-id="11dec-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="11dec-177">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="11dec-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="11dec-178">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="11dec-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="11dec-179">\<binding></span><span class="sxs-lookup"><span data-stu-id="11dec-179">\<binding></span></span>](../../../misc/binding.md)
