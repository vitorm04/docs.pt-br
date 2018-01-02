---
title: '&lt;issuerMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28746481bd24eb0d80304456ea8f34f505a016b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="aa93f-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="aa93f-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="aa93f-103">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="aa93f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="aa93f-104">\<associações ></span><span class="sxs-lookup"><span data-stu-id="aa93f-104">\<bindings></span></span>  
<span data-ttu-id="aa93f-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="aa93f-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="aa93f-106">\<associação ></span><span class="sxs-lookup"><span data-stu-id="aa93f-106">\<binding></span></span>  
<span data-ttu-id="aa93f-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="aa93f-107">\<security></span></span>  
<span data-ttu-id="aa93f-108">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="aa93f-108">\<message></span></span>  
<span data-ttu-id="aa93f-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="aa93f-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa93f-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa93f-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa93f-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="aa93f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aa93f-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="aa93f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa93f-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="aa93f-113">Attributes</span></span>  
  
|<span data-ttu-id="aa93f-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="aa93f-114">Attribute</span></span>|<span data-ttu-id="aa93f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa93f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa93f-116">endereço</span><span class="sxs-lookup"><span data-stu-id="aa93f-116">address</span></span>|<span data-ttu-id="aa93f-117">Atributo `string` obrigatório.</span><span class="sxs-lookup"><span data-stu-id="aa93f-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="aa93f-118">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="aa93f-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="aa93f-119">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="aa93f-119">The address must be an absolute URI.</span></span> <span data-ttu-id="aa93f-120">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="aa93f-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa93f-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="aa93f-121">Child Elements</span></span>  
  
|<span data-ttu-id="aa93f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa93f-122">Element</span></span>|<span data-ttu-id="aa93f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa93f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa93f-124">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="aa93f-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="aa93f-125">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="aa93f-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="aa93f-126">\<identidade ></span><span class="sxs-lookup"><span data-stu-id="aa93f-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="aa93f-127">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade de troca de mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="aa93f-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa93f-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="aa93f-128">Parent Elements</span></span>  
  
|<span data-ttu-id="aa93f-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa93f-129">Element</span></span>|<span data-ttu-id="aa93f-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa93f-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa93f-131">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="aa93f-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="aa93f-132">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="aa93f-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa93f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa93f-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="aa93f-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="aa93f-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="aa93f-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="aa93f-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="aa93f-136">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="aa93f-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="aa93f-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="aa93f-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
