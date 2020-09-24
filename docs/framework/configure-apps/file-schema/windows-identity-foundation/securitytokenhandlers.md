---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: d892fbd802ed366ca7af9b85fbf5c23d4d27e0f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156999"
---
# \<securityTokenHandlers>

<span data-ttu-id="1ff52-101">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1ff52-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="1ff52-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ff52-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ff52-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1ff52-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1ff52-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1ff52-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ff52-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="1ff52-105">Attributes</span></span>  
  
|<span data-ttu-id="1ff52-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="1ff52-106">Attribute</span></span>|<span data-ttu-id="1ff52-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ff52-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ff52-108">name</span><span class="sxs-lookup"><span data-stu-id="1ff52-108">name</span></span>|<span data-ttu-id="1ff52-109">Especifica o nome de uma coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="1ff52-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="1ff52-110">Os únicos valores reconhecidos pela estrutura são "ActAs" e "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="1ff52-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="1ff52-111">Se as coleções do manipulador de token forem especificadas com um desses nomes, a coleção será usada ao processar os tokens ActAs ou OnBehalfOf, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1ff52-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ff52-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1ff52-112">Child Elements</span></span>  
  
|<span data-ttu-id="1ff52-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ff52-113">Element</span></span>|<span data-ttu-id="1ff52-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ff52-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="1ff52-115">Adiciona um manipulador de token de segurança à coleção do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="1ff52-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="1ff52-116">Limpa todos os manipuladores de token de segurança da coleção do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="1ff52-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="1ff52-117">Remove um manipulador de token de segurança da coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="1ff52-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="1ff52-118">Fornece a configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="1ff52-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ff52-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1ff52-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1ff52-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ff52-120">Element</span></span>|<span data-ttu-id="1ff52-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ff52-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="1ff52-122">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="1ff52-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ff52-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ff52-123">Remarks</span></span>  

 <span data-ttu-id="1ff52-124">Você pode especificar uma ou mais coleções nomeadas de manipuladores de token de segurança em uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="1ff52-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="1ff52-125">Você pode especificar um nome para uma coleção usando o `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="1ff52-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="1ff52-126">Os únicos nomes que a estrutura manipula são "ActAs" e "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="1ff52-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="1ff52-127">Se houver manipuladores nessas coleções, eles serão usados por um serviço de token de segurança (STS) em vez dos manipuladores padrão durante o processamento `ActAs` e os `OnBehalfOf` tokens.</span><span class="sxs-lookup"><span data-stu-id="1ff52-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="1ff52-128">Por padrão, a coleção é populada com os seguintes tipos de manipuladores:,,,,, <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> e <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="1ff52-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="1ff52-129">Você pode modificar a coleção usando os `<add>` elementos, `<remove>` e `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="1ff52-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="1ff52-130">Você deve garantir que apenas um único manipulador de qualquer tipo específico exista na coleção.</span><span class="sxs-lookup"><span data-stu-id="1ff52-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="1ff52-131">Por exemplo, se você derivar um manipulador da <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, o manipulador ou o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> poderá ser configurado em uma única coleção, mas não em ambos.</span><span class="sxs-lookup"><span data-stu-id="1ff52-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="1ff52-132">Use o `<securityTokenHandlerConfiguration>` elemento para especificar as definições de configuração para os manipuladores na coleção.</span><span class="sxs-lookup"><span data-stu-id="1ff52-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="1ff52-133">As configurações especificadas por meio desse elemento substituem aquelas especificadas no serviço por meio do [\<identityConfiguration>](identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="1ff52-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="1ff52-134">Alguns manipuladores (incluindo vários dos tipos de manipuladores internos) podem dar suporte à configuração adicional por meio de um elemento filho do `<add>` elemento.</span><span class="sxs-lookup"><span data-stu-id="1ff52-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="1ff52-135">As configurações especificadas em um manipulador substituem as configurações equivalentes especificadas na coleção ou no serviço.</span><span class="sxs-lookup"><span data-stu-id="1ff52-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
