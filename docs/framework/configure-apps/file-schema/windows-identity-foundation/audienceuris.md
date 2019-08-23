---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941952"
---
# <a name="audienceuris"></a><span data-ttu-id="3a41f-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="3a41f-101">\<audienceUris></span></span>
<span data-ttu-id="3a41f-102">Especifica o conjunto de URIs que são identificadores aceitáveis da terceira parte confiável (RP).</span><span class="sxs-lookup"><span data-stu-id="3a41f-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="3a41f-103">Os tokens não serão aceitos, a menos que eles estejam no escopo de um dos URIs de público permitidos.</span><span class="sxs-lookup"><span data-stu-id="3a41f-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="3a41f-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3a41f-104">\<system.identityModel></span></span>  
<span data-ttu-id="3a41f-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3a41f-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3a41f-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="3a41f-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3a41f-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="3a41f-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="3a41f-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="3a41f-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a41f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a41f-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a41f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a41f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3a41f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a41f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a41f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a41f-112">Attributes</span></span>  
  
|<span data-ttu-id="3a41f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3a41f-113">Attribute</span></span>|<span data-ttu-id="3a41f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a41f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a41f-115">modo</span><span class="sxs-lookup"><span data-stu-id="3a41f-115">mode</span></span>|<span data-ttu-id="3a41f-116">Um <xref:System.IdentityModel.Selectors.AudienceUriMode> valor que especifica se a restrição de audiência deve ser aplicada a um token de entrada.</span><span class="sxs-lookup"><span data-stu-id="3a41f-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="3a41f-117">Os valores possíveis são "Always", "Never" e "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="3a41f-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="3a41f-118">O padrão é "Always".</span><span class="sxs-lookup"><span data-stu-id="3a41f-118">The default is "Always".</span></span> <span data-ttu-id="3a41f-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3a41f-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a41f-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a41f-120">Child Elements</span></span>  
  
|<span data-ttu-id="3a41f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a41f-121">Element</span></span>|<span data-ttu-id="3a41f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a41f-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="3a41f-123">Adiciona o URI especificado pelo `value` atributo à coleção audienceUris.</span><span class="sxs-lookup"><span data-stu-id="3a41f-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="3a41f-124">O atributo `value` é necessário.</span><span class="sxs-lookup"><span data-stu-id="3a41f-124">The `value` attribute is required.</span></span> <span data-ttu-id="3a41f-125">O URI diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="3a41f-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="3a41f-126">Limpa a coleção audienceUris.</span><span class="sxs-lookup"><span data-stu-id="3a41f-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="3a41f-127">Todos os identificadores são removidos da coleção.</span><span class="sxs-lookup"><span data-stu-id="3a41f-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="3a41f-128">Remove o URI especificado pelo `value` atributo da coleção audienceUris.</span><span class="sxs-lookup"><span data-stu-id="3a41f-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="3a41f-129">O atributo `value` é necessário.</span><span class="sxs-lookup"><span data-stu-id="3a41f-129">The `value` attribute is required.</span></span> <span data-ttu-id="3a41f-130">O URI diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="3a41f-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a41f-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a41f-131">Parent Elements</span></span>  
  
|<span data-ttu-id="3a41f-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a41f-132">Element</span></span>|<span data-ttu-id="3a41f-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a41f-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a41f-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="3a41f-134">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="3a41f-135">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="3a41f-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a41f-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a41f-136">Remarks</span></span>  
 <span data-ttu-id="3a41f-137">Por padrão, a coleção está vazia; Use `<add>`os `<clear>`elementos, `<remove>` e para modificar a coleção.</span><span class="sxs-lookup"><span data-stu-id="3a41f-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="3a41f-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>e <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> os objetos usam os valores na coleção de URI de audiência para configurar quaisquer restrições de URI <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> de audiência permitidas em objetos.</span><span class="sxs-lookup"><span data-stu-id="3a41f-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="3a41f-139">O `<audienceUris>` elemento é representado <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> pela classe.</span><span class="sxs-lookup"><span data-stu-id="3a41f-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="3a41f-140">Um URI individual adicionado à coleção é representado pela <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.</span><span class="sxs-lookup"><span data-stu-id="3a41f-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a41f-141">O uso do `<audienceUris>` elemento como um elemento filho [ \<do elemento > identityConfiguration](identityconfiguration.md) foi preterido, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="3a41f-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="3a41f-142">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas `<identityConfiguration>` no elemento.</span><span class="sxs-lookup"><span data-stu-id="3a41f-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a41f-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a41f-143">Example</span></span>  
 <span data-ttu-id="3a41f-144">O XML a seguir mostra como configurar os URIs de público aceitáveis para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a41f-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="3a41f-145">Este exemplo configura um único URI.</span><span class="sxs-lookup"><span data-stu-id="3a41f-145">This example configures a single URI.</span></span> <span data-ttu-id="3a41f-146">Os tokens com escopo definido para esse URI serão aceitos, todos os outros serão rejeitados.</span><span class="sxs-lookup"><span data-stu-id="3a41f-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
