---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397910"
---
# <a name="issuer"></a><span data-ttu-id="e406e-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="e406e-101">\<issuer></span></span>
<span data-ttu-id="e406e-102">Especifica o serviço de token de segurança (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="e406e-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="e406e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e406e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e406e-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e406e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e406e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e406e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e406e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> wsFederationHttpBinding**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e406e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e406e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="e406e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e406e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e406e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e406e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de mensagem**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e406e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e406e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do emissor**</span><span class="sxs-lookup"><span data-stu-id="e406e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e406e-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e406e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e406e-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e406e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e406e-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="e406e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e406e-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="e406e-114">Attributes</span></span>  
  
|<span data-ttu-id="e406e-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="e406e-115">Attribute</span></span>|<span data-ttu-id="e406e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e406e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e406e-117">endereço</span><span class="sxs-lookup"><span data-stu-id="e406e-117">address</span></span>|<span data-ttu-id="e406e-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="e406e-118">Required string.</span></span> <span data-ttu-id="e406e-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="e406e-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e406e-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e406e-120">Child Elements</span></span>  
  
|<span data-ttu-id="e406e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="e406e-121">Element</span></span>|<span data-ttu-id="e406e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e406e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e406e-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="e406e-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="e406e-124">Uma coleção de cabeçalhos de endereço para os pontos de extremidade que o construtor pode criar.</span><span class="sxs-lookup"><span data-stu-id="e406e-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="e406e-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="e406e-125">\<identity></span></span>](identity.md)|<span data-ttu-id="e406e-126">Ao usar um token emitido, especifica as configurações que permitem que o cliente autentique o servidor.</span><span class="sxs-lookup"><span data-stu-id="e406e-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e406e-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e406e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e406e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="e406e-128">Element</span></span>|<span data-ttu-id="e406e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="e406e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e406e-130">\<message></span><span class="sxs-lookup"><span data-stu-id="e406e-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="e406e-131">Define as configurações para a segurança em nível de mensagem para [ \<](wsfederationhttpbinding.md) o elemento de > WSFederationHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="e406e-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e406e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e406e-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="e406e-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="e406e-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e406e-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="e406e-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e406e-135">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="e406e-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e406e-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="e406e-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e406e-137">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="e406e-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="e406e-138">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="e406e-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
