---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: ecf26263bf47e8b4609e7adc208f0a59a2fa795b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255179"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="37f41-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="37f41-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="37f41-102">Registra um Gerenciador de autenticação de declarações para as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="37f41-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="37f41-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="37f41-103">\<system.identityModel></span></span>  
<span data-ttu-id="37f41-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="37f41-104">\<identityConfiguration></span></span>  
<span data-ttu-id="37f41-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="37f41-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37f41-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37f41-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37f41-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="37f41-107">Attributes and Elements</span></span>  
 <span data-ttu-id="37f41-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="37f41-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37f41-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="37f41-109">Attributes</span></span>  
  
|<span data-ttu-id="37f41-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="37f41-110">Attribute</span></span>|<span data-ttu-id="37f41-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="37f41-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37f41-112">tipo</span><span class="sxs-lookup"><span data-stu-id="37f41-112">type</span></span>|<span data-ttu-id="37f41-113">Especifica um tipo personalizado que deriva de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="37f41-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="37f41-114">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="37f41-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37f41-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="37f41-115">Child Elements</span></span>  
 <span data-ttu-id="37f41-116">Se não houver nenhuma `type` atributo, ou se o `type` as referências ao atributo de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não tem elementos filho; no entanto, as classes derivadas de <xref:System.Security.Claims.ClaimsAuthenticationManager> pode definir os elementos de configuração filho.</span><span class="sxs-lookup"><span data-stu-id="37f41-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37f41-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="37f41-117">Parent Elements</span></span>  
  
|<span data-ttu-id="37f41-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="37f41-118">Element</span></span>|<span data-ttu-id="37f41-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="37f41-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37f41-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="37f41-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="37f41-121">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="37f41-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37f41-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="37f41-122">Remarks</span></span>  
 <span data-ttu-id="37f41-123">O comportamento padrão fornecido por meio de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe retorna as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="37f41-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="37f41-124">Se nenhum `type` atributo for especificado ou se o `type` atributo especifica a <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não tem elementos filho.</span><span class="sxs-lookup"><span data-stu-id="37f41-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="37f41-125">Você pode especificar o `type` atributo para registrar um tipo derivado do <xref:System.Security.Claims.ClaimsAuthenticationManager> classe para implementar comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="37f41-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="37f41-126">Classes derivadas podem dar suporte a configuração por meio de elementos filho do `<claimsAuthenticationManager>` elemento, substituindo o <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> método para lidar com esses elementos.</span><span class="sxs-lookup"><span data-stu-id="37f41-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="37f41-127">O esquema definido para os elementos filho é até o designer da classe.</span><span class="sxs-lookup"><span data-stu-id="37f41-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="37f41-128">O `<claimsAuthenticationManager>` conjuntos de elemento de <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="37f41-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37f41-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37f41-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
