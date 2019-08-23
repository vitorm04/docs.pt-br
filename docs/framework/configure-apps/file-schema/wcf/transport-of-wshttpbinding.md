---
title: <transport> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 384267e3d018d714f95356461eb303bc9ec0cb3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934632"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="ae7d2-102">\<> de transporte \<de WSHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ae7d2-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="ae7d2-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="ae7d2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae7d2-104">\<system.serviceModel></span></span>\
<span data-ttu-id="ae7d2-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ae7d2-105">\<bindings></span></span>\
<span data-ttu-id="ae7d2-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ae7d2-106">\<wsHttpBinding></span></span>\
<span data-ttu-id="ae7d2-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="ae7d2-107">\<binding></span></span>\
<span data-ttu-id="ae7d2-108">\<> de segurança </span><span class="sxs-lookup"><span data-stu-id="ae7d2-108">\<security></span></span>\
<span data-ttu-id="ae7d2-109">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="ae7d2-109">\<transport></span></span>

## <a name="syntax"></a><span data-ttu-id="ae7d2-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae7d2-110">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="ae7d2-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="ae7d2-111">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="ae7d2-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ae7d2-112">Attributes and Elements</span></span>

<span data-ttu-id="ae7d2-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae7d2-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="ae7d2-114">Attributes</span></span>

|<span data-ttu-id="ae7d2-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="ae7d2-115">Attribute</span></span>|<span data-ttu-id="ae7d2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae7d2-116">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="ae7d2-117">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="ae7d2-118">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="ae7d2-119">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="ae7d2-120">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="ae7d2-121">Uma cadeia de caracteres que especifica o realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="ae7d2-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ae7d2-123">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="ae7d2-124">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="ae7d2-125">Um usuário pode consultar o realm de autenticação para determinar que um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="ae7d2-126">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="ae7d2-127">1.  Nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="ae7d2-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="ae7d2-128">2.  WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="ae7d2-129">3.  Sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="ae7d2-130">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ae7d2-131">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="ae7d2-131">clientCredentialType Attribute</span></span>

|<span data-ttu-id="ae7d2-132">Valor</span><span class="sxs-lookup"><span data-stu-id="ae7d2-132">Value</span></span>|<span data-ttu-id="ae7d2-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae7d2-133">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="ae7d2-134">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-134">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="ae7d2-135">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-135">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="ae7d2-136">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-136">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="ae7d2-137">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="ae7d2-138">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-138">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="ae7d2-139">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-139">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="ae7d2-140">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="ae7d2-140">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="ae7d2-141">Valor</span><span class="sxs-lookup"><span data-stu-id="ae7d2-141">Value</span></span>|<span data-ttu-id="ae7d2-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae7d2-142">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="ae7d2-143">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-143">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="ae7d2-144">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-144">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="ae7d2-145">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-145">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="ae7d2-146">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-146">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="ae7d2-147">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-147">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="ae7d2-148">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-148">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ae7d2-149">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ae7d2-149">Child Elements</span></span>

<span data-ttu-id="ae7d2-150">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ae7d2-150">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ae7d2-151">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ae7d2-151">Parent Elements</span></span>

|<span data-ttu-id="ae7d2-152">Elemento</span><span class="sxs-lookup"><span data-stu-id="ae7d2-152">Element</span></span>|<span data-ttu-id="ae7d2-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae7d2-153">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae7d2-154">\<security></span><span class="sxs-lookup"><span data-stu-id="ae7d2-154">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="ae7d2-155">Representa os recursos de segurança do [ \<> de WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ae7d2-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="ae7d2-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae7d2-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="ae7d2-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ae7d2-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ae7d2-158">Associações</span><span class="sxs-lookup"><span data-stu-id="ae7d2-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ae7d2-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ae7d2-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ae7d2-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ae7d2-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ae7d2-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="ae7d2-161">\<binding></span></span>](../../../misc/binding.md)
