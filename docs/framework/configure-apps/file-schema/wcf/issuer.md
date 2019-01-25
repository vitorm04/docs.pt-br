---
title: '&lt;issuer&gt;'
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 8313d7e361356e5159d1f2d531a6dd34ae7ff4d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612171"
---
# <a name="ltissuergt"></a><span data-ttu-id="366a1-102">&lt;issuer&gt;</span><span class="sxs-lookup"><span data-stu-id="366a1-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="366a1-103">Especifica a Security Token Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="366a1-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="366a1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="366a1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="366a1-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="366a1-105">\<bindings></span></span>  
<span data-ttu-id="366a1-106">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="366a1-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="366a1-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="366a1-107">\<binding></span></span>  
<span data-ttu-id="366a1-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="366a1-108">\<security></span></span>  
<span data-ttu-id="366a1-109">\<message></span><span class="sxs-lookup"><span data-stu-id="366a1-109">\<message></span></span>  
<span data-ttu-id="366a1-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="366a1-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="366a1-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="366a1-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="366a1-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="366a1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="366a1-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="366a1-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="366a1-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="366a1-114">Attributes</span></span>  
  
|<span data-ttu-id="366a1-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="366a1-115">Attribute</span></span>|<span data-ttu-id="366a1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="366a1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="366a1-117">endereço</span><span class="sxs-lookup"><span data-stu-id="366a1-117">address</span></span>|<span data-ttu-id="366a1-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="366a1-118">Required string.</span></span> <span data-ttu-id="366a1-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="366a1-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="366a1-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="366a1-120">Child Elements</span></span>  
  
|<span data-ttu-id="366a1-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="366a1-121">Element</span></span>|<span data-ttu-id="366a1-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="366a1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="366a1-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="366a1-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="366a1-124">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="366a1-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="366a1-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="366a1-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="366a1-126">Ao usar um token emitido, especifica as configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="366a1-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="366a1-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="366a1-127">Parent Elements</span></span>  
  
|<span data-ttu-id="366a1-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="366a1-128">Element</span></span>|<span data-ttu-id="366a1-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="366a1-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="366a1-130">\<message></span><span class="sxs-lookup"><span data-stu-id="366a1-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="366a1-131">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="366a1-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="366a1-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="366a1-132">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="366a1-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="366a1-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="366a1-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="366a1-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="366a1-135">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="366a1-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="366a1-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="366a1-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="366a1-137">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="366a1-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="366a1-138">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="366a1-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
