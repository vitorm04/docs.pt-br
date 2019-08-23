---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942466"
---
# <a name="securitytokenhandlers"></a><span data-ttu-id="60872-101">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="60872-101">\<securityTokenHandlers></span></span>
<span data-ttu-id="60872-102">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="60872-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="60872-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="60872-103">\<system.identityModel></span></span>  
<span data-ttu-id="60872-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="60872-104">\<identityConfiguration></span></span>  
<span data-ttu-id="60872-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="60872-105">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60872-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60872-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60872-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="60872-107">Attributes and Elements</span></span>  
 <span data-ttu-id="60872-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="60872-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60872-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="60872-109">Attributes</span></span>  
  
|<span data-ttu-id="60872-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="60872-110">Attribute</span></span>|<span data-ttu-id="60872-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="60872-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60872-112">name</span><span class="sxs-lookup"><span data-stu-id="60872-112">name</span></span>|<span data-ttu-id="60872-113">Especifica o nome de uma coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="60872-113">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="60872-114">Os únicos valores reconhecidos pela estrutura são "ActAs" e "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="60872-114">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="60872-115">Se as coleções do manipulador de token forem especificadas com um desses nomes, a coleção será usada ao processar os tokens ActAs ou OnBehalfOf, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="60872-115">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60872-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="60872-116">Child Elements</span></span>  
  
|<span data-ttu-id="60872-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="60872-117">Element</span></span>|<span data-ttu-id="60872-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="60872-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60872-119">\<add></span><span class="sxs-lookup"><span data-stu-id="60872-119">\<add></span></span>](add.md)|<span data-ttu-id="60872-120">Adiciona um manipulador de token de segurança à coleção do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="60872-120">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="60872-121">\<clear></span><span class="sxs-lookup"><span data-stu-id="60872-121">\<clear></span></span>](clear.md)|<span data-ttu-id="60872-122">Limpa todos os manipuladores de token de segurança da coleção do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="60872-122">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="60872-123">\<remove></span><span class="sxs-lookup"><span data-stu-id="60872-123">\<remove></span></span>](remove.md)|<span data-ttu-id="60872-124">Remove um manipulador de token de segurança da coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="60872-124">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="60872-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="60872-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="60872-126">Fornece a configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="60872-126">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60872-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="60872-127">Parent Elements</span></span>  
  
|<span data-ttu-id="60872-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="60872-128">Element</span></span>|<span data-ttu-id="60872-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="60872-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60872-130">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="60872-130">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="60872-131">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="60872-131">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60872-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="60872-132">Remarks</span></span>  
 <span data-ttu-id="60872-133">Você pode especificar uma ou mais coleções nomeadas de manipuladores de token de segurança em uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="60872-133">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="60872-134">Você pode especificar um nome para uma coleção usando o `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="60872-134">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="60872-135">Os únicos nomes que a estrutura manipula são "ActAs" e "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="60872-135">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="60872-136">Se houver manipuladores nessas coleções, eles serão usados por um serviço de token de segurança (STS) em vez dos manipuladores padrão `ActAs` durante `OnBehalfOf` o processamento e os tokens.</span><span class="sxs-lookup"><span data-stu-id="60872-136">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="60872-137">Por padrão, a coleção é populada com os seguintes tipos <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>de manipuladores <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>: <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>,, <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>,, e.</span><span class="sxs-lookup"><span data-stu-id="60872-137">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="60872-138">Você pode modificar a coleção usando os `<add>`elementos, `<remove>`e. `<clear>`</span><span class="sxs-lookup"><span data-stu-id="60872-138">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="60872-139">Você deve garantir que apenas um único manipulador de qualquer tipo específico exista na coleção.</span><span class="sxs-lookup"><span data-stu-id="60872-139">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="60872-140">Por exemplo, se você derivar um manipulador da <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, o manipulador ou o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> poderá ser configurado em uma única coleção, mas não em ambos.</span><span class="sxs-lookup"><span data-stu-id="60872-140">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="60872-141">Use o `<securityTokenHandlerConfiguration>` elemento para especificar as definições de configuração para os manipuladores na coleção.</span><span class="sxs-lookup"><span data-stu-id="60872-141">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="60872-142">As configurações especificadas por meio desse elemento substituem aquelas especificadas no serviço por meio do [ \<elemento identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="60872-142">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="60872-143">Alguns manipuladores (incluindo vários dos tipos de manipuladores internos) podem dar suporte à configuração adicional por meio de um elemento `<add>` filho do elemento.</span><span class="sxs-lookup"><span data-stu-id="60872-143">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="60872-144">As configurações especificadas em um manipulador substituem as configurações equivalentes especificadas na coleção ou no serviço.</span><span class="sxs-lookup"><span data-stu-id="60872-144">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
