---
title: <transport> De <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1c25ffd70ae83f14d5e596b1ee32d05abcc95184
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267671"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="1262e-102">\<transporte > de \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="1262e-102">\<transport> of \<wsHttpBinding></span></span>
<span data-ttu-id="1262e-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="1262e-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="1262e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1262e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1262e-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="1262e-105">\<bindings></span></span>  
<span data-ttu-id="1262e-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1262e-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="1262e-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="1262e-107">\<binding></span></span>  
<span data-ttu-id="1262e-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="1262e-108">\<security></span></span>  
<span data-ttu-id="1262e-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="1262e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1262e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1262e-110">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtecutionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="1262e-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="1262e-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1262e-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1262e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1262e-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1262e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1262e-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="1262e-114">Attributes</span></span>  
  
|<span data-ttu-id="1262e-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="1262e-115">Attribute</span></span>|<span data-ttu-id="1262e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="1262e-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="1262e-117">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1262e-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="1262e-118">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="1262e-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="1262e-119">Especifica a credencial usada para autenticar o cliente para um proxy do domínio.</span><span class="sxs-lookup"><span data-stu-id="1262e-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="1262e-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="1262e-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="1262e-121">Uma cadeia de caracteres que especifica o realm de autenticação para a autenticação básica ou digest.</span><span class="sxs-lookup"><span data-stu-id="1262e-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="1262e-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="1262e-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="1262e-123">Pelo menos, um realm de autenticação especifica o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="1262e-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="1262e-124">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="1262e-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="1262e-125">Um usuário pode consultar o realm de autenticação para determinar quais dos vários possíveis nomes de usuário e senhas pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="1262e-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="1262e-126">Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposta.</span><span class="sxs-lookup"><span data-stu-id="1262e-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="1262e-127">1.  Nunca – a política de nunca é aplicada (proteção estendida é desabilitada).</span><span class="sxs-lookup"><span data-stu-id="1262e-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="1262e-128">2.  WhenSupported – a política é aplicada somente se o cliente oferece suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="1262e-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="1262e-129">3.  Sempre – a política sempre é aplicada.</span><span class="sxs-lookup"><span data-stu-id="1262e-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="1262e-130">Os clientes que não dão suporte a proteção estendida falharão ao autenticar.</span><span class="sxs-lookup"><span data-stu-id="1262e-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="1262e-131">clientCredentialType de atributo</span><span class="sxs-lookup"><span data-stu-id="1262e-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1262e-132">Valor</span><span class="sxs-lookup"><span data-stu-id="1262e-132">Value</span></span>|<span data-ttu-id="1262e-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="1262e-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="1262e-134">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="1262e-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="1262e-135">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="1262e-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="1262e-136">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="1262e-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="1262e-137">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="1262e-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="1262e-138">Usa integrada a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="1262e-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="1262e-139">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="1262e-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="1262e-140">proxyCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="1262e-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1262e-141">Valor</span><span class="sxs-lookup"><span data-stu-id="1262e-141">Value</span></span>|<span data-ttu-id="1262e-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="1262e-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="1262e-143">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="1262e-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="1262e-144">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="1262e-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="1262e-145">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="1262e-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="1262e-146">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="1262e-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="1262e-147">Usa integrada a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="1262e-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="1262e-148">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="1262e-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1262e-149">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1262e-149">Child Elements</span></span>  
 <span data-ttu-id="1262e-150">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1262e-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1262e-151">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1262e-151">Parent Elements</span></span>  
  
|<span data-ttu-id="1262e-152">Elemento</span><span class="sxs-lookup"><span data-stu-id="1262e-152">Element</span></span>|<span data-ttu-id="1262e-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="1262e-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1262e-154">\<security></span><span class="sxs-lookup"><span data-stu-id="1262e-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="1262e-155">Representa os recursos de segurança de [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1262e-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1262e-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1262e-156">See also</span></span>
- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="1262e-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1262e-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1262e-158">Associações</span><span class="sxs-lookup"><span data-stu-id="1262e-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1262e-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="1262e-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1262e-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1262e-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1262e-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="1262e-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
