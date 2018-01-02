---
title: '&lt;adicionar&gt; &lt;allowedAudienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b10a0ef5718197464ffa40126f0a013d82256dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a><span data-ttu-id="cbb0a-102">&lt;adicionar&gt; &lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="cbb0a-102">&lt;add&gt; of &lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="cbb0a-103">Adiciona um Uri de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="cbb0a-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cbb0a-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-105">\<behaviors></span></span>  
<span data-ttu-id="cbb0a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cbb0a-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-107">\<behavior></span></span>  
<span data-ttu-id="cbb0a-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-108">\<serviceCredentials></span></span>  
<span data-ttu-id="cbb0a-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="cbb0a-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="cbb0a-111">\<Adicionar > elemento \<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb0a-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbb0a-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbb0a-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cbb0a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cbb0a-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbb0a-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="cbb0a-115">Attributes</span></span>  
  
|<span data-ttu-id="cbb0a-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="cbb0a-116">Attribute</span></span>|<span data-ttu-id="cbb0a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbb0a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbb0a-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="cbb0a-118">allowedAudienceUri</span></span>|<span data-ttu-id="cbb0a-119">Uma cadeia de caracteres que contém uma Uri de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbb0a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cbb0a-120">Child Elements</span></span>  
 <span data-ttu-id="cbb0a-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbb0a-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cbb0a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cbb0a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="cbb0a-123">Element</span></span>|<span data-ttu-id="cbb0a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbb0a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbb0a-125">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="cbb0a-126">Representa uma coleção de URIs de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbb0a-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="cbb0a-127">Remarks</span></span>  
 <span data-ttu-id="cbb0a-128">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que emite <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="cbb0a-129">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços da Web para o qual o token de segurança destina-se com a adição de um <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> para o token de segurança.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="cbb0a-130">Que permite que o <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> para o serviço Web destinatário verificar se o token de segurança emitido destina-se para esse serviço da Web, especificando que essa seleção deve acontecer, fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cbb0a-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="cbb0a-131">Definir o `audienceUriMode` atributo de `<issuedTokenAuthentication>` para <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="cbb0a-132">Especifique o conjunto de URIs válidos, adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="cbb0a-133">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="cbb0a-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="cbb0a-134">Para obter mais informações sobre como usar este elemento de configuração, consulte [como: configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="cbb0a-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb0a-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbb0a-135">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="cbb0a-136">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [<span data-ttu-id="cbb0a-137">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="cbb0a-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="cbb0a-138">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="cbb0a-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="cbb0a-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="cbb0a-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cbb0a-140">Como configurar as credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="cbb0a-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
