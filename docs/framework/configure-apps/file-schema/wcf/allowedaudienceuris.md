---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: 03888600a89d72f5216c8c8cac21c9da96879ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919972"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="8c4f7-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="8c4f7-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="8c4f7-102">Representa uma coleção de URIs de destino para as <xref:System.IdentityModel.Tokens.SamlSecurityToken> quais o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="8c4f7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8c4f7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8c4f7-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="8c4f7-104">\<behaviors></span></span>  
<span data-ttu-id="8c4f7-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="8c4f7-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="8c4f7-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="8c4f7-106">\<behavior></span></span>  
<span data-ttu-id="8c4f7-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="8c4f7-107">\<serviceCredentials></span></span>  
<span data-ttu-id="8c4f7-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="8c4f7-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="8c4f7-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="8c4f7-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c4f7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c4f7-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c4f7-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8c4f7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8c4f7-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="8c4f7-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c4f7-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="8c4f7-113">Attributes</span></span>  
 <span data-ttu-id="8c4f7-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8c4f7-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8c4f7-115">Child Elements</span></span>  
  
|<span data-ttu-id="8c4f7-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c4f7-116">Element</span></span>|<span data-ttu-id="8c4f7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c4f7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c4f7-118">\<add></span><span class="sxs-lookup"><span data-stu-id="8c4f7-118">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="8c4f7-119">Adiciona um URI de destino para o <xref:System.IdentityModel.Tokens.SamlSecurityToken> qual o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c4f7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8c4f7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8c4f7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c4f7-121">Element</span></span>|<span data-ttu-id="8c4f7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c4f7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c4f7-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="8c4f7-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="8c4f7-124">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c4f7-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c4f7-125">Remarks</span></span>  
 <span data-ttu-id="8c4f7-126">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que <xref:System.IdentityModel.Tokens.SamlSecurityToken> emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="8c4f7-127">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços Web para os quais o token de segurança é destinado adicionando <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> um ao token de segurança.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="8c4f7-128">Isso permite <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> que o para o serviço Web de destinatário Verifique se o token de segurança emitido destina-se a esse serviço Web, especificando que essa verificação deve acontecer fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8c4f7-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="8c4f7-129">Defina o `audienceUriMode` atributo de `<issuedTokenAuthentication>` como <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="8c4f7-130">Especifique o conjunto de URIs válidos adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="8c4f7-131">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="8c4f7-132">Para obter mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="8c4f7-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4f7-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c4f7-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="8c4f7-134">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="8c4f7-134">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="8c4f7-135">\<add></span><span class="sxs-lookup"><span data-stu-id="8c4f7-135">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="8c4f7-136">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="8c4f7-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8c4f7-137">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8c4f7-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8c4f7-138">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="8c4f7-138">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
