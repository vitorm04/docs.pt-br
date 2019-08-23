---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 08fda249b526961ff711f439cf729a18e15b412b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929370"
---
# <a name="issuer"></a><span data-ttu-id="da93d-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="da93d-101">\<issuer></span></span>
<span data-ttu-id="da93d-102">Especifica o serviço de token de segurança (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="da93d-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="da93d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="da93d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="da93d-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="da93d-104">\<bindings></span></span>  
<span data-ttu-id="da93d-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="da93d-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="da93d-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="da93d-106">\<binding></span></span>  
<span data-ttu-id="da93d-107">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="da93d-107">\<security></span></span>  
<span data-ttu-id="da93d-108">\<message></span><span class="sxs-lookup"><span data-stu-id="da93d-108">\<message></span></span>  
<span data-ttu-id="da93d-109">\<issuer></span><span class="sxs-lookup"><span data-stu-id="da93d-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da93d-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da93d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da93d-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="da93d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="da93d-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="da93d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da93d-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="da93d-113">Attributes</span></span>  
  
|<span data-ttu-id="da93d-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="da93d-114">Attribute</span></span>|<span data-ttu-id="da93d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="da93d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da93d-116">endereço</span><span class="sxs-lookup"><span data-stu-id="da93d-116">address</span></span>|<span data-ttu-id="da93d-117">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="da93d-117">Required string.</span></span> <span data-ttu-id="da93d-118">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="da93d-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da93d-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="da93d-119">Child Elements</span></span>  
  
|<span data-ttu-id="da93d-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="da93d-120">Element</span></span>|<span data-ttu-id="da93d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="da93d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da93d-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="da93d-122">\<headers></span></span>](headers-element.md)|<span data-ttu-id="da93d-123">Uma coleção de cabeçalhos de endereço para os pontos de extremidade que o construtor pode criar.</span><span class="sxs-lookup"><span data-stu-id="da93d-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="da93d-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="da93d-124">\<identity></span></span>](identity.md)|<span data-ttu-id="da93d-125">Ao usar um token emitido, especifica as configurações que permitem que o cliente autentique o servidor.</span><span class="sxs-lookup"><span data-stu-id="da93d-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da93d-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="da93d-126">Parent Elements</span></span>  
  
|<span data-ttu-id="da93d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="da93d-127">Element</span></span>|<span data-ttu-id="da93d-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="da93d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da93d-129">\<message></span><span class="sxs-lookup"><span data-stu-id="da93d-129">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="da93d-130">Define as configurações para a segurança em nível de mensagem para [ \<](wsfederationhttpbinding.md) o elemento de > WSFederationHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="da93d-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da93d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da93d-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="da93d-132">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="da93d-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="da93d-133">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="da93d-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="da93d-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="da93d-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="da93d-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="da93d-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="da93d-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="da93d-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="da93d-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="da93d-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
