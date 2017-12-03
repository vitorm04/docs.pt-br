---
title: '&lt;transporte&gt; de &lt;webHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d5c0d17f756c4cca84a48cf6849c4d0945cc2b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="b9ae0-102">&lt;transporte&gt; de &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="b9ae0-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="b9ae0-103">Define as configurações de segurança de nível de transporte para um ponto de extremidade de serviço configurada para receber solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="b9ae0-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b9ae0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b9ae0-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="b9ae0-105">\<bindings></span></span>  
<span data-ttu-id="b9ae0-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b9ae0-106">\<webHttpBinding></span></span>  
<span data-ttu-id="b9ae0-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b9ae0-107">\<binding></span></span>  
<span data-ttu-id="b9ae0-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="b9ae0-108">\<security></span></span>  
<span data-ttu-id="b9ae0-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="b9ae0-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ae0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9ae0-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="b9ae0-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="b9ae0-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9ae0-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b9ae0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b9ae0-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9ae0-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b9ae0-114">Attributes</span></span>  
  
|<span data-ttu-id="b9ae0-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="b9ae0-115">Attribute</span></span>|<span data-ttu-id="b9ae0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9ae0-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="b9ae0-117">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="b9ae0-118">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="b9ae0-119">Especifica a credencial usada para autenticar o cliente a um proxy do domínio.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="b9ae0-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="b9ae0-121">Uma cadeia de caracteres que especifica o realm de autenticação para a autenticação básica ou digest.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="b9ae0-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="b9ae0-123">Pelo menos, um realm de autenticação especifica o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="b9ae0-124">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="b9ae0-125">Um usuário pode consultar o realm de autenticação para determinar qual da várias possíveis nomes de usuário e senhas pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="b9ae0-126">Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> devem ser impostas.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b9ae0-127">1.  Nunca – a política é aplicada nunca (proteção estendida é desabilitada).</span><span class="sxs-lookup"><span data-stu-id="b9ae0-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b9ae0-128">2.  WhenSupported – a política será aplicada somente se o cliente oferece suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b9ae0-129">3.  Sempre – a política sempre é aplicada.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b9ae0-130">Os clientes que não oferecem suporte a proteção estendida falhará ao autenticar.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b9ae0-131">clientCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="b9ae0-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b9ae0-132">Valor</span><span class="sxs-lookup"><span data-stu-id="b9ae0-132">Value</span></span>|<span data-ttu-id="b9ae0-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9ae0-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="b9ae0-134">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="b9ae0-135">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="b9ae0-136">Usa certificados x. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="b9ae0-137">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="b9ae0-138">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="b9ae0-139">Usa autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="b9ae0-140">proxyCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="b9ae0-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b9ae0-141">Valor</span><span class="sxs-lookup"><span data-stu-id="b9ae0-141">Value</span></span>|<span data-ttu-id="b9ae0-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9ae0-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="b9ae0-143">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="b9ae0-144">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="b9ae0-145">Usa autenticação digest.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="b9ae0-146">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="b9ae0-147">Usa autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9ae0-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b9ae0-148">Child Elements</span></span>  
 <span data-ttu-id="b9ae0-149">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9ae0-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b9ae0-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b9ae0-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="b9ae0-151">Element</span></span>|<span data-ttu-id="b9ae0-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9ae0-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9ae0-153">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="b9ae0-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="b9ae0-154">Representa os recursos de segurança de [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b9ae0-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9ae0-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9ae0-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="b9ae0-156">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b9ae0-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="b9ae0-157">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="b9ae0-157">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="b9ae0-158">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="b9ae0-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b9ae0-159">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b9ae0-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b9ae0-160">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b9ae0-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="b9ae0-161">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="b9ae0-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
