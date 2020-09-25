---
title: <add> de <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: bcbc9c7dbc5b57da2de2685fff8eee4aca64f7cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181681"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="f35e3-102">\<add> de \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="f35e3-102">\<add> of \<allowedAudienceUris></span></span>

<span data-ttu-id="f35e3-103">Adiciona um URI de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por uma <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="f35e3-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowedAudienceUris>**](allowedaudienceuris.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="f35e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f35e3-104">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f35e3-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f35e3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f35e3-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f35e3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f35e3-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f35e3-107">Attributes</span></span>  
  
|<span data-ttu-id="f35e3-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="f35e3-108">Attribute</span></span>|<span data-ttu-id="f35e3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f35e3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f35e3-110">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="f35e3-110">allowedAudienceUri</span></span>|<span data-ttu-id="f35e3-111">Uma cadeia de caracteres que contém um URI de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por uma <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="f35e3-111">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f35e3-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f35e3-112">Child Elements</span></span>  

 <span data-ttu-id="f35e3-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f35e3-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f35e3-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f35e3-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f35e3-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f35e3-115">Element</span></span>|<span data-ttu-id="f35e3-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f35e3-116">Description</span></span>|  
|-------------|-----------------|  
|[\<allowedAudienceUris>](allowedaudienceuris.md)|<span data-ttu-id="f35e3-117">Representa uma coleção de URIs de destino para as quais o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por uma <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="f35e3-117">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f35e3-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="f35e3-118">Remarks</span></span>  

 <span data-ttu-id="f35e3-119">Você deve usar essa coleção em um aplicativo federado que utiliza um serviço de token de segurança (STS) que emite <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="f35e3-119">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="f35e3-120">Quando o STS emite o token de segurança, ele pode especificar o URI dos serviços Web para os quais o token de segurança é destinado adicionando um <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> ao token de segurança.</span><span class="sxs-lookup"><span data-stu-id="f35e3-120">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="f35e3-121">Isso permite que o <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> para o serviço Web de destinatário Verifique se o token de segurança emitido destina-se a esse serviço Web, especificando que essa verificação deve acontecer fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f35e3-121">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="f35e3-122">Defina o `audienceUriMode` atributo de `<issuedTokenAuthentication>` como <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> ou <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> .</span><span class="sxs-lookup"><span data-stu-id="f35e3-122">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="f35e3-123">Especifique o conjunto de URIs válidos adicionando os URIs a esta coleção.</span><span class="sxs-lookup"><span data-stu-id="f35e3-123">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="f35e3-124">Para obter mais informações, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="f35e3-124">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="f35e3-125">Para obter mais informações sobre como usar esse elemento de configuração, consulte [How to: Configure Credentials on a serviço de Federação](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="f35e3-125">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35e3-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="f35e3-126">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris>](allowedaudienceuris.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="f35e3-127">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="f35e3-127">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f35e3-128">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f35e3-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f35e3-129">Como: configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="f35e3-129">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
