---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 556c444d5e48e27036c4b49338f6e70de7ef5c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750742"
---
# <a name="audienceuris"></a><span data-ttu-id="8b0fd-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="8b0fd-101">\<audienceUris></span></span>
<span data-ttu-id="8b0fd-102">Especifica o conjunto de URIs que são aceitáveis identificadores da terceira parte confiável (RP).</span><span class="sxs-lookup"><span data-stu-id="8b0fd-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="8b0fd-103">Não serão aceita tokens, a menos que eles estão no escopo para um dos URIs de audiência permitidas.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="8b0fd-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8b0fd-104">\<system.identityModel></span></span>  
<span data-ttu-id="8b0fd-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b0fd-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8b0fd-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="8b0fd-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="8b0fd-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b0fd-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="8b0fd-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="8b0fd-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b0fd-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b0fd-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b0fd-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8b0fd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8b0fd-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b0fd-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b0fd-112">Attributes</span></span>  
  
|<span data-ttu-id="8b0fd-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8b0fd-113">Attribute</span></span>|<span data-ttu-id="8b0fd-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b0fd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b0fd-115">modo</span><span class="sxs-lookup"><span data-stu-id="8b0fd-115">mode</span></span>|<span data-ttu-id="8b0fd-116">Um <xref:System.IdentityModel.Selectors.AudienceUriMode> valor que especifica se a restrição de público-alvo deve ser aplicada a um token de entrada.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="8b0fd-117">Os valores possíveis são "Sempre", "Nunca" e "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="8b0fd-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="8b0fd-118">O padrão é "Sempre".</span><span class="sxs-lookup"><span data-stu-id="8b0fd-118">The default is "Always".</span></span> <span data-ttu-id="8b0fd-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b0fd-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8b0fd-120">Child Elements</span></span>  
  
|<span data-ttu-id="8b0fd-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b0fd-121">Element</span></span>|<span data-ttu-id="8b0fd-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b0fd-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="8b0fd-123">Adiciona o URI especificado pelo `value` atributo à coleção de audienceUris.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="8b0fd-124">O atributo `value` é necessário.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-124">The `value` attribute is required.</span></span> <span data-ttu-id="8b0fd-125">O URI é diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="8b0fd-126">Limpa a coleção de audienceUris.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="8b0fd-127">Todos os identificadores são removidos da coleção.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="8b0fd-128">Remove o URI especificado pelo `value` atributo da coleção de audienceUris.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="8b0fd-129">O atributo `value` é necessário.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-129">The `value` attribute is required.</span></span> <span data-ttu-id="8b0fd-130">O URI é diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b0fd-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8b0fd-131">Parent Elements</span></span>  
  
|<span data-ttu-id="8b0fd-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b0fd-132">Element</span></span>|<span data-ttu-id="8b0fd-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b0fd-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b0fd-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b0fd-134">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="8b0fd-135">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b0fd-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b0fd-136">Remarks</span></span>  
 <span data-ttu-id="8b0fd-137">Por padrão, a coleção estiver vazia; Use `<add>`, `<clear>`, e `<remove>` elementos para modificar a coleção.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="8b0fd-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> e <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objetos usam os valores na coleção de URI público-alvo para configurar qualquer permissão público as restrições de URI em <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objetos.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="8b0fd-139">O `<audienceUris>` elemento é representado pelo <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="8b0fd-140">Um URI individual adicionado à coleção é representado pelo <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b0fd-141">O uso do `<audienceUris>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi preterido, mas ainda há suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="8b0fd-142">Configurações de `<securityTokenHandlerConfiguration>` elemento substituem as o `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b0fd-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b0fd-143">Example</span></span>  
 <span data-ttu-id="8b0fd-144">O XML a seguir mostra como configurar o URIs de público-alvo aceitáveis para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="8b0fd-145">Este exemplo configura um URI único.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-145">This example configures a single URI.</span></span> <span data-ttu-id="8b0fd-146">Tokens no escopo para esse URI serão aceito, todos os outros serão rejeitados.</span><span class="sxs-lookup"><span data-stu-id="8b0fd-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
