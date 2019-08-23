---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923106"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="5bfd3-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="5bfd3-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="5bfd3-102">Registra o resolvedor de token de serviço que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="5bfd3-103">O resolvedor de token de serviço é usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="5bfd3-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5bfd3-104">\<system.identityModel></span></span>  
<span data-ttu-id="5bfd3-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5bfd3-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5bfd3-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5bfd3-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5bfd3-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="5bfd3-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="5bfd3-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="5bfd3-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfd3-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bfd3-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bfd3-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5bfd3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5bfd3-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bfd3-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5bfd3-112">Attributes</span></span>  
  
|<span data-ttu-id="5bfd3-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5bfd3-113">Attribute</span></span>|<span data-ttu-id="5bfd3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bfd3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bfd3-115">tipo</span><span class="sxs-lookup"><span data-stu-id="5bfd3-115">type</span></span>|<span data-ttu-id="5bfd3-116">Especifica o tipo do resolvedor de token de serviço.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="5bfd3-117">O <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tipo ou um tipo que deriva <xref:System.IdentityModel.Selectors.SecurityTokenResolver> da classe.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="5bfd3-118">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="5bfd3-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="5bfd3-119">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bfd3-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5bfd3-120">Child Elements</span></span>  
 <span data-ttu-id="5bfd3-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5bfd3-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bfd3-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5bfd3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5bfd3-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="5bfd3-123">Element</span></span>|<span data-ttu-id="5bfd3-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bfd3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bfd3-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="5bfd3-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="5bfd3-126">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bfd3-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bfd3-127">Remarks</span></span>  
 <span data-ttu-id="5bfd3-128">O resolvedor de token de serviço pode ser usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="5bfd3-129">Ele é usado para recuperar a chave que deve ser usada para descriptografar tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="5bfd3-130">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="5bfd3-131">O tipo especificado pode ser <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou um tipo personalizado que deriva <xref:System.IdentityModel.Selectors.SecurityTokenResolver> da classe.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="5bfd3-132">Alguns manipuladores de token permitem que você especifique as configurações do resolvedor de token de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="5bfd3-133">As configurações em manipuladores de token individuais substituem aquelas especificadas na coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bfd3-134">A especificação `<serviceTokenResolver>` do elemento como um elemento filho [ \<do elemento > identityConfiguration](identityconfiguration.md) foi preterida, mas ainda tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="5bfd3-135">As configurações no `<securityTokenHandlerConfiguration>` elemento substituem aquelas `<identityConfiguration>` no elemento.</span><span class="sxs-lookup"><span data-stu-id="5bfd3-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bfd3-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5bfd3-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
