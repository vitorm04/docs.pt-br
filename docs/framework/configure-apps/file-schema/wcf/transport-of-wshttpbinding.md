---
title: <transport> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732742"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="a8479-102">\<transport> de \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a8479-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="a8479-103">Define as configurações de autenticação para o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8479-103">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="a8479-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8479-104">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="a8479-105">Type</span><span class="sxs-lookup"><span data-stu-id="a8479-105">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="a8479-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a8479-106">Attributes and Elements</span></span>

<span data-ttu-id="a8479-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a8479-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8479-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a8479-108">Attributes</span></span>

|<span data-ttu-id="a8479-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="a8479-109">Attribute</span></span>|<span data-ttu-id="a8479-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8479-110">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="a8479-111">Especifica a credencial usada para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a8479-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="a8479-112">Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="a8479-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="a8479-113">Especifica a credencial usada para autenticar o cliente para um proxy de domínio.</span><span class="sxs-lookup"><span data-stu-id="a8479-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="a8479-114">Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="a8479-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="a8479-115">Uma cadeia de caracteres que especifica o realm de autenticação para Digest ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="a8479-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="a8479-116">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a8479-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a8479-117">Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação.</span><span class="sxs-lookup"><span data-stu-id="a8479-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="a8479-118">Ele também pode especificar uma coleção de usuários que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="a8479-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="a8479-119">Um usuário pode consultar o realm de autenticação para determinar que um dos vários nomes de usuário e senhas possíveis podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="a8479-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="a8479-120">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="a8479-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="a8479-121">1. nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="a8479-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="a8479-122">2. WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="a8479-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="a8479-123">3. sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="a8479-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="a8479-124">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="a8479-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a8479-125">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="a8479-125">clientCredentialType Attribute</span></span>

|<span data-ttu-id="a8479-126">Valor</span><span class="sxs-lookup"><span data-stu-id="a8479-126">Value</span></span>|<span data-ttu-id="a8479-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8479-127">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="a8479-128">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="a8479-128">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="a8479-129">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="a8479-129">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="a8479-130">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="a8479-130">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="a8479-131">Usa a autenticação NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8479-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="a8479-132">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8479-132">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="a8479-133">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a8479-133">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="a8479-134">Atributo proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="a8479-134">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="a8479-135">Valor</span><span class="sxs-lookup"><span data-stu-id="a8479-135">Value</span></span>|<span data-ttu-id="a8479-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8479-136">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="a8479-137">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="a8479-137">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="a8479-138">Usa a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="a8479-138">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="a8479-139">Usa a autenticação Digest.</span><span class="sxs-lookup"><span data-stu-id="a8479-139">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="a8479-140">Usa NTLM como um fallback com um domínio do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8479-140">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="a8479-141">Usa a autenticação integrada do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8479-141">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="a8479-142">Usa certificados X. 509 para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a8479-142">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a8479-143">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a8479-143">Child Elements</span></span>

<span data-ttu-id="a8479-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a8479-144">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8479-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a8479-145">Parent Elements</span></span>

|<span data-ttu-id="a8479-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8479-146">Element</span></span>|<span data-ttu-id="a8479-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8479-147">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="a8479-148">Representa os recursos de segurança do [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a8479-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="a8479-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8479-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="a8479-150">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a8479-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a8479-151">Associações</span><span class="sxs-lookup"><span data-stu-id="a8479-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a8479-152">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="a8479-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a8479-153">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a8479-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
