---
title: <transport> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: d575b7e282775e2e2c498ac94bb54a563b8d125e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201389"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="84880-102">\<transport> de \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="84880-102">\<transport> of \<basicHttpBinding></span></span>

<span data-ttu-id="84880-103">Define as propriedades que controlam os parâmetros de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="84880-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="84880-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84880-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84880-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84880-105">Attributes and Elements</span></span>  

 <span data-ttu-id="84880-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="84880-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84880-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="84880-107">Attributes</span></span>  
  
|<span data-ttu-id="84880-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="84880-108">Attribute</span></span>|<span data-ttu-id="84880-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="84880-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84880-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="84880-110">clientCredentialType</span></span>|<span data-ttu-id="84880-111">-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a autenticação HTTP.</span><span class="sxs-lookup"><span data-stu-id="84880-111">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="84880-112">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="84880-112">The default is `None`.</span></span> <span data-ttu-id="84880-113">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="84880-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="84880-114">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="84880-114">proxyCredentialType</span></span>|<span data-ttu-id="84880-115">-Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente de dentro de um domínio usando um proxy sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="84880-115">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="84880-116">Esse atributo é aplicável somente quando o `mode` atributo do elemento pai `security` é `Transport` ou `TransportCredentialsOnly` .</span><span class="sxs-lookup"><span data-stu-id="84880-116">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="84880-117">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="84880-117">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="84880-118">territórios</span><span class="sxs-lookup"><span data-stu-id="84880-118">realm</span></span>|<span data-ttu-id="84880-119">Uma cadeia de caracteres que especifica o realm usado pelo esquema de autenticação HTTP para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="84880-119">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="84880-120">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="84880-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="84880-121">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="84880-121">policyEnforcement</span></span>|<span data-ttu-id="84880-122">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="84880-122">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="84880-123">1. nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="84880-123">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="84880-124">2. WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="84880-124">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="84880-125">3. sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="84880-125">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="84880-126">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="84880-126">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="84880-127">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="84880-127">protectionScenario</span></span>|<span data-ttu-id="84880-128">Essa enumeração Especifica o cenário de proteção imposto pela política.</span><span class="sxs-lookup"><span data-stu-id="84880-128">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="84880-129">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="84880-129">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="84880-130">Valor</span><span class="sxs-lookup"><span data-stu-id="84880-130">Value</span></span>|<span data-ttu-id="84880-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="84880-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84880-132">Nenhum</span><span class="sxs-lookup"><span data-stu-id="84880-132">None</span></span>|<span data-ttu-id="84880-133">As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="84880-133">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="84880-134">Basic</span><span class="sxs-lookup"><span data-stu-id="84880-134">Basic</span></span>|<span data-ttu-id="84880-135">Especifica autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="84880-135">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="84880-136">Digest</span><span class="sxs-lookup"><span data-stu-id="84880-136">Digest</span></span>|<span data-ttu-id="84880-137">Especifica a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="84880-137">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="84880-138">Ntlm</span><span class="sxs-lookup"><span data-stu-id="84880-138">Ntlm</span></span>|<span data-ttu-id="84880-139">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="84880-139">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="84880-140">Windows</span><span class="sxs-lookup"><span data-stu-id="84880-140">Windows</span></span>|<span data-ttu-id="84880-141">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="84880-141">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="84880-142">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="84880-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="84880-143">Valor</span><span class="sxs-lookup"><span data-stu-id="84880-143">Value</span></span>|<span data-ttu-id="84880-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="84880-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84880-145">Nenhum</span><span class="sxs-lookup"><span data-stu-id="84880-145">None</span></span>|<span data-ttu-id="84880-146">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="84880-146">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="84880-147">Basic</span><span class="sxs-lookup"><span data-stu-id="84880-147">Basic</span></span>|<span data-ttu-id="84880-148">Especifica a autenticação básica, conforme definido pela RFC 2617 – autenticação HTTP: autenticação básica e resumida.</span><span class="sxs-lookup"><span data-stu-id="84880-148">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="84880-149">Digest</span><span class="sxs-lookup"><span data-stu-id="84880-149">Digest</span></span>|<span data-ttu-id="84880-150">Especifica a autenticação Digest, conforme definido pela RFC 2617 – autenticação HTTP: autenticação básica e resumida.</span><span class="sxs-lookup"><span data-stu-id="84880-150">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="84880-151">Ntlm</span><span class="sxs-lookup"><span data-stu-id="84880-151">Ntlm</span></span>|<span data-ttu-id="84880-152">Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.</span><span class="sxs-lookup"><span data-stu-id="84880-152">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="84880-153">Windows</span><span class="sxs-lookup"><span data-stu-id="84880-153">Windows</span></span>|<span data-ttu-id="84880-154">Especifica a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="84880-154">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="84880-155">Certificado</span><span class="sxs-lookup"><span data-stu-id="84880-155">Certificate</span></span>|<span data-ttu-id="84880-156">Executa a autenticação de cliente usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="84880-156">Performs client authentication using a certificate.</span></span> <span data-ttu-id="84880-157">Essa opção só funcionará se o `Mode` atributo do `security` elemento pai estiver definido como transporte e não funcionará se estiver definido como TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="84880-157">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84880-158">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="84880-158">Child Elements</span></span>  

 <span data-ttu-id="84880-159">Nenhum</span><span class="sxs-lookup"><span data-stu-id="84880-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84880-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="84880-160">Parent Elements</span></span>  
  
|<span data-ttu-id="84880-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="84880-161">Element</span></span>|<span data-ttu-id="84880-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="84880-162">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="84880-163">Define os recursos de segurança para o [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="84880-163">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="84880-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84880-164">Example</span></span>  

 <span data-ttu-id="84880-165">O exemplo a seguir demonstra o uso de segurança de transporte SSL com a associação básica.</span><span class="sxs-lookup"><span data-stu-id="84880-165">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="84880-166">Por padrão, a associação básica dá suporte à comunicação HTTP.</span><span class="sxs-lookup"><span data-stu-id="84880-166">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84880-167">Veja também</span><span class="sxs-lookup"><span data-stu-id="84880-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="84880-168">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="84880-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="84880-169">Associações</span><span class="sxs-lookup"><span data-stu-id="84880-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="84880-170">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="84880-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="84880-171">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="84880-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
