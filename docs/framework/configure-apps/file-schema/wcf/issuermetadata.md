---
title: '&lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 22e30e0962ec8d2eb0f7e52f4db143fba9bbf703
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491552"
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="a695b-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="a695b-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="a695b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a695b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a695b-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a695b-104">\<bindings></span></span>  
<span data-ttu-id="a695b-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a695b-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="a695b-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="a695b-106">\<binding></span></span>  
<span data-ttu-id="a695b-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="a695b-107">\<security></span></span>  
<span data-ttu-id="a695b-108">\<message></span><span class="sxs-lookup"><span data-stu-id="a695b-108">\<message></span></span>  
<span data-ttu-id="a695b-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="a695b-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a695b-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a695b-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a695b-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a695b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a695b-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a695b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a695b-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a695b-113">Attributes</span></span>  
  
|<span data-ttu-id="a695b-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a695b-114">Attribute</span></span>|<span data-ttu-id="a695b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a695b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a695b-116">endereço</span><span class="sxs-lookup"><span data-stu-id="a695b-116">address</span></span>|<span data-ttu-id="a695b-117">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a695b-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="a695b-118">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a695b-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="a695b-119">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="a695b-119">The address must be an absolute URI.</span></span> <span data-ttu-id="a695b-120">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a695b-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a695b-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a695b-121">Child Elements</span></span>  
  
|<span data-ttu-id="a695b-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="a695b-122">Element</span></span>|<span data-ttu-id="a695b-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a695b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a695b-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="a695b-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="a695b-125">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="a695b-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="a695b-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="a695b-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="a695b-127">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="a695b-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a695b-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a695b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a695b-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="a695b-129">Element</span></span>|<span data-ttu-id="a695b-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="a695b-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a695b-131">\<message></span><span class="sxs-lookup"><span data-stu-id="a695b-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a695b-132">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a695b-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a695b-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a695b-133">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="a695b-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a695b-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a695b-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a695b-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a695b-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a695b-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a695b-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a695b-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
