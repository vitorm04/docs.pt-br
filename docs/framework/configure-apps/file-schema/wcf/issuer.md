---
title: '&lt;emissor&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 235888aa97238489a51c2ea065efa0575e0d3724
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="d2c0e-102">&lt;emissor&gt;</span><span class="sxs-lookup"><span data-stu-id="d2c0e-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="d2c0e-103">Especifica o Token de segurança Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="d2c0e-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="d2c0e-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d2c0e-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-105">\<bindings></span></span>  
<span data-ttu-id="d2c0e-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="d2c0e-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-107">\<binding></span></span>  
<span data-ttu-id="d2c0e-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-108">\<security></span></span>  
<span data-ttu-id="d2c0e-109">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-109">\<message></span></span>  
<span data-ttu-id="d2c0e-110">\<emissor ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c0e-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2c0e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2c0e-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d2c0e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d2c0e-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="d2c0e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2c0e-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="d2c0e-114">Attributes</span></span>  
  
|<span data-ttu-id="d2c0e-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="d2c0e-115">Attribute</span></span>|<span data-ttu-id="d2c0e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2c0e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2c0e-117">endereço</span><span class="sxs-lookup"><span data-stu-id="d2c0e-117">address</span></span>|<span data-ttu-id="d2c0e-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="d2c0e-118">Required string.</span></span> <span data-ttu-id="d2c0e-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="d2c0e-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2c0e-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d2c0e-120">Child Elements</span></span>  
  
|<span data-ttu-id="d2c0e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d2c0e-121">Element</span></span>|<span data-ttu-id="d2c0e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2c0e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2c0e-123">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="d2c0e-124">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d2c0e-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="d2c0e-125">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="d2c0e-126">Ao usar um token emitido, especifica configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="d2c0e-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2c0e-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d2c0e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d2c0e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="d2c0e-128">Element</span></span>|<span data-ttu-id="d2c0e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2c0e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2c0e-130">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="d2c0e-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="d2c0e-131">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d2c0e-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2c0e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2c0e-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="d2c0e-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="d2c0e-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d2c0e-134">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d2c0e-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d2c0e-135">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="d2c0e-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d2c0e-136">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d2c0e-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="d2c0e-137">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d2c0e-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="d2c0e-138">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d2c0e-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
