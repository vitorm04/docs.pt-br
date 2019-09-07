---
title: <add> de <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: e15cb2d3e525d39a321bbe9760ddb8d72b02fffa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398351"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="29942-102">\<Adicionar > de \<AllowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="29942-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="29942-103">Adiciona um URI de destino para o <xref:System.IdentityModel.Tokens.SamlSecurityToken> qual o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="29942-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
<span data-ttu-id="29942-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="29942-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="29942-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="29942-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="29942-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="29942-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="29942-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="29942-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="29942-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="29942-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="29942-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="29942-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="29942-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedTokenAuthentication**](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="29942-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="29942-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> allowedAudienceUris**](allowedaudienceuris.md)</span><span class="sxs-lookup"><span data-stu-id="29942-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)</span></span>\
<span data-ttu-id="29942-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="29942-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29942-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29942-113">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29942-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="29942-114">Attributes and Elements</span></span>  
 <span data-ttu-id="29942-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="29942-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29942-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="29942-116">Attributes</span></span>  
  
|<span data-ttu-id="29942-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="29942-117">Attribute</span></span>|<span data-ttu-id="29942-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="29942-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29942-119">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="29942-119">allowedAudienceUri</span></span>|<span data-ttu-id="29942-120">Uma cadeia de caracteres que contém um URI de destino <xref:System.IdentityModel.Tokens.SamlSecurityToken> para o qual o token de segurança pode ser direcionado para ser considerado <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> válido por uma instância.</span><span class="sxs-lookup"><span data-stu-id="29942-120">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29942-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="29942-121">Child Elements</span></span>  
 <span data-ttu-id="29942-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="29942-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29942-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="29942-123">Parent Elements</span></span>  
  
|<span data-ttu-id="29942-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="29942-124">Element</span></span>|<span data-ttu-id="29942-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="29942-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29942-126">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="29942-126">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="29942-127">Representa uma coleção de URIs de destino para as <xref:System.IdentityModel.Tokens.SamlSecurityToken> quais o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="29942-127">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29942-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="29942-128">Remarks</span></span>  
 <span data-ttu-id="29942-129">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que <xref:System.IdentityModel.Tokens.SamlSecurityToken> emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="29942-129">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="29942-130">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços Web para os quais o token de segurança é destinado adicionando <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> um ao token de segurança.</span><span class="sxs-lookup"><span data-stu-id="29942-130">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="29942-131">Isso permite <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> que o para o serviço Web de destinatário Verifique se o token de segurança emitido destina-se a esse serviço Web, especificando que essa verificação deve acontecer fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="29942-131">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="29942-132">Defina o `audienceUriMode` atributo de `<issuedTokenAuthentication>` como <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="29942-132">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="29942-133">Especifique o conjunto de URIs válidos adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="29942-133">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="29942-134">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="29942-134">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="29942-135">Para obter mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="29942-135">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29942-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29942-136">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="29942-137">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="29942-137">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="29942-138">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="29942-138">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="29942-139">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="29942-139">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="29942-140">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="29942-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="29942-141">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="29942-141">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
