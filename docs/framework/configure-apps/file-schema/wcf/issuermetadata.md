---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 0dffad6a17720dd0506acbcd60efe4aafe24ed28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761670"
---
# <a name="issuermetadata"></a><span data-ttu-id="3ad30-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="3ad30-101">\<issuerMetadata></span></span>
<span data-ttu-id="3ad30-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ad30-102">\<system.serviceModel></span></span>  
<span data-ttu-id="3ad30-103">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3ad30-103">\<bindings></span></span>  
<span data-ttu-id="3ad30-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3ad30-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="3ad30-105">\<binding></span><span class="sxs-lookup"><span data-stu-id="3ad30-105">\<binding></span></span>  
<span data-ttu-id="3ad30-106">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="3ad30-106">\<security></span></span>  
<span data-ttu-id="3ad30-107">\<message></span><span class="sxs-lookup"><span data-stu-id="3ad30-107">\<message></span></span>  
<span data-ttu-id="3ad30-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="3ad30-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ad30-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ad30-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ad30-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3ad30-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ad30-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3ad30-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ad30-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ad30-112">Attributes</span></span>  
  
|<span data-ttu-id="3ad30-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3ad30-113">Attribute</span></span>|<span data-ttu-id="3ad30-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ad30-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ad30-115">endereço</span><span class="sxs-lookup"><span data-stu-id="3ad30-115">address</span></span>|<span data-ttu-id="3ad30-116">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3ad30-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="3ad30-117">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3ad30-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="3ad30-118">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="3ad30-118">The address must be an absolute URI.</span></span> <span data-ttu-id="3ad30-119">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="3ad30-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ad30-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3ad30-120">Child Elements</span></span>  
  
|<span data-ttu-id="3ad30-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ad30-121">Element</span></span>|<span data-ttu-id="3ad30-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ad30-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ad30-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="3ad30-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="3ad30-124">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="3ad30-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="3ad30-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="3ad30-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="3ad30-126">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="3ad30-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ad30-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3ad30-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3ad30-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ad30-128">Element</span></span>|<span data-ttu-id="3ad30-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ad30-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ad30-130">\<message></span><span class="sxs-lookup"><span data-stu-id="3ad30-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="3ad30-131">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="3ad30-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ad30-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ad30-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="3ad30-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="3ad30-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3ad30-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="3ad30-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3ad30-135">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="3ad30-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3ad30-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="3ad30-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
