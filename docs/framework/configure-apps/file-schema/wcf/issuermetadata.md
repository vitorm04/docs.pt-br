---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: c557bd903462ccf4029b7317cbd45610e3fba165
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264447"
---
# <a name="issuermetadata"></a><span data-ttu-id="51523-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="51523-101">\<issuerMetadata></span></span>
<span data-ttu-id="51523-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="51523-102">\<system.serviceModel></span></span>  
<span data-ttu-id="51523-103">\<bindings></span><span class="sxs-lookup"><span data-stu-id="51523-103">\<bindings></span></span>  
<span data-ttu-id="51523-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="51523-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="51523-105">\<binding></span><span class="sxs-lookup"><span data-stu-id="51523-105">\<binding></span></span>  
<span data-ttu-id="51523-106">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="51523-106">\<security></span></span>  
<span data-ttu-id="51523-107">\<message></span><span class="sxs-lookup"><span data-stu-id="51523-107">\<message></span></span>  
<span data-ttu-id="51523-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="51523-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51523-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51523-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51523-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="51523-110">Attributes and Elements</span></span>  
 <span data-ttu-id="51523-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="51523-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51523-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="51523-112">Attributes</span></span>  
  
|<span data-ttu-id="51523-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="51523-113">Attribute</span></span>|<span data-ttu-id="51523-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="51523-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51523-115">endereço</span><span class="sxs-lookup"><span data-stu-id="51523-115">address</span></span>|<span data-ttu-id="51523-116">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="51523-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="51523-117">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="51523-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="51523-118">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="51523-118">The address must be an absolute URI.</span></span> <span data-ttu-id="51523-119">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="51523-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51523-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="51523-120">Child Elements</span></span>  
  
|<span data-ttu-id="51523-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="51523-121">Element</span></span>|<span data-ttu-id="51523-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="51523-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51523-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="51523-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="51523-124">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="51523-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="51523-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="51523-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="51523-126">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="51523-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51523-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="51523-127">Parent Elements</span></span>  
  
|<span data-ttu-id="51523-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="51523-128">Element</span></span>|<span data-ttu-id="51523-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="51523-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51523-130">\<message></span><span class="sxs-lookup"><span data-stu-id="51523-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="51523-131">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="51523-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51523-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51523-132">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="51523-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="51523-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="51523-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="51523-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="51523-135">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="51523-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="51523-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="51523-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
