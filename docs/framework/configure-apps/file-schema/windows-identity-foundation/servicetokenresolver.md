---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c25ea1fc32c93e7eb57ef8ed06d6f786ae0a670e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755754"
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="9b8be-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="9b8be-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="9b8be-103">Registra o resolvedor de token de serviço que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="9b8be-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="9b8be-104">O resolvedor de token de serviço é usado para resolver o token de criptografia em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9b8be-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="9b8be-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9b8be-105">\<system.identityModel></span></span>  
<span data-ttu-id="9b8be-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9b8be-106">\<identityConfiguration></span></span>  
<span data-ttu-id="9b8be-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="9b8be-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="9b8be-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9b8be-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="9b8be-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="9b8be-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8be-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b8be-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b8be-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9b8be-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9b8be-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9b8be-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b8be-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="9b8be-113">Attributes</span></span>  
  
|<span data-ttu-id="9b8be-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="9b8be-114">Attribute</span></span>|<span data-ttu-id="9b8be-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b8be-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9b8be-116">tipo</span><span class="sxs-lookup"><span data-stu-id="9b8be-116">type</span></span>|<span data-ttu-id="9b8be-117">Especifica o tipo de resolvedor de token de serviço.</span><span class="sxs-lookup"><span data-stu-id="9b8be-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="9b8be-118">Ou o <xref:System.IdentityModel.Selectors.SecurityTokenResolver> tipo ou um tipo que deriva de <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="9b8be-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="9b8be-119">Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="9b8be-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="9b8be-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9b8be-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b8be-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9b8be-121">Child Elements</span></span>  
 <span data-ttu-id="9b8be-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9b8be-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b8be-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9b8be-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9b8be-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9b8be-124">Element</span></span>|<span data-ttu-id="9b8be-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b8be-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b8be-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9b8be-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="9b8be-127">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="9b8be-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b8be-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b8be-128">Remarks</span></span>  
 <span data-ttu-id="9b8be-129">O resolvedor de token de serviço pode ser usado para resolver o token de criptografia em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9b8be-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="9b8be-130">Ele é usado para recuperar a chave que deve ser usada para descriptografar tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="9b8be-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="9b8be-131">Você deve especificar o `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="9b8be-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="9b8be-132">O tipo especificado pode ser <xref:System.IdentityModel.Selectors.SecurityTokenResolver> ou um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.SecurityTokenResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="9b8be-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="9b8be-133">Alguns manipuladores de token permitem que você especifique configurações de resolvedor de token de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="9b8be-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="9b8be-134">As configurações em manipuladores de token individuais substituem especificado na coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9b8be-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b8be-135">Especificando o `<serviceTokenResolver>` como um elemento filho do [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento foi substituído, mas ainda há suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9b8be-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="9b8be-136">Configurações de `<securityTokenHandlerConfiguration>` elemento substituem aquelas no `<identityConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="9b8be-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b8be-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b8be-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
