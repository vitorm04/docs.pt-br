---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: ea2d4bb285047939992e9b191abc2dc896bdaa6a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398282"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="5cfe2-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="5cfe2-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="5cfe2-102">Representa uma coleção de URIs de destino para as <xref:System.IdentityModel.Tokens.SamlSecurityToken> quais o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
<span data-ttu-id="5cfe2-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5cfe2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5cfe2-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5cfe2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5cfe2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5cfe2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5cfe2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5cfe2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="5cfe2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5cfe2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="5cfe2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5cfe2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="5cfe2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedTokenAuthentication**](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5cfe2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="5cfe2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> allowedAudienceUris**</span><span class="sxs-lookup"><span data-stu-id="5cfe2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cfe2-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cfe2-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cfe2-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5cfe2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5cfe2-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="5cfe2-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cfe2-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="5cfe2-114">Attributes</span></span>  
 <span data-ttu-id="5cfe2-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5cfe2-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5cfe2-116">Child Elements</span></span>  
  
|<span data-ttu-id="5cfe2-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5cfe2-117">Element</span></span>|<span data-ttu-id="5cfe2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cfe2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cfe2-119">\<add></span><span class="sxs-lookup"><span data-stu-id="5cfe2-119">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="5cfe2-120">Adiciona um URI de destino para o <xref:System.IdentityModel.Tokens.SamlSecurityToken> qual o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5cfe2-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5cfe2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5cfe2-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="5cfe2-122">Element</span></span>|<span data-ttu-id="5cfe2-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cfe2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cfe2-124">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="5cfe2-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="5cfe2-125">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cfe2-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="5cfe2-126">Remarks</span></span>  
 <span data-ttu-id="5cfe2-127">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que <xref:System.IdentityModel.Tokens.SamlSecurityToken> emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="5cfe2-128">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços Web para os quais o token de segurança é destinado adicionando <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> um ao token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="5cfe2-129">Isso permite <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> que o para o serviço Web de destinatário Verifique se o token de segurança emitido destina-se a esse serviço Web, especificando que essa verificação deve acontecer fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5cfe2-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="5cfe2-130">Defina o `audienceUriMode` atributo de `<issuedTokenAuthentication>` como <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="5cfe2-131">Especifique o conjunto de URIs válidos adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="5cfe2-132">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="5cfe2-133">Para obter mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="5cfe2-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cfe2-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cfe2-134">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="5cfe2-135">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="5cfe2-135">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="5cfe2-136">\<add></span><span class="sxs-lookup"><span data-stu-id="5cfe2-136">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="5cfe2-137">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="5cfe2-137">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5cfe2-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5cfe2-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5cfe2-139">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="5cfe2-139">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
