---
title: '&lt;Emissor&gt;'
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 638b206f5372a654eca68d2f6ebb69bb0ac9e241
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750551"
---
# <a name="ltissuergt"></a><span data-ttu-id="23e6c-102">&lt;Emissor&gt;</span><span class="sxs-lookup"><span data-stu-id="23e6c-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="23e6c-103">Especifica o Token de segurança Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="23e6c-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="23e6c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="23e6c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="23e6c-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="23e6c-105">\<bindings></span></span>  
<span data-ttu-id="23e6c-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="23e6c-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="23e6c-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="23e6c-107">\<binding></span></span>  
<span data-ttu-id="23e6c-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="23e6c-108">\<security></span></span>  
<span data-ttu-id="23e6c-109">\<message></span><span class="sxs-lookup"><span data-stu-id="23e6c-109">\<message></span></span>  
<span data-ttu-id="23e6c-110">\<emissor ></span><span class="sxs-lookup"><span data-stu-id="23e6c-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e6c-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23e6c-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" >  
   <headers>  
      <add name="String"  
                 namespace="String" />  
   </headers>  
   <identity>  
           <certificate encodedValue="String"/>  
      <certificateReference findValue="String"   
         isChainIncluded="Boolean"  
         storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
         storeLocation="LocalMachine/CurrentUser"  
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23e6c-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="23e6c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="23e6c-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="23e6c-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23e6c-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="23e6c-114">Attributes</span></span>  
  
|<span data-ttu-id="23e6c-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="23e6c-115">Attribute</span></span>|<span data-ttu-id="23e6c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e6c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23e6c-117">endereço</span><span class="sxs-lookup"><span data-stu-id="23e6c-117">address</span></span>|<span data-ttu-id="23e6c-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="23e6c-118">Required string.</span></span> <span data-ttu-id="23e6c-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="23e6c-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23e6c-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="23e6c-120">Child Elements</span></span>  
  
|<span data-ttu-id="23e6c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="23e6c-121">Element</span></span>|<span data-ttu-id="23e6c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e6c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23e6c-123">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="23e6c-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="23e6c-124">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="23e6c-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="23e6c-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="23e6c-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="23e6c-126">Ao usar um token emitido, especifica configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="23e6c-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23e6c-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="23e6c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="23e6c-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="23e6c-128">Element</span></span>|<span data-ttu-id="23e6c-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e6c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23e6c-130">\<message></span><span class="sxs-lookup"><span data-stu-id="23e6c-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="23e6c-131">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="23e6c-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23e6c-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23e6c-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="23e6c-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="23e6c-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="23e6c-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="23e6c-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="23e6c-135">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="23e6c-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="23e6c-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="23e6c-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="23e6c-137">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="23e6c-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="23e6c-138">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="23e6c-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
