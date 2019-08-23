---
title: <add> de <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: 64f0dd5c97ddfcd2fffd8ff4820d02af8c1ced54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926889"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="b4f21-102">\<Adicionar > de \<AllowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="b4f21-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="b4f21-103">Adiciona um URI de destino para o <xref:System.IdentityModel.Tokens.SamlSecurityToken> qual o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="b4f21-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="b4f21-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b4f21-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b4f21-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b4f21-105">\<behaviors></span></span>  
<span data-ttu-id="b4f21-106">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="b4f21-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b4f21-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="b4f21-107">\<behavior></span></span>  
<span data-ttu-id="b4f21-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="b4f21-108">\<serviceCredentials></span></span>  
<span data-ttu-id="b4f21-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="b4f21-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="b4f21-110">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="b4f21-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="b4f21-111">\<Adicionar > elemento para \<AllowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="b4f21-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4f21-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4f21-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4f21-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b4f21-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b4f21-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b4f21-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4f21-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="b4f21-115">Attributes</span></span>  
  
|<span data-ttu-id="b4f21-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="b4f21-116">Attribute</span></span>|<span data-ttu-id="b4f21-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4f21-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b4f21-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="b4f21-118">allowedAudienceUri</span></span>|<span data-ttu-id="b4f21-119">Uma cadeia de caracteres que contém um URI de destino <xref:System.IdentityModel.Tokens.SamlSecurityToken> para o qual o token de segurança pode ser direcionado para ser considerado <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> válido por uma instância.</span><span class="sxs-lookup"><span data-stu-id="b4f21-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4f21-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b4f21-120">Child Elements</span></span>  
 <span data-ttu-id="b4f21-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b4f21-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b4f21-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b4f21-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b4f21-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4f21-123">Element</span></span>|<span data-ttu-id="b4f21-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4f21-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4f21-125">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="b4f21-125">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)|<span data-ttu-id="b4f21-126">Representa uma coleção de URIs de destino para as <xref:System.IdentityModel.Tokens.SamlSecurityToken> quais o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="b4f21-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4f21-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4f21-127">Remarks</span></span>  
 <span data-ttu-id="b4f21-128">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que <xref:System.IdentityModel.Tokens.SamlSecurityToken> emite tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="b4f21-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="b4f21-129">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços Web para os quais o token de segurança é destinado adicionando <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> um ao token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b4f21-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="b4f21-130">Isso permite <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> que o para o serviço Web de destinatário Verifique se o token de segurança emitido destina-se a esse serviço Web, especificando que essa verificação deve acontecer fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b4f21-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="b4f21-131">Defina o `audienceUriMode` atributo de `<issuedTokenAuthentication>` como <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="b4f21-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="b4f21-132">Especifique o conjunto de URIs válidos adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="b4f21-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="b4f21-133">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="b4f21-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="b4f21-134">Para obter mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="b4f21-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f21-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4f21-135">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="b4f21-136">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="b4f21-136">\<allowedAudienceUris></span></span>](allowedaudienceuris.md)
- [<span data-ttu-id="b4f21-137">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="b4f21-137">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="b4f21-138">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b4f21-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b4f21-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b4f21-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b4f21-140">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="b4f21-140">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
