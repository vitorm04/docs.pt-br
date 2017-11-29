---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3151ec3511bca598e5aaabc72b821bdd3aed0b7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlersgt"></a><span data-ttu-id="5184e-102">&lt;securityTokenHandlers&gt;</span><span class="sxs-lookup"><span data-stu-id="5184e-102">&lt;securityTokenHandlers&gt;</span></span>
<span data-ttu-id="5184e-103">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5184e-103">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
 <span data-ttu-id="5184e-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="5184e-104">\<system.identityModel></span></span>  
<span data-ttu-id="5184e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5184e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5184e-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="5184e-106">\<securityTokenHandlers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5184e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5184e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5184e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5184e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5184e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5184e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5184e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5184e-110">Attributes</span></span>  
  
|<span data-ttu-id="5184e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5184e-111">Attribute</span></span>|<span data-ttu-id="5184e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5184e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5184e-113">name</span><span class="sxs-lookup"><span data-stu-id="5184e-113">name</span></span>|<span data-ttu-id="5184e-114">Especifica o nome de uma coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="5184e-114">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="5184e-115">Os únicos valores reconhecidos pela estrutura são "ActAs" e "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="5184e-115">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="5184e-116">Se o manipulador de token coleções é especificadas com qualquer um desses nomes, a coleção será usada ao processamento ActAs ou OnBehalfOf tokens respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5184e-116">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5184e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5184e-117">Child Elements</span></span>  
  
|<span data-ttu-id="5184e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="5184e-118">Element</span></span>|<span data-ttu-id="5184e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5184e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5184e-120">\<add></span><span class="sxs-lookup"><span data-stu-id="5184e-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="5184e-121">Adiciona um manipulador de token de segurança para a coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="5184e-121">Adds a security token handler to the token handler collection.</span></span>|  
|[<span data-ttu-id="5184e-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="5184e-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|<span data-ttu-id="5184e-123">Limpa todos os manipuladores de token de segurança da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="5184e-123">Clears all security token handlers from the token handler collection.</span></span>|  
|[<span data-ttu-id="5184e-124">\<remove></span><span class="sxs-lookup"><span data-stu-id="5184e-124">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|<span data-ttu-id="5184e-125">Remove um manipulador de token de segurança da coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="5184e-125">Removes a security token handler from the token handler collection.</span></span>|  
|[<span data-ttu-id="5184e-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5184e-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="5184e-127">Fornece configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="5184e-127">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5184e-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5184e-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5184e-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="5184e-129">Element</span></span>|<span data-ttu-id="5184e-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="5184e-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5184e-131">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5184e-131">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="5184e-132">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="5184e-132">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5184e-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="5184e-133">Remarks</span></span>  
 <span data-ttu-id="5184e-134">Você pode especificar uma ou mais coleções de manipuladores de token de segurança nomeadas em uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="5184e-134">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="5184e-135">Você pode especificar um nome para uma coleção usando o `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="5184e-135">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="5184e-136">Apenas os nomes que lida com a estrutura são "ActAs" e "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="5184e-136">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="5184e-137">Se existirem manipuladores nessas coleções, são usadas por um serviço de token de segurança (STS) em vez do manipulador padrão durante o processamento `ActAs` e `OnBehalfOf` tokens.</span><span class="sxs-lookup"><span data-stu-id="5184e-137">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="5184e-138">Por padrão, a coleção é preenchida com os seguintes tipos de manipulador: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, e <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="5184e-138">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="5184e-139">Você pode modificar a coleção usando o `<add>`, `<remove>`, e `<clear>` elementos.</span><span class="sxs-lookup"><span data-stu-id="5184e-139">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="5184e-140">Certifique-se de que apenas um único manipulador de qualquer tipo específico existe na coleção.</span><span class="sxs-lookup"><span data-stu-id="5184e-140">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="5184e-141">Por exemplo, se você derivar um manipulador do <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, ou o manipulador ou <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> pode ser configurado em uma única coleção, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="5184e-141">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="5184e-142">Use o `<securityTokenHandlerConfiguration>` elemento para especificar configurações para os manipuladores na coleção.</span><span class="sxs-lookup"><span data-stu-id="5184e-142">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="5184e-143">As configurações especificadas por meio desse elemento substituem aquelas especificadas no serviço por meio de [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="5184e-143">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="5184e-144">Alguns manipuladores (incluindo vários tipos de manipulador internos) podem dar suporte a configuração adicional por meio de um elemento filho do `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="5184e-144">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="5184e-145">As configurações especificadas em um manipulador de substituem configurações equivalentes especificadas na coleção ou o serviço.</span><span class="sxs-lookup"><span data-stu-id="5184e-145">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
