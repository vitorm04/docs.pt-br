---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251871"
---
# \<securityTokenHandlers>
<span data-ttu-id="da735-101">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="da735-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="da735-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da735-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da735-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="da735-103">Attributes and Elements</span></span>  
 <span data-ttu-id="da735-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="da735-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da735-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="da735-105">Attributes</span></span>  
  
|<span data-ttu-id="da735-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="da735-106">Attribute</span></span>|<span data-ttu-id="da735-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="da735-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da735-108">name</span><span class="sxs-lookup"><span data-stu-id="da735-108">name</span></span>|<span data-ttu-id="da735-109">Especifica o nome de uma coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="da735-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="da735-110">Os únicos valores reconhecidos pela estrutura são "ActAs" e "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="da735-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="da735-111">Se as coleções do manipulador de token forem especificadas com um desses nomes, a coleção será usada ao processar os tokens ActAs ou OnBehalfOf, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="da735-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da735-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="da735-112">Child Elements</span></span>  
  
|<span data-ttu-id="da735-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="da735-113">Element</span></span>|<span data-ttu-id="da735-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="da735-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="da735-115">Adiciona um manipulador de token de segurança à coleção do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="da735-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="da735-116">Limpa todos os manipuladores de token de segurança da coleção do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="da735-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="da735-117">Remove um manipulador de token de segurança da coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="da735-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="da735-118">Fornece a configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="da735-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da735-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="da735-119">Parent Elements</span></span>  
  
|<span data-ttu-id="da735-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="da735-120">Element</span></span>|<span data-ttu-id="da735-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="da735-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="da735-122">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="da735-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da735-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="da735-123">Remarks</span></span>  
 <span data-ttu-id="da735-124">Você pode especificar uma ou mais coleções nomeadas de manipuladores de token de segurança em uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="da735-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="da735-125">Você pode especificar um nome para uma coleção usando o `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="da735-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="da735-126">Os únicos nomes que a estrutura manipula são "ActAs" e "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="da735-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="da735-127">Se houver manipuladores nessas coleções, eles serão usados por um serviço de token de segurança (STS) em vez dos manipuladores padrão durante o processamento `ActAs` e os `OnBehalfOf` tokens.</span><span class="sxs-lookup"><span data-stu-id="da735-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="da735-128">Por padrão, a coleção é populada com os seguintes tipos de manipuladores:,,,,, <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> e <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="da735-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="da735-129">Você pode modificar a coleção usando os `<add>` elementos, `<remove>` e `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="da735-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="da735-130">Você deve garantir que apenas um único manipulador de qualquer tipo específico exista na coleção.</span><span class="sxs-lookup"><span data-stu-id="da735-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="da735-131">Por exemplo, se você derivar um manipulador da <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, o manipulador ou o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> poderá ser configurado em uma única coleção, mas não em ambos.</span><span class="sxs-lookup"><span data-stu-id="da735-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="da735-132">Use o `<securityTokenHandlerConfiguration>` elemento para especificar as definições de configuração para os manipuladores na coleção.</span><span class="sxs-lookup"><span data-stu-id="da735-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="da735-133">As configurações especificadas por meio desse elemento substituem aquelas especificadas no serviço por meio do [\<identityConfiguration>](identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="da735-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="da735-134">Alguns manipuladores (incluindo vários dos tipos de manipuladores internos) podem dar suporte à configuração adicional por meio de um elemento filho do `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="da735-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="da735-135">As configurações especificadas em um manipulador substituem as configurações equivalentes especificadas na coleção ou no serviço.</span><span class="sxs-lookup"><span data-stu-id="da735-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
