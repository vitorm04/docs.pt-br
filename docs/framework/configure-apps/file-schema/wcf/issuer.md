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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dcd85443a802db2b6f2e0b1823dd6cb60ed8f705
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="39ed4-102">&lt;emissor&gt;</span><span class="sxs-lookup"><span data-stu-id="39ed4-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="39ed4-103">Especifica o Token de segurança Service (STS) que emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="39ed4-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="39ed4-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="39ed4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="39ed4-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="39ed4-105">\<bindings></span></span>  
<span data-ttu-id="39ed4-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="39ed4-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="39ed4-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="39ed4-107">\<binding></span></span>  
<span data-ttu-id="39ed4-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="39ed4-108">\<security></span></span>  
<span data-ttu-id="39ed4-109">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="39ed4-109">\<message></span></span>  
<span data-ttu-id="39ed4-110">\<emissor ></span><span class="sxs-lookup"><span data-stu-id="39ed4-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39ed4-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39ed4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39ed4-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39ed4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="39ed4-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="39ed4-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39ed4-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="39ed4-114">Attributes</span></span>  
  
|<span data-ttu-id="39ed4-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="39ed4-115">Attribute</span></span>|<span data-ttu-id="39ed4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="39ed4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39ed4-117">endereço</span><span class="sxs-lookup"><span data-stu-id="39ed4-117">address</span></span>|<span data-ttu-id="39ed4-118">Cadeia de caracteres obrigatória.</span><span class="sxs-lookup"><span data-stu-id="39ed4-118">Required string.</span></span> <span data-ttu-id="39ed4-119">A URL do STS.</span><span class="sxs-lookup"><span data-stu-id="39ed4-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39ed4-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39ed4-120">Child Elements</span></span>  
  
|<span data-ttu-id="39ed4-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="39ed4-121">Element</span></span>|<span data-ttu-id="39ed4-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="39ed4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39ed4-123">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="39ed4-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="39ed4-124">Uma coleção de cabeçalhos de endereço para o construtor pode criar os pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="39ed4-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="39ed4-125">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="39ed4-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="39ed4-126">Ao usar um token emitido, especifica configurações que permitem que o cliente autenticar o servidor.</span><span class="sxs-lookup"><span data-stu-id="39ed4-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39ed4-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39ed4-127">Parent Elements</span></span>  
  
|<span data-ttu-id="39ed4-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="39ed4-128">Element</span></span>|<span data-ttu-id="39ed4-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="39ed4-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39ed4-130">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="39ed4-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="39ed4-131">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="39ed4-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39ed4-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39ed4-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="39ed4-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="39ed4-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="39ed4-134">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="39ed4-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="39ed4-135">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="39ed4-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="39ed4-136">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="39ed4-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="39ed4-137">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="39ed4-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="39ed4-138">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="39ed4-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
