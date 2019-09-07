---
title: <transport> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 521aaf3913a1d30d10a674b71d4d98affcabc296
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399348"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="8f935-102">\<> de transporte \<de NetHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="8f935-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="8f935-103">Define as propriedades que controlam os parâmetros de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="8f935-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="8f935-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8f935-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8f935-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8f935-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8f935-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="8f935-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8f935-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> NetHttpBinding**](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8f935-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="8f935-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="8f935-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8f935-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8f935-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="8f935-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transporte**</span><span class="sxs-lookup"><span data-stu-id="8f935-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f935-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f935-111">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f935-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8f935-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8f935-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8f935-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f935-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f935-114">Attributes</span></span>  
  
|<span data-ttu-id="8f935-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="8f935-115">Attribute</span></span>|<span data-ttu-id="8f935-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f935-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f935-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="8f935-117">clientCredentialType</span></span>|<span data-ttu-id="8f935-118">-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a autenticação HTTP.</span><span class="sxs-lookup"><span data-stu-id="8f935-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="8f935-119">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="8f935-119">The default is `None`.</span></span> <span data-ttu-id="8f935-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8f935-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="8f935-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="8f935-121">proxyCredentialType</span></span>|<span data-ttu-id="8f935-122">-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente de dentro de um domínio usando um proxy sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="8f935-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="8f935-123">Esse atributo é aplicável somente quando o `mode` atributo do elemento pai `security` é `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="8f935-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="8f935-124">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="8f935-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="8f935-125">territórios</span><span class="sxs-lookup"><span data-stu-id="8f935-125">realm</span></span>|<span data-ttu-id="8f935-126">Uma cadeia de caracteres que especifica o realm usado pelo esquema de autenticação HTTP para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="8f935-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="8f935-127">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="8f935-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="8f935-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="8f935-128">policyEnforcement</span></span>|<span data-ttu-id="8f935-129">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="8f935-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="8f935-130">1.  Nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="8f935-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="8f935-131">2.  WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="8f935-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="8f935-132">3.  Sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="8f935-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="8f935-133">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="8f935-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="8f935-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="8f935-134">protectionScenario</span></span>|<span data-ttu-id="8f935-135">Essa enumeração Especifica o cenário de proteção imposto pela política.</span><span class="sxs-lookup"><span data-stu-id="8f935-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="8f935-136">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="8f935-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="8f935-137">Valor</span><span class="sxs-lookup"><span data-stu-id="8f935-137">Value</span></span>|<span data-ttu-id="8f935-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f935-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f935-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8f935-139">None</span></span>|<span data-ttu-id="8f935-140">As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="8f935-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="8f935-141">Basic</span><span class="sxs-lookup"><span data-stu-id="8f935-141">Basic</span></span>|<span data-ttu-id="8f935-142">Especifica autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="8f935-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="8f935-143">Digest</span><span class="sxs-lookup"><span data-stu-id="8f935-143">Digest</span></span>|<span data-ttu-id="8f935-144">Especifica a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="8f935-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="8f935-145">NTLM</span><span class="sxs-lookup"><span data-stu-id="8f935-145">Ntlm</span></span>|<span data-ttu-id="8f935-146">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="8f935-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="8f935-147">Windows</span><span class="sxs-lookup"><span data-stu-id="8f935-147">Windows</span></span>|<span data-ttu-id="8f935-148">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="8f935-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="8f935-149">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="8f935-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="8f935-150">Valor</span><span class="sxs-lookup"><span data-stu-id="8f935-150">Value</span></span>|<span data-ttu-id="8f935-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f935-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8f935-152">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8f935-152">None</span></span>|<span data-ttu-id="8f935-153">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="8f935-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="8f935-154">Basic</span><span class="sxs-lookup"><span data-stu-id="8f935-154">Basic</span></span>|<span data-ttu-id="8f935-155">Especifica a autenticação básica, conforme definido pela RFC 2617 – autenticação HTTP: Autenticação básica e resumida.</span><span class="sxs-lookup"><span data-stu-id="8f935-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="8f935-156">Digest</span><span class="sxs-lookup"><span data-stu-id="8f935-156">Digest</span></span>|<span data-ttu-id="8f935-157">Especifica a autenticação Digest, conforme definido pela RFC 2617 – autenticação HTTP: Autenticação básica e resumida.</span><span class="sxs-lookup"><span data-stu-id="8f935-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="8f935-158">NTLM</span><span class="sxs-lookup"><span data-stu-id="8f935-158">Ntlm</span></span>|<span data-ttu-id="8f935-159">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="8f935-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="8f935-160">Windows</span><span class="sxs-lookup"><span data-stu-id="8f935-160">Windows</span></span>|<span data-ttu-id="8f935-161">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="8f935-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="8f935-162">Certificate</span><span class="sxs-lookup"><span data-stu-id="8f935-162">Certificate</span></span>|<span data-ttu-id="8f935-163">Executa a autenticação de cliente usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="8f935-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="8f935-164">Essa opção só funcionará se `Mode` o atributo do elemento `security` pai estiver definido como transporte e não funcionará se estiver definido como TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="8f935-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f935-165">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8f935-165">Child Elements</span></span>  
 <span data-ttu-id="8f935-166">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8f935-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f935-167">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8f935-167">Parent Elements</span></span>  
  
|<span data-ttu-id="8f935-168">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f935-168">Element</span></span>|<span data-ttu-id="8f935-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f935-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f935-170">\<security></span><span class="sxs-lookup"><span data-stu-id="8f935-170">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="8f935-171">Define os recursos de segurança para o [ \<> NetHttpBinding](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8f935-171">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8f935-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f935-172">Example</span></span>  
 <span data-ttu-id="8f935-173">O exemplo a seguir demonstra o uso de segurança de transporte SSL com a associação básica.</span><span class="sxs-lookup"><span data-stu-id="8f935-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="8f935-174">Por padrão, a associação básica dá suporte à comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="8f935-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="8f935-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f935-175">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="8f935-176">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8f935-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8f935-177">Associações</span><span class="sxs-lookup"><span data-stu-id="8f935-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8f935-178">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="8f935-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8f935-179">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8f935-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8f935-180">\<binding></span><span class="sxs-lookup"><span data-stu-id="8f935-180">\<binding></span></span>](../../../misc/binding.md)
