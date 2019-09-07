---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397887"
---
# <a name="issuermetadata"></a><span data-ttu-id="bd8fc-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="bd8fc-101">\<issuerMetadata></span></span>

<span data-ttu-id="bd8fc-102">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd8fc-102">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd8fc-103">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bd8fc-103">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bd8fc-104">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bd8fc-104">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bd8fc-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> wsFederationHttpBinding**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="bd8fc-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="bd8fc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="bd8fc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="bd8fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="bd8fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="bd8fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de mensagem**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="bd8fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="bd8fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> issuerMetadata**</span><span class="sxs-lookup"><span data-stu-id="bd8fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8fc-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd8fc-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd8fc-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bd8fc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bd8fc-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bd8fc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd8fc-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="bd8fc-113">Attributes</span></span>  
  
|<span data-ttu-id="bd8fc-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="bd8fc-114">Attribute</span></span>|<span data-ttu-id="bd8fc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd8fc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd8fc-116">endereço</span><span class="sxs-lookup"><span data-stu-id="bd8fc-116">address</span></span>|<span data-ttu-id="bd8fc-117">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bd8fc-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="bd8fc-118">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="bd8fc-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="bd8fc-119">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="bd8fc-119">The address must be an absolute URI.</span></span> <span data-ttu-id="bd8fc-120">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="bd8fc-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd8fc-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bd8fc-121">Child Elements</span></span>  
  
|<span data-ttu-id="bd8fc-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd8fc-122">Element</span></span>|<span data-ttu-id="bd8fc-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd8fc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd8fc-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="bd8fc-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="bd8fc-125">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="bd8fc-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="bd8fc-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="bd8fc-126">\<identity></span></span>](identity.md)|<span data-ttu-id="bd8fc-127">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="bd8fc-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd8fc-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bd8fc-128">Parent Elements</span></span>  
  
|<span data-ttu-id="bd8fc-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd8fc-129">Element</span></span>|<span data-ttu-id="bd8fc-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd8fc-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd8fc-131">\<message></span><span class="sxs-lookup"><span data-stu-id="bd8fc-131">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="bd8fc-132">Define as configurações para a segurança em nível de mensagem para [ \<](wsfederationhttpbinding.md) o elemento de > WSFederationHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="bd8fc-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd8fc-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd8fc-133">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="bd8fc-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="bd8fc-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="bd8fc-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="bd8fc-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="bd8fc-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bd8fc-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="bd8fc-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="bd8fc-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
