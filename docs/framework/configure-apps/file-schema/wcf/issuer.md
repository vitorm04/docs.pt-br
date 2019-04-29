---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 37d935287fa7dfba640c39071295fd660f4db7c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756254"
---
# <a name="issuer"></a><span data-ttu-id="9e485-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="9e485-101">\<issuer></span></span>
<span data-ttu-id="9e485-102">Especifica a Security Token Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="9e485-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="9e485-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9e485-103">\<system.serviceModel></span></span>  
<span data-ttu-id="9e485-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9e485-104">\<bindings></span></span>  
<span data-ttu-id="9e485-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9e485-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="9e485-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="9e485-106">\<binding></span></span>  
<span data-ttu-id="9e485-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="9e485-107">\<security></span></span>  
<span data-ttu-id="9e485-108">\<message></span><span class="sxs-lookup"><span data-stu-id="9e485-108">\<message></span></span>  
<span data-ttu-id="9e485-109">\<issuer></span><span class="sxs-lookup"><span data-stu-id="9e485-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e485-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e485-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e485-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9e485-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9e485-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="9e485-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e485-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="9e485-113">Attributes</span></span>  
  
|<span data-ttu-id="9e485-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="9e485-114">Attribute</span></span>|<span data-ttu-id="9e485-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e485-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e485-116">endereço</span><span class="sxs-lookup"><span data-stu-id="9e485-116">address</span></span>|<span data-ttu-id="9e485-117">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="9e485-117">Required string.</span></span> <span data-ttu-id="9e485-118">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="9e485-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e485-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9e485-119">Child Elements</span></span>  
  
|<span data-ttu-id="9e485-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e485-120">Element</span></span>|<span data-ttu-id="9e485-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e485-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e485-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="9e485-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="9e485-123">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9e485-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="9e485-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="9e485-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="9e485-125">Ao usar um token emitido, especifica as configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="9e485-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e485-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9e485-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9e485-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e485-127">Element</span></span>|<span data-ttu-id="9e485-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e485-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e485-129">\<message></span><span class="sxs-lookup"><span data-stu-id="9e485-129">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="9e485-130">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="9e485-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e485-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e485-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="9e485-132">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="9e485-132">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9e485-133">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="9e485-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9e485-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="9e485-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9e485-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="9e485-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9e485-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="9e485-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="9e485-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="9e485-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
