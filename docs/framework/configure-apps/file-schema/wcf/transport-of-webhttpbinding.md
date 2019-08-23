---
title: <transport> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: f78add5397644dc40bfd22f10bd84aa5c5eb29e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923205"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="662a7-102">\<> de transporte \<de WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="662a7-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="662a7-103">Define as configurações de segurança no nível de transporte para um ponto de extremidade de serviço configurado para receber solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="662a7-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="662a7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="662a7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="662a7-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="662a7-105">\<bindings></span></span>  
<span data-ttu-id="662a7-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="662a7-106">\<webHttpBinding></span></span>  
<span data-ttu-id="662a7-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="662a7-107">\<binding></span></span>  
<span data-ttu-id="662a7-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="662a7-108">\<security></span></span>  
<span data-ttu-id="662a7-109">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="662a7-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="662a7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="662a7-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>
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
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="662a7-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="662a7-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="662a7-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="662a7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="662a7-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="662a7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="662a7-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="662a7-114">Attributes</span></span>  
  
|<span data-ttu-id="662a7-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="662a7-115">Attribute</span></span>|<span data-ttu-id="662a7-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="662a7-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="662a7-117">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="662a7-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="662a7-118">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="662a7-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="662a7-119">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="662a7-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="662a7-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="662a7-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="662a7-121">Uma cadeia de caracteres que especifica o realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="662a7-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="662a7-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="662a7-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="662a7-123">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="662a7-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="662a7-124">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="662a7-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="662a7-125">Um usuário pode consultar o realm de autenticação para determinar que um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="662a7-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="662a7-126">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="662a7-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="662a7-127">1.  Nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="662a7-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="662a7-128">2.  WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="662a7-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="662a7-129">3.  Sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="662a7-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="662a7-130">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="662a7-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="662a7-131">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="662a7-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="662a7-132">Valor</span><span class="sxs-lookup"><span data-stu-id="662a7-132">Value</span></span>|<span data-ttu-id="662a7-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="662a7-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="662a7-134">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="662a7-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="662a7-135">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="662a7-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="662a7-136">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="662a7-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="662a7-137">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="662a7-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="662a7-138">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="662a7-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="662a7-139">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="662a7-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="662a7-140">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="662a7-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="662a7-141">Valor</span><span class="sxs-lookup"><span data-stu-id="662a7-141">Value</span></span>|<span data-ttu-id="662a7-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="662a7-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="662a7-143">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="662a7-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="662a7-144">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="662a7-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="662a7-145">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="662a7-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="662a7-146">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="662a7-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="662a7-147">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="662a7-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="662a7-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="662a7-148">Child Elements</span></span>  
 <span data-ttu-id="662a7-149">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="662a7-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="662a7-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="662a7-150">Parent Elements</span></span>  
  
|<span data-ttu-id="662a7-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="662a7-151">Element</span></span>|<span data-ttu-id="662a7-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="662a7-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="662a7-153">\<security></span><span class="sxs-lookup"><span data-stu-id="662a7-153">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="662a7-154">Representa os recursos de segurança do [ \<elemento WSHttpBinding >](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="662a7-154">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="662a7-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="662a7-155">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="662a7-156">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="662a7-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="662a7-157">Associações</span><span class="sxs-lookup"><span data-stu-id="662a7-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="662a7-158">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="662a7-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="662a7-159">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="662a7-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="662a7-160">\<binding></span><span class="sxs-lookup"><span data-stu-id="662a7-160">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="662a7-161">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="662a7-161">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
