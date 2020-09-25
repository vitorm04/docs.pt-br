---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: c9787d8e0d8d66494bbf2dbd0e24ff39178a4cde
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189897"
---
# \<audienceUris>

<span data-ttu-id="e8d6e-101">Especifica o conjunto de URIs que são identificadores aceitáveis da terceira parte confiável (RP).</span><span class="sxs-lookup"><span data-stu-id="e8d6e-101">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="e8d6e-102">Os tokens não serão aceitos se eles não forem analisados por uma das URIs de audiência permitidas.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-102">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="e8d6e-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8d6e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8d6e-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e8d6e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e8d6e-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8d6e-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="e8d6e-106">Attributes</span></span>  
  
|<span data-ttu-id="e8d6e-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="e8d6e-107">Attribute</span></span>|<span data-ttu-id="e8d6e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8d6e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8d6e-109">mode</span><span class="sxs-lookup"><span data-stu-id="e8d6e-109">mode</span></span>|<span data-ttu-id="e8d6e-110">Um <xref:System.IdentityModel.Selectors.AudienceUriMode> valor que especifica se a restrição de audiência deve ser aplicada a um token de entrada.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-110">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="e8d6e-111">Os valores possíveis são "Always", "Never" e "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="e8d6e-111">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="e8d6e-112">O padrão é "Always".</span><span class="sxs-lookup"><span data-stu-id="e8d6e-112">The default is "Always".</span></span> <span data-ttu-id="e8d6e-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8d6e-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e8d6e-114">Child Elements</span></span>  
  
|<span data-ttu-id="e8d6e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8d6e-115">Element</span></span>|<span data-ttu-id="e8d6e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8d6e-116">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="e8d6e-117">Adiciona o URI especificado pelo `value` atributo à coleção audienceUris.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-117">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="e8d6e-118">O atributo `value` é necessário.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-118">The `value` attribute is required.</span></span> <span data-ttu-id="e8d6e-119">O URI diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-119">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="e8d6e-120">Limpa a coleção audienceUris.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-120">Clears the audienceUris collection.</span></span> <span data-ttu-id="e8d6e-121">Todos os identificadores são removidos da coleção.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-121">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="e8d6e-122">Remove o URI especificado pelo `value` atributo da coleção audienceUris.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-122">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="e8d6e-123">O atributo `value` é necessário.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-123">The `value` attribute is required.</span></span> <span data-ttu-id="e8d6e-124">O URI diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-124">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8d6e-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e8d6e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e8d6e-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8d6e-126">Element</span></span>|<span data-ttu-id="e8d6e-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8d6e-127">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="e8d6e-128">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8d6e-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8d6e-129">Remarks</span></span>  

 <span data-ttu-id="e8d6e-130">Por padrão, a coleção está vazia; Use `<add>` `<clear>` `<remove>` os elementos, e para modificar a coleção.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-130">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="e8d6e-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> e <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> os objetos usam os valores na coleção de URI de audiência para configurar quaisquer restrições de URI de audiência permitidas em <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objetos.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="e8d6e-132">O `<audienceUris>` elemento é representado pela <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-132">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="e8d6e-133">Um URI individual adicionado à coleção é representado pela <xref:System.IdentityModel.Configuration.AudienceUriElement> classe.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-133">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8d6e-134">O uso do `<audienceUris>` elemento como um elemento filho do elemento foi [\<identityConfiguration>](identityconfiguration.md) preterido, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-134">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="e8d6e-135">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas no `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8d6e-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8d6e-136">Example</span></span>  

 <span data-ttu-id="e8d6e-137">O XML a seguir mostra como configurar os URIs de público aceitáveis para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-137">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="e8d6e-138">Este exemplo configura um único URI.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-138">This example configures a single URI.</span></span> <span data-ttu-id="e8d6e-139">Os tokens com escopo definido para esse URI serão aceitos, todos os outros serão rejeitados.</span><span class="sxs-lookup"><span data-stu-id="e8d6e-139">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
