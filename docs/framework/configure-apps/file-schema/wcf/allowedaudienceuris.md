---
title: '&lt;allowedAudienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: b7a4ae230e9b8788d9ac23147a3fcf21637dadaf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754074"
---
# <a name="ltallowedaudienceurisgt"></a><span data-ttu-id="be4c9-102">&lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="be4c9-102">&lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="be4c9-103">Representa uma coleção de URIs de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="be4c9-103">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="be4c9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="be4c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="be4c9-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="be4c9-105">\<behaviors></span></span>  
<span data-ttu-id="be4c9-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="be4c9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="be4c9-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="be4c9-107">\<behavior></span></span>  
<span data-ttu-id="be4c9-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="be4c9-108">\<serviceCredentials></span></span>  
<span data-ttu-id="be4c9-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="be4c9-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="be4c9-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="be4c9-110">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be4c9-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be4c9-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be4c9-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="be4c9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="be4c9-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="be4c9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be4c9-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="be4c9-114">Attributes</span></span>  
 <span data-ttu-id="be4c9-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="be4c9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="be4c9-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="be4c9-116">Child Elements</span></span>  
  
|<span data-ttu-id="be4c9-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="be4c9-117">Element</span></span>|<span data-ttu-id="be4c9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="be4c9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be4c9-119">\<add></span><span class="sxs-lookup"><span data-stu-id="be4c9-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="be4c9-120">Adiciona um Uri de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="be4c9-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be4c9-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="be4c9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="be4c9-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="be4c9-122">Element</span></span>|<span data-ttu-id="be4c9-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="be4c9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be4c9-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="be4c9-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="be4c9-125">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="be4c9-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be4c9-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="be4c9-126">Remarks</span></span>  
 <span data-ttu-id="be4c9-127">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que emite <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="be4c9-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="be4c9-128">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços da Web para o qual o token de segurança destina-se com a adição de um <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> para o token de segurança.</span><span class="sxs-lookup"><span data-stu-id="be4c9-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="be4c9-129">Que permite que o <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> para o serviço Web destinatário verificar se o token de segurança emitido destina-se para esse serviço da Web, especificando que essa seleção deve acontecer, fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="be4c9-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="be4c9-130">Definir o `audienceUriMode` atributo de `<issuedTokenAuthentication>` para <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span><span class="sxs-lookup"><span data-stu-id="be4c9-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="be4c9-131">Especifique o conjunto de URIs válidos, adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="be4c9-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="be4c9-132">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="be4c9-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="be4c9-133">Para obter mais informações sobre como usar este elemento de configuração, consulte [como: configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="be4c9-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be4c9-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be4c9-134">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="be4c9-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="be4c9-135">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="be4c9-136">\<add></span><span class="sxs-lookup"><span data-stu-id="be4c9-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)  
 [<span data-ttu-id="be4c9-137">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="be4c9-137">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="be4c9-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="be4c9-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="be4c9-139">Como configurar as credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="be4c9-139">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
