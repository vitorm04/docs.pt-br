---
title: <transport> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: c563339e4f854cc4e60f92dd5b8c0b39112dc000
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736113"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="89be8-102">> de transporte de \<de \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="89be8-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="89be8-103">Define as propriedades que controlam os parâmetros de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="89be8-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="89be8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="89be8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="89be8-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="89be8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="89be8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="89be8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="89be8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**BasicHttpBinding**](basichttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="89be8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="89be8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="89be8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="89be8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<security >** ](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="89be8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="89be8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**transporte >**</span><span class="sxs-lookup"><span data-stu-id="89be8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89be8-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89be8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89be8-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="89be8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="89be8-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="89be8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89be8-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="89be8-114">Attributes</span></span>  
  
|<span data-ttu-id="89be8-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="89be8-115">Attribute</span></span>|<span data-ttu-id="89be8-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="89be8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89be8-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="89be8-117">clientCredentialType</span></span>|<span data-ttu-id="89be8-118">-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a autenticação HTTP.</span><span class="sxs-lookup"><span data-stu-id="89be8-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="89be8-119">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="89be8-119">The default is `None`.</span></span> <span data-ttu-id="89be8-120">Este atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="89be8-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="89be8-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="89be8-121">proxyCredentialType</span></span>|<span data-ttu-id="89be8-122">-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente de dentro de um domínio usando um proxy sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="89be8-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="89be8-123">Esse atributo é aplicável somente quando o atributo `mode` do elemento `security` pai é `Transport` ou `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="89be8-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="89be8-124">Este atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="89be8-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="89be8-125">territórios</span><span class="sxs-lookup"><span data-stu-id="89be8-125">realm</span></span>|<span data-ttu-id="89be8-126">Uma cadeia de caracteres que especifica o realm usado pelo esquema de autenticação HTTP para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="89be8-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="89be8-127">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="89be8-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="89be8-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="89be8-128">policyEnforcement</span></span>|<span data-ttu-id="89be8-129">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="89be8-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="89be8-130">1. nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="89be8-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="89be8-131">2. WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="89be8-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="89be8-132">3. sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="89be8-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="89be8-133">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="89be8-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="89be8-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="89be8-134">protectionScenario</span></span>|<span data-ttu-id="89be8-135">Essa enumeração Especifica o cenário de proteção imposto pela política.</span><span class="sxs-lookup"><span data-stu-id="89be8-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="89be8-136">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="89be8-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="89be8-137">Valor</span><span class="sxs-lookup"><span data-stu-id="89be8-137">Value</span></span>|<span data-ttu-id="89be8-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="89be8-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89be8-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="89be8-139">None</span></span>|<span data-ttu-id="89be8-140">As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="89be8-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="89be8-141">Basic</span><span class="sxs-lookup"><span data-stu-id="89be8-141">Basic</span></span>|<span data-ttu-id="89be8-142">Especifica autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="89be8-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="89be8-143">Digest</span><span class="sxs-lookup"><span data-stu-id="89be8-143">Digest</span></span>|<span data-ttu-id="89be8-144">Especifica a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="89be8-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="89be8-145">NTLM</span><span class="sxs-lookup"><span data-stu-id="89be8-145">Ntlm</span></span>|<span data-ttu-id="89be8-146">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="89be8-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="89be8-147">Windows</span><span class="sxs-lookup"><span data-stu-id="89be8-147">Windows</span></span>|<span data-ttu-id="89be8-148">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="89be8-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="89be8-149">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="89be8-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="89be8-150">Valor</span><span class="sxs-lookup"><span data-stu-id="89be8-150">Value</span></span>|<span data-ttu-id="89be8-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="89be8-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89be8-152">Nenhum</span><span class="sxs-lookup"><span data-stu-id="89be8-152">None</span></span>|<span data-ttu-id="89be8-153">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="89be8-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="89be8-154">Basic</span><span class="sxs-lookup"><span data-stu-id="89be8-154">Basic</span></span>|<span data-ttu-id="89be8-155">Especifica a autenticação básica, conforme definido pela RFC 2617 – autenticação HTTP: autenticação básica e resumida.</span><span class="sxs-lookup"><span data-stu-id="89be8-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="89be8-156">Digest</span><span class="sxs-lookup"><span data-stu-id="89be8-156">Digest</span></span>|<span data-ttu-id="89be8-157">Especifica a autenticação Digest, conforme definido pela RFC 2617 – autenticação HTTP: autenticação básica e resumida.</span><span class="sxs-lookup"><span data-stu-id="89be8-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="89be8-158">NTLM</span><span class="sxs-lookup"><span data-stu-id="89be8-158">Ntlm</span></span>|<span data-ttu-id="89be8-159">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="89be8-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="89be8-160">Windows</span><span class="sxs-lookup"><span data-stu-id="89be8-160">Windows</span></span>|<span data-ttu-id="89be8-161">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="89be8-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="89be8-162">Certificate</span><span class="sxs-lookup"><span data-stu-id="89be8-162">Certificate</span></span>|<span data-ttu-id="89be8-163">Executa a autenticação de cliente usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="89be8-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="89be8-164">Essa opção só funcionará se o atributo `Mode` do elemento pai `security` for definido como transporte e não funcionará se estiver definido como TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="89be8-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89be8-165">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="89be8-165">Child Elements</span></span>  
 <span data-ttu-id="89be8-166">Nenhum</span><span class="sxs-lookup"><span data-stu-id="89be8-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89be8-167">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="89be8-167">Parent Elements</span></span>  
  
|<span data-ttu-id="89be8-168">Elemento</span><span class="sxs-lookup"><span data-stu-id="89be8-168">Element</span></span>|<span data-ttu-id="89be8-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="89be8-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89be8-170">\<Security ></span><span class="sxs-lookup"><span data-stu-id="89be8-170">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="89be8-171">Define os recursos de segurança para o [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="89be8-171">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89be8-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89be8-172">Example</span></span>  
 <span data-ttu-id="89be8-173">O exemplo a seguir demonstra o uso de segurança de transporte SSL com a associação básica.</span><span class="sxs-lookup"><span data-stu-id="89be8-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="89be8-174">Por padrão, a associação básica dá suporte à comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="89be8-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89be8-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89be8-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="89be8-176">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="89be8-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="89be8-177">Associações</span><span class="sxs-lookup"><span data-stu-id="89be8-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="89be8-178">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="89be8-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="89be8-179">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="89be8-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="89be8-180">\<binding ></span><span class="sxs-lookup"><span data-stu-id="89be8-180">\<binding></span></span>](bindings.md)
