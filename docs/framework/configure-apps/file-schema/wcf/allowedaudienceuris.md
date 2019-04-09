---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: f758fc8e0934f56f9593246497d8aba5084c4a79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143345"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="33e04-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="33e04-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="33e04-102">Representa uma coleção de URIs de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="33e04-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="33e04-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="33e04-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="33e04-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="33e04-104">\<behaviors></span></span>  
<span data-ttu-id="33e04-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="33e04-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="33e04-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="33e04-106">\<behavior></span></span>  
<span data-ttu-id="33e04-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="33e04-107">\<serviceCredentials></span></span>  
<span data-ttu-id="33e04-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="33e04-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="33e04-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="33e04-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e04-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33e04-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33e04-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="33e04-111">Attributes and Elements</span></span>  
 <span data-ttu-id="33e04-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="33e04-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33e04-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="33e04-113">Attributes</span></span>  
 <span data-ttu-id="33e04-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="33e04-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="33e04-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="33e04-115">Child Elements</span></span>  
  
|<span data-ttu-id="33e04-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="33e04-116">Element</span></span>|<span data-ttu-id="33e04-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="33e04-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33e04-118">\<add></span><span class="sxs-lookup"><span data-stu-id="33e04-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="33e04-119">Adiciona um Uri de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="33e04-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33e04-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="33e04-120">Parent Elements</span></span>  
  
|<span data-ttu-id="33e04-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="33e04-121">Element</span></span>|<span data-ttu-id="33e04-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="33e04-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33e04-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="33e04-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="33e04-124">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="33e04-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33e04-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="33e04-125">Remarks</span></span>  
 <span data-ttu-id="33e04-126">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que emite <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="33e04-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="33e04-127">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços da Web para o qual o token de segurança destina-se com a adição de um <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> para o token de segurança.</span><span class="sxs-lookup"><span data-stu-id="33e04-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="33e04-128">Que permite que o <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> para o serviço Web destinatário verificar se o token de segurança emitido é destinado para esse serviço Web, especificando que essa verificação deve acontecer, fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="33e04-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="33e04-129">Defina as `audienceUriMode` atributo de `<issuedTokenAuthentication>` ao <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="33e04-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="33e04-130">Especifique o conjunto de URIs válidos, adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="33e04-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="33e04-131">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="33e04-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="33e04-132">Para obter mais informações sobre como usar este elemento de configuração, consulte [como: Configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="33e04-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e04-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33e04-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="33e04-134">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="33e04-134">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="33e04-135">\<add></span><span class="sxs-lookup"><span data-stu-id="33e04-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)
- [<span data-ttu-id="33e04-136">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="33e04-136">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="33e04-137">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="33e04-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="33e04-138">Como: configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="33e04-138">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
