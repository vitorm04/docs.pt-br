---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 30a53c11b551623311f7ca3f957143fc702568a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251844"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="fffbc-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="fffbc-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="fffbc-102">Registra o resolvedor de token de serviço que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="fffbc-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="fffbc-103">O resolvedor de token de serviço é usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="fffbc-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="fffbc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fffbc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fffbc-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="fffbc-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="fffbc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="fffbc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="fffbc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="fffbc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="fffbc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlerConfiguration**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="fffbc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="fffbc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> serviceTokenResolver**</span><span class="sxs-lookup"><span data-stu-id="fffbc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fffbc-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fffbc-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fffbc-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fffbc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fffbc-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fffbc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fffbc-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="fffbc-113">Attributes</span></span>  
  
|<span data-ttu-id="fffbc-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="fffbc-114">Attribute</span></span>|<span data-ttu-id="fffbc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="fffbc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fffbc-116">tipo</span><span class="sxs-lookup"><span data-stu-id="fffbc-116">type</span></span>|<span data-ttu-id="fffbc-117">Especifica o tipo do resolvedor de token de serviço.</span><span class="sxs-lookup"><span data-stu-id="fffbc-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="fffbc-118">O <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tipo ou um tipo que deriva <xref:System.IdentityModel.Selectors.SecurityTokenResolver> da classe.</span><span class="sxs-lookup"><span data-stu-id="fffbc-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="fffbc-119">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="fffbc-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="fffbc-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fffbc-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fffbc-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fffbc-121">Child Elements</span></span>  
 <span data-ttu-id="fffbc-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="fffbc-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fffbc-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fffbc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fffbc-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="fffbc-124">Element</span></span>|<span data-ttu-id="fffbc-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="fffbc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fffbc-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="fffbc-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="fffbc-127">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="fffbc-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fffbc-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="fffbc-128">Remarks</span></span>  
 <span data-ttu-id="fffbc-129">O resolvedor de token de serviço pode ser usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="fffbc-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="fffbc-130">Ele é usado para recuperar a chave que deve ser usada para descriptografar tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="fffbc-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="fffbc-131">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="fffbc-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="fffbc-132">O tipo especificado pode ser <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou um tipo personalizado que deriva <xref:System.IdentityModel.Selectors.SecurityTokenResolver> da classe.</span><span class="sxs-lookup"><span data-stu-id="fffbc-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="fffbc-133">Alguns manipuladores de token permitem que você especifique as configurações do resolvedor de token de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="fffbc-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="fffbc-134">As configurações em manipuladores de token individuais substituem aquelas especificadas na coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="fffbc-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fffbc-135">A especificação `<serviceTokenResolver>` do elemento como um elemento filho [ \<do elemento > identityConfiguration](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fffbc-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="fffbc-136">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas `<identityConfiguration>` no elemento.</span><span class="sxs-lookup"><span data-stu-id="fffbc-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fffbc-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fffbc-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
 