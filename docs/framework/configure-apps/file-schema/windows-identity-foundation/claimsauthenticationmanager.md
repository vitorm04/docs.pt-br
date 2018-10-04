---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 0ec7e44363f87e54eae97b70352f520fe87540be
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581817"
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="c453b-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="c453b-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="c453b-103">Registra um Gerenciador de autenticação de declarações para as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="c453b-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="c453b-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c453b-104">\<system.identityModel></span></span>  
<span data-ttu-id="c453b-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c453b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="c453b-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="c453b-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c453b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c453b-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c453b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c453b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c453b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c453b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c453b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c453b-110">Attributes</span></span>  
  
|<span data-ttu-id="c453b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="c453b-111">Attribute</span></span>|<span data-ttu-id="c453b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c453b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c453b-113">tipo</span><span class="sxs-lookup"><span data-stu-id="c453b-113">type</span></span>|<span data-ttu-id="c453b-114">Especifica um tipo personalizado que deriva de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="c453b-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="c453b-115">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="c453b-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c453b-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c453b-116">Child Elements</span></span>  
 <span data-ttu-id="c453b-117">Se não houver nenhuma `type` atributo, ou se o `type` as referências ao atributo de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não tem elementos filho; no entanto, as classes derivadas de <xref:System.Security.Claims.ClaimsAuthenticationManager> pode definir os elementos de configuração filho.</span><span class="sxs-lookup"><span data-stu-id="c453b-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c453b-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c453b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c453b-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="c453b-119">Element</span></span>|<span data-ttu-id="c453b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c453b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c453b-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="c453b-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="c453b-122">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="c453b-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c453b-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="c453b-123">Remarks</span></span>  
 <span data-ttu-id="c453b-124">O comportamento padrão fornecido por meio de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe retorna as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="c453b-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="c453b-125">Se nenhum `type` atributo for especificado ou se o `type` atributo especifica a <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não tem elementos filho.</span><span class="sxs-lookup"><span data-stu-id="c453b-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="c453b-126">Você pode especificar o `type` atributo para registrar um tipo derivado do <xref:System.Security.Claims.ClaimsAuthenticationManager> classe para implementar comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="c453b-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="c453b-127">Classes derivadas podem dar suporte a configuração por meio de elementos filho do `<claimsAuthenticationManager>` elemento, substituindo o <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> método para lidar com esses elementos.</span><span class="sxs-lookup"><span data-stu-id="c453b-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="c453b-128">O esquema definido para os elementos filho é até o designer da classe.</span><span class="sxs-lookup"><span data-stu-id="c453b-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="c453b-129">O `<claimsAuthenticationManager>` conjuntos de elemento de <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c453b-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c453b-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c453b-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
