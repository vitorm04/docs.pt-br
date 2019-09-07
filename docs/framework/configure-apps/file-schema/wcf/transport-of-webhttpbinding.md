---
title: <transport> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 98cdaa86441f91552c7133d8e5694f88019a6dbf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399274"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="4feca-102">\<> de transporte \<de WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="4feca-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="4feca-103">Define as configurações de segurança no nível de transporte para um ponto de extremidade de serviço configurado para receber solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="4feca-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
<span data-ttu-id="4feca-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4feca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4feca-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4feca-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4feca-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4feca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4feca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> WebHttpBinding**](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4feca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="4feca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="4feca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4feca-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4feca-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)</span></span>\
<span data-ttu-id="4feca-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transporte**</span><span class="sxs-lookup"><span data-stu-id="4feca-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4feca-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4feca-111">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="4feca-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="4feca-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4feca-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4feca-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4feca-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4feca-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4feca-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="4feca-115">Attributes</span></span>  
  
|<span data-ttu-id="4feca-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="4feca-116">Attribute</span></span>|<span data-ttu-id="4feca-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="4feca-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="4feca-118">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="4feca-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="4feca-119">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4feca-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="4feca-120">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="4feca-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="4feca-121">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4feca-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="4feca-122">Uma cadeia de caracteres que especifica o realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="4feca-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="4feca-123">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="4feca-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="4feca-124">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="4feca-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="4feca-125">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="4feca-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="4feca-126">Um usuário pode consultar o realm de autenticação para determinar que um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="4feca-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="4feca-127">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="4feca-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="4feca-128">1.  Nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="4feca-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="4feca-129">2.  WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="4feca-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="4feca-130">3.  Sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="4feca-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="4feca-131">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="4feca-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="4feca-132">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="4feca-132">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4feca-133">Valor</span><span class="sxs-lookup"><span data-stu-id="4feca-133">Value</span></span>|<span data-ttu-id="4feca-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="4feca-134">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="4feca-135">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="4feca-135">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="4feca-136">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="4feca-136">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="4feca-137">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="4feca-137">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="4feca-138">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="4feca-138">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="4feca-139">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="4feca-139">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="4feca-140">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="4feca-140">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="4feca-141">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="4feca-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4feca-142">Valor</span><span class="sxs-lookup"><span data-stu-id="4feca-142">Value</span></span>|<span data-ttu-id="4feca-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="4feca-143">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="4feca-144">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="4feca-144">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="4feca-145">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="4feca-145">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="4feca-146">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="4feca-146">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="4feca-147">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="4feca-147">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="4feca-148">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="4feca-148">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4feca-149">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4feca-149">Child Elements</span></span>  
 <span data-ttu-id="4feca-150">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4feca-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4feca-151">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4feca-151">Parent Elements</span></span>  
  
|<span data-ttu-id="4feca-152">Elemento</span><span class="sxs-lookup"><span data-stu-id="4feca-152">Element</span></span>|<span data-ttu-id="4feca-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="4feca-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4feca-154">\<security></span><span class="sxs-lookup"><span data-stu-id="4feca-154">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="4feca-155">Representa os recursos de segurança do [ \<elemento WSHttpBinding >](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4feca-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4feca-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4feca-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="4feca-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4feca-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4feca-158">Associações</span><span class="sxs-lookup"><span data-stu-id="4feca-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4feca-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="4feca-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4feca-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4feca-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4feca-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="4feca-161">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="4feca-162">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="4feca-162">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
