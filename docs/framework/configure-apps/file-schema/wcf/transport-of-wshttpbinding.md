---
title: <transport> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 95cfa076f62f767af431ff5a0bcc2ca31b824e30
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399236"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="23e94-102">\<> de transporte \<de WSHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="23e94-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="23e94-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="23e94-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="23e94-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="23e94-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="23e94-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="23e94-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="23e94-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="23e94-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="23e94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="23e94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="23e94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="23e94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="23e94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="23e94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="23e94-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transporte**</span><span class="sxs-lookup"><span data-stu-id="23e94-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="23e94-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23e94-111">Syntax</span></span>

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
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="23e94-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="23e94-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="23e94-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="23e94-113">Attributes and Elements</span></span>

<span data-ttu-id="23e94-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="23e94-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="23e94-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="23e94-115">Attributes</span></span>

|<span data-ttu-id="23e94-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="23e94-116">Attribute</span></span>|<span data-ttu-id="23e94-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e94-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="23e94-118">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="23e94-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="23e94-119">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="23e94-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="23e94-120">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="23e94-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="23e94-121">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="23e94-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="23e94-122">Uma cadeia de caracteres que especifica o realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="23e94-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="23e94-123">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="23e94-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="23e94-124">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="23e94-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="23e94-125">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="23e94-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="23e94-126">Um usuário pode consultar o realm de autenticação para determinar que um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="23e94-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="23e94-127">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="23e94-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="23e94-128">1.  Nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="23e94-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="23e94-129">2.  WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="23e94-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="23e94-130">3.  Sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="23e94-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="23e94-131">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="23e94-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="23e94-132">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="23e94-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="23e94-133">Valor</span><span class="sxs-lookup"><span data-stu-id="23e94-133">Value</span></span>|<span data-ttu-id="23e94-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e94-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="23e94-135">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="23e94-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="23e94-136">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="23e94-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="23e94-137">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="23e94-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="23e94-138">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="23e94-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="23e94-139">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="23e94-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="23e94-140">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="23e94-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="23e94-141">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="23e94-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="23e94-142">Valor</span><span class="sxs-lookup"><span data-stu-id="23e94-142">Value</span></span>|<span data-ttu-id="23e94-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e94-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="23e94-144">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="23e94-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="23e94-145">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="23e94-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="23e94-146">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="23e94-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="23e94-147">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="23e94-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="23e94-148">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="23e94-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="23e94-149">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="23e94-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="23e94-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="23e94-150">Child Elements</span></span>

<span data-ttu-id="23e94-151">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="23e94-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="23e94-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="23e94-152">Parent Elements</span></span>

|<span data-ttu-id="23e94-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="23e94-153">Element</span></span>|<span data-ttu-id="23e94-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e94-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23e94-155">\<security></span><span class="sxs-lookup"><span data-stu-id="23e94-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="23e94-156">Representa os recursos de segurança do [ \<> de WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="23e94-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="23e94-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23e94-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="23e94-158">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="23e94-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="23e94-159">Associações</span><span class="sxs-lookup"><span data-stu-id="23e94-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="23e94-160">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="23e94-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="23e94-161">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="23e94-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="23e94-162">\<binding></span><span class="sxs-lookup"><span data-stu-id="23e94-162">\<binding></span></span>](../../../misc/binding.md)
