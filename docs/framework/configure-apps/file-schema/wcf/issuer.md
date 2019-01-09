---
title: '&lt;emissor&gt;'
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: d2728bf3613b41ed9f0810207d27d6d67477afd2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149547"
---
# <a name="ltissuergt"></a><span data-ttu-id="bee44-102">&lt;emissor&gt;</span><span class="sxs-lookup"><span data-stu-id="bee44-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="bee44-103">Especifica a Security Token Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="bee44-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="bee44-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bee44-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bee44-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="bee44-105">\<bindings></span></span>  
<span data-ttu-id="bee44-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="bee44-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="bee44-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="bee44-107">\<binding></span></span>  
<span data-ttu-id="bee44-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="bee44-108">\<security></span></span>  
<span data-ttu-id="bee44-109">\<message></span><span class="sxs-lookup"><span data-stu-id="bee44-109">\<message></span></span>  
<span data-ttu-id="bee44-110">\<emissor ></span><span class="sxs-lookup"><span data-stu-id="bee44-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee44-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bee44-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bee44-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bee44-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bee44-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="bee44-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bee44-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="bee44-114">Attributes</span></span>  
  
|<span data-ttu-id="bee44-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="bee44-115">Attribute</span></span>|<span data-ttu-id="bee44-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="bee44-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bee44-117">endereço</span><span class="sxs-lookup"><span data-stu-id="bee44-117">address</span></span>|<span data-ttu-id="bee44-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="bee44-118">Required string.</span></span> <span data-ttu-id="bee44-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="bee44-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bee44-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bee44-120">Child Elements</span></span>  
  
|<span data-ttu-id="bee44-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="bee44-121">Element</span></span>|<span data-ttu-id="bee44-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="bee44-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bee44-123">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="bee44-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="bee44-124">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="bee44-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="bee44-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="bee44-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="bee44-126">Ao usar um token emitido, especifica as configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="bee44-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bee44-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bee44-127">Parent Elements</span></span>  
  
|<span data-ttu-id="bee44-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="bee44-128">Element</span></span>|<span data-ttu-id="bee44-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="bee44-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bee44-130">\<message></span><span class="sxs-lookup"><span data-stu-id="bee44-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="bee44-131">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="bee44-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bee44-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bee44-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="bee44-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="bee44-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="bee44-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="bee44-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="bee44-135">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="bee44-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="bee44-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="bee44-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="bee44-137">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bee44-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="bee44-138">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="bee44-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
