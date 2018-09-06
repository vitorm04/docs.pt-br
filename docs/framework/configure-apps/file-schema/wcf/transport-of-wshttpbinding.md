---
title: '&lt;transporte&gt; de &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 771866a83d54ca9e4fc7f3ed6d351b4a6c755b4c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890948"
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="d5e8f-102">&lt;transporte&gt; de &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d5e8f-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="d5e8f-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="d5e8f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d5e8f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d5e8f-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="d5e8f-105">\<bindings></span></span>  
<span data-ttu-id="d5e8f-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d5e8f-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="d5e8f-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d5e8f-107">\<binding></span></span>  
<span data-ttu-id="d5e8f-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="d5e8f-108">\<security></span></span>  
<span data-ttu-id="d5e8f-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="d5e8f-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e8f-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5e8f-110">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="d5e8f-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="d5e8f-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5e8f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d5e8f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d5e8f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5e8f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="d5e8f-114">Attributes</span></span>  
  
|<span data-ttu-id="d5e8f-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="d5e8f-115">Attribute</span></span>|<span data-ttu-id="d5e8f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5e8f-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="d5e8f-117">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="d5e8f-118">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="d5e8f-119">Especifica a credencial usada para autenticar o cliente para um proxy do domínio.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="d5e8f-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="d5e8f-121">Uma cadeia de caracteres que especifica o realm de autenticação para a autenticação básica ou digest.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="d5e8f-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="d5e8f-123">Pelo menos, um realm de autenticação especifica o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="d5e8f-124">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="d5e8f-125">Um usuário pode consultar o realm de autenticação para determinar quais dos vários possíveis nomes de usuário e senhas pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="d5e8f-126">Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposta.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="d5e8f-127">1.  Nunca – a política de nunca é aplicada (proteção estendida é desabilitada).</span><span class="sxs-lookup"><span data-stu-id="d5e8f-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="d5e8f-128">2.  WhenSupported – a política é aplicada somente se o cliente oferece suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="d5e8f-129">3.  Sempre – a política sempre é aplicada.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="d5e8f-130">Os clientes que não dão suporte a proteção estendida falharão ao autenticar.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="d5e8f-131">clientCredentialType de atributo</span><span class="sxs-lookup"><span data-stu-id="d5e8f-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d5e8f-132">Valor</span><span class="sxs-lookup"><span data-stu-id="d5e8f-132">Value</span></span>|<span data-ttu-id="d5e8f-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5e8f-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="d5e8f-134">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="d5e8f-135">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="d5e8f-136">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="d5e8f-137">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="d5e8f-138">Usa integrada a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="d5e8f-139">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="d5e8f-140">proxyCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="d5e8f-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d5e8f-141">Valor</span><span class="sxs-lookup"><span data-stu-id="d5e8f-141">Value</span></span>|<span data-ttu-id="d5e8f-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5e8f-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="d5e8f-143">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="d5e8f-144">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="d5e8f-145">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="d5e8f-146">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="d5e8f-147">Usa integrada a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="d5e8f-148">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5e8f-149">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d5e8f-149">Child Elements</span></span>  
 <span data-ttu-id="d5e8f-150">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d5e8f-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5e8f-151">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d5e8f-151">Parent Elements</span></span>  
  
|<span data-ttu-id="d5e8f-152">Elemento</span><span class="sxs-lookup"><span data-stu-id="d5e8f-152">Element</span></span>|<span data-ttu-id="d5e8f-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5e8f-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5e8f-154">\<security></span><span class="sxs-lookup"><span data-stu-id="d5e8f-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="d5e8f-155">Representa os recursos de segurança de [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d5e8f-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5e8f-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5e8f-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="d5e8f-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d5e8f-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d5e8f-158">Associações</span><span class="sxs-lookup"><span data-stu-id="d5e8f-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d5e8f-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="d5e8f-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d5e8f-160">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d5e8f-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d5e8f-161">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d5e8f-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
