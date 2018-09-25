---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: af138a4da49a48ed43e1bc8f2c2c81c56892feed
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082442"
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="ba22e-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="ba22e-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="ba22e-103">Especifica o conjunto de URIs que são aceitáveis identificadores da terceira parte confiável (RP).</span><span class="sxs-lookup"><span data-stu-id="ba22e-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="ba22e-104">Não serão aceita tokens, a menos que eles estão no escopo para um dos URIs de audiência permitidas.</span><span class="sxs-lookup"><span data-stu-id="ba22e-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="ba22e-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ba22e-105">\<system.identityModel></span></span>  
<span data-ttu-id="ba22e-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ba22e-106">\<identityConfiguration></span></span>  
<span data-ttu-id="ba22e-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ba22e-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ba22e-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ba22e-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="ba22e-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="ba22e-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba22e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba22e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba22e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ba22e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ba22e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ba22e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba22e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ba22e-113">Attributes</span></span>  
  
|<span data-ttu-id="ba22e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ba22e-114">Attribute</span></span>|<span data-ttu-id="ba22e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba22e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba22e-116">modo</span><span class="sxs-lookup"><span data-stu-id="ba22e-116">mode</span></span>|<span data-ttu-id="ba22e-117">Um <xref:System.IdentityModel.Selectors.AudienceUriMode> valor que especifica se a restrição de público-alvo deve ser aplicada a um token de entrada.</span><span class="sxs-lookup"><span data-stu-id="ba22e-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="ba22e-118">Os valores possíveis são "Sempre", "Nunca" e "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="ba22e-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="ba22e-119">O padrão é "Sempre".</span><span class="sxs-lookup"><span data-stu-id="ba22e-119">The default is "Always".</span></span> <span data-ttu-id="ba22e-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ba22e-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba22e-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ba22e-121">Child Elements</span></span>  
  
|<span data-ttu-id="ba22e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba22e-122">Element</span></span>|<span data-ttu-id="ba22e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba22e-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="ba22e-124">Adiciona o URI especificado pelo `value` atributo à coleção de audienceUris.</span><span class="sxs-lookup"><span data-stu-id="ba22e-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="ba22e-125">O atributo `value` é necessário.</span><span class="sxs-lookup"><span data-stu-id="ba22e-125">The `value` attribute is required.</span></span> <span data-ttu-id="ba22e-126">O URI é diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ba22e-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="ba22e-127">Limpa a coleção de audienceUris.</span><span class="sxs-lookup"><span data-stu-id="ba22e-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="ba22e-128">Todos os identificadores são removidos da coleção.</span><span class="sxs-lookup"><span data-stu-id="ba22e-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="ba22e-129">Remove o URI especificado pelo `value` atributo da coleção de audienceUris.</span><span class="sxs-lookup"><span data-stu-id="ba22e-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="ba22e-130">O atributo `value` é necessário.</span><span class="sxs-lookup"><span data-stu-id="ba22e-130">The `value` attribute is required.</span></span> <span data-ttu-id="ba22e-131">O URI é diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ba22e-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba22e-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ba22e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="ba22e-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba22e-133">Element</span></span>|<span data-ttu-id="ba22e-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba22e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba22e-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ba22e-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="ba22e-136">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="ba22e-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba22e-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba22e-137">Remarks</span></span>  
 <span data-ttu-id="ba22e-138">Por padrão, a coleção estiver vazia; Use `<add>`, `<clear>`, e `<remove>` elementos para modificar a coleção.</span><span class="sxs-lookup"><span data-stu-id="ba22e-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="ba22e-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> e <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objetos usam os valores na coleção de URI público-alvo para configurar qualquer permissão público as restrições de URI em <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objetos.</span><span class="sxs-lookup"><span data-stu-id="ba22e-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="ba22e-140">O `<audienceUris>` elemento é representado pelo <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="ba22e-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="ba22e-141">Um URI individual adicionado à coleção é representado pelo <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.</span><span class="sxs-lookup"><span data-stu-id="ba22e-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba22e-142">O uso do `<audienceUris>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi preterido, mas ainda há suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="ba22e-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="ba22e-143">Configurações de `<securityTokenHandlerConfiguration>` elemento substituem as o `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="ba22e-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba22e-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba22e-144">Example</span></span>  
 <span data-ttu-id="ba22e-145">O XML a seguir mostra como configurar o URIs de público-alvo aceitáveis para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ba22e-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="ba22e-146">Este exemplo configura um URI único.</span><span class="sxs-lookup"><span data-stu-id="ba22e-146">This example configures a single URI.</span></span> <span data-ttu-id="ba22e-147">Tokens no escopo para esse URI serão aceito, todos os outros serão rejeitados.</span><span class="sxs-lookup"><span data-stu-id="ba22e-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
