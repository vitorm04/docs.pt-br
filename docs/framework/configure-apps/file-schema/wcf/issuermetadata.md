---
title: '&lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 5f6b8d2f861c4d64a3b81407de4ce13b42d9b864
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752927"
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="d1cda-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="d1cda-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="d1cda-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d1cda-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d1cda-104">\<associações ></span><span class="sxs-lookup"><span data-stu-id="d1cda-104">\<bindings></span></span>  
<span data-ttu-id="d1cda-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d1cda-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="d1cda-106">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d1cda-106">\<binding></span></span>  
<span data-ttu-id="d1cda-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="d1cda-107">\<security></span></span>  
<span data-ttu-id="d1cda-108">\<message></span><span class="sxs-lookup"><span data-stu-id="d1cda-108">\<message></span></span>  
<span data-ttu-id="d1cda-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="d1cda-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1cda-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1cda-110">Syntax</span></span>  
  
```xml  
<issuerMetadata address=String" >  
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
</issuerMetadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1cda-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d1cda-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d1cda-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d1cda-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1cda-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="d1cda-113">Attributes</span></span>  
  
|<span data-ttu-id="d1cda-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="d1cda-114">Attribute</span></span>|<span data-ttu-id="d1cda-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1cda-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1cda-116">endereço</span><span class="sxs-lookup"><span data-stu-id="d1cda-116">address</span></span>|<span data-ttu-id="d1cda-117">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d1cda-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="d1cda-118">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d1cda-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="d1cda-119">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="d1cda-119">The address must be an absolute URI.</span></span> <span data-ttu-id="d1cda-120">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="d1cda-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1cda-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d1cda-121">Child Elements</span></span>  
  
|<span data-ttu-id="d1cda-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1cda-122">Element</span></span>|<span data-ttu-id="d1cda-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1cda-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1cda-124">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="d1cda-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="d1cda-125">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="d1cda-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="d1cda-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="d1cda-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="d1cda-127">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade de troca de mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="d1cda-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1cda-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d1cda-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d1cda-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1cda-129">Element</span></span>|<span data-ttu-id="d1cda-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1cda-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1cda-131">\<message></span><span class="sxs-lookup"><span data-stu-id="d1cda-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="d1cda-132">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d1cda-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1cda-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1cda-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="d1cda-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="d1cda-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d1cda-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d1cda-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d1cda-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d1cda-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="d1cda-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d1cda-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
