---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 1143717882652fc8a03947327b5f1ea89dde7373
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793803"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="b51fe-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="b51fe-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="b51fe-102">Registra o resolvedor de token de serviço que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="b51fe-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="b51fe-103">O resolvedor de token de serviço é usado para resolver o token de criptografia em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b51fe-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="b51fe-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b51fe-104">\<system.identityModel></span></span>  
<span data-ttu-id="b51fe-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b51fe-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b51fe-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="b51fe-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b51fe-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="b51fe-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="b51fe-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="b51fe-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b51fe-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b51fe-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b51fe-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b51fe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b51fe-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b51fe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b51fe-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b51fe-112">Attributes</span></span>  
  
|<span data-ttu-id="b51fe-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b51fe-113">Attribute</span></span>|<span data-ttu-id="b51fe-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b51fe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b51fe-115">tipo</span><span class="sxs-lookup"><span data-stu-id="b51fe-115">type</span></span>|<span data-ttu-id="b51fe-116">Especifica o tipo de resolvedor de token de serviço.</span><span class="sxs-lookup"><span data-stu-id="b51fe-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="b51fe-117">Ambos os <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tipo ou um tipo que deriva a <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="b51fe-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="b51fe-118">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="b51fe-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="b51fe-119">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b51fe-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b51fe-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b51fe-120">Child Elements</span></span>  
 <span data-ttu-id="b51fe-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b51fe-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b51fe-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b51fe-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b51fe-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b51fe-123">Element</span></span>|<span data-ttu-id="b51fe-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b51fe-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b51fe-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="b51fe-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="b51fe-126">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="b51fe-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b51fe-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="b51fe-127">Remarks</span></span>  
 <span data-ttu-id="b51fe-128">O resolvedor de token do serviço pode ser usado para resolver o token de criptografia em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b51fe-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="b51fe-129">Ele é usado para recuperar a chave que deve ser usada para descriptografar tokens recebidos.</span><span class="sxs-lookup"><span data-stu-id="b51fe-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="b51fe-130">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="b51fe-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="b51fe-131">O tipo especificado pode ser <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="b51fe-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="b51fe-132">Alguns manipuladores de token permitem que você especifique configurações de resolvedor de token do serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="b51fe-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="b51fe-133">As configurações em manipuladores de token individuais substituem aqueles especificados na coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b51fe-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b51fe-134">Especificando o `<serviceTokenResolver>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi preterido, mas ainda há suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="b51fe-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="b51fe-135">Configurações de `<securityTokenHandlerConfiguration>` elemento substituem as o `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="b51fe-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b51fe-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b51fe-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
