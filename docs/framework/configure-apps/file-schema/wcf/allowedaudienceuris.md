---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: ea2d4bb285047939992e9b191abc2dc896bdaa6a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398282"
---
# \<allowedAudienceUris>
<span data-ttu-id="dffdb-101">Representa uma coleção de URIs de destino para as quais o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por uma <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="dffdb-101">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="dffdb-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dffdb-102">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dffdb-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dffdb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="dffdb-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="dffdb-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dffdb-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="dffdb-105">Attributes</span></span>  
 <span data-ttu-id="dffdb-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dffdb-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dffdb-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dffdb-107">Child Elements</span></span>  
  
|<span data-ttu-id="dffdb-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="dffdb-108">Element</span></span>|<span data-ttu-id="dffdb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="dffdb-109">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-allowedaudienceuris.md)|<span data-ttu-id="dffdb-110">Adiciona um URI de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por uma <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="dffdb-110">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dffdb-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dffdb-111">Parent Elements</span></span>  
  
|<span data-ttu-id="dffdb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="dffdb-112">Element</span></span>|<span data-ttu-id="dffdb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dffdb-113">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="dffdb-114">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="dffdb-114">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dffdb-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="dffdb-115">Remarks</span></span>  
 <span data-ttu-id="dffdb-116">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que emite <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="dffdb-116">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="dffdb-117">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços Web para os quais o token de segurança é destinado adicionando um <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> ao token de segurança.</span><span class="sxs-lookup"><span data-stu-id="dffdb-117">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="dffdb-118">Isso permite que o <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> para o serviço Web de destinatário Verifique se o token de segurança emitido destina-se a esse serviço Web, especificando que essa verificação deve acontecer fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dffdb-118">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="dffdb-119">Defina o `audienceUriMode` atributo de `<issuedTokenAuthentication>` como <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> .</span><span class="sxs-lookup"><span data-stu-id="dffdb-119">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="dffdb-120">Especifique o conjunto de URIs válidos adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="dffdb-120">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="dffdb-121">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="dffdb-121">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="dffdb-122">Para obter mais informações sobre como usar esse elemento de configuração, consulte [How to: Configure Credentials on a serviço de Federação](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="dffdb-122">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffdb-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="dffdb-123">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [\<add>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="dffdb-124">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="dffdb-124">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="dffdb-125">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="dffdb-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dffdb-126">Como configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="dffdb-126">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
