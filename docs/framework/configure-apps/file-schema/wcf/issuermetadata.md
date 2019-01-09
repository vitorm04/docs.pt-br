---
title: '&lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 38fa373212464a7dc919c2f364524a391db17d43
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149352"
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="e58d5-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="e58d5-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="e58d5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e58d5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e58d5-104">\<associações ></span><span class="sxs-lookup"><span data-stu-id="e58d5-104">\<bindings></span></span>  
<span data-ttu-id="e58d5-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e58d5-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="e58d5-106">\<associação ></span><span class="sxs-lookup"><span data-stu-id="e58d5-106">\<binding></span></span>  
<span data-ttu-id="e58d5-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="e58d5-107">\<security></span></span>  
<span data-ttu-id="e58d5-108">\<message></span><span class="sxs-lookup"><span data-stu-id="e58d5-108">\<message></span></span>  
<span data-ttu-id="e58d5-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="e58d5-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58d5-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e58d5-110">Syntax</span></span>  
  
```xml  
<issuerMetadata address="String">
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
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e58d5-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e58d5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e58d5-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e58d5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e58d5-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="e58d5-113">Attributes</span></span>  
  
|<span data-ttu-id="e58d5-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="e58d5-114">Attribute</span></span>|<span data-ttu-id="e58d5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e58d5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e58d5-116">endereço</span><span class="sxs-lookup"><span data-stu-id="e58d5-116">address</span></span>|<span data-ttu-id="e58d5-117">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e58d5-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="e58d5-118">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e58d5-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="e58d5-119">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="e58d5-119">The address must be an absolute URI.</span></span> <span data-ttu-id="e58d5-120">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="e58d5-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e58d5-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e58d5-121">Child Elements</span></span>  
  
|<span data-ttu-id="e58d5-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="e58d5-122">Element</span></span>|<span data-ttu-id="e58d5-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="e58d5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e58d5-124">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="e58d5-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="e58d5-125">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="e58d5-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="e58d5-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="e58d5-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e58d5-127">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="e58d5-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e58d5-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e58d5-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e58d5-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="e58d5-129">Element</span></span>|<span data-ttu-id="e58d5-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="e58d5-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e58d5-131">\<message></span><span class="sxs-lookup"><span data-stu-id="e58d5-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="e58d5-132">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="e58d5-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e58d5-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e58d5-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="e58d5-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="e58d5-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="e58d5-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="e58d5-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="e58d5-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="e58d5-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="e58d5-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="e58d5-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
