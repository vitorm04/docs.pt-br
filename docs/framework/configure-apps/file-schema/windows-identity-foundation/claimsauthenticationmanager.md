---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252098"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="4b112-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="4b112-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="4b112-102">Registra um Gerenciador de autenticação de declarações para as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="4b112-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="4b112-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b112-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4b112-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="4b112-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="4b112-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="4b112-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="4b112-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> claimsAuthenticationManager**</span><span class="sxs-lookup"><span data-stu-id="4b112-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b112-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b112-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b112-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4b112-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4b112-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4b112-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b112-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="4b112-110">Attributes</span></span>  
  
|<span data-ttu-id="4b112-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="4b112-111">Attribute</span></span>|<span data-ttu-id="4b112-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b112-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b112-113">tipo</span><span class="sxs-lookup"><span data-stu-id="4b112-113">type</span></span>|<span data-ttu-id="4b112-114">Especifica um tipo personalizado que deriva da <xref:System.Security.Claims.ClaimsAuthenticationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="4b112-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="4b112-115">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="4b112-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b112-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4b112-116">Child Elements</span></span>  
 <span data-ttu-id="4b112-117">Se não houver nenhum `type` atributo ou se o `type` atributo fizer referência à <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não assumirá elementos filho; no entanto, as <xref:System.Security.Claims.ClaimsAuthenticationManager> classes derivadas de podem definir elementos de configuração filho.</span><span class="sxs-lookup"><span data-stu-id="4b112-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b112-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4b112-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4b112-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="4b112-119">Element</span></span>|<span data-ttu-id="4b112-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b112-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b112-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b112-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="4b112-122">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="4b112-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b112-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b112-123">Remarks</span></span>  
 <span data-ttu-id="4b112-124">O comportamento padrão fornecido por meio <xref:System.Security.Claims.ClaimsAuthenticationManager> da classe ecoa as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="4b112-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="4b112-125">Se nenhum `type` atributo for especificado ou se o `type` atributo especificar a <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não assumirá elementos filho.</span><span class="sxs-lookup"><span data-stu-id="4b112-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="4b112-126">Você pode especificar o `type` atributo para registrar um tipo derivado <xref:System.Security.Claims.ClaimsAuthenticationManager> da classe para implementar o comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="4b112-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="4b112-127">Classes derivadas podem dar suporte à configuração por meio de `<claimsAuthenticationManager>` elementos filho do elemento <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> , substituindo o método para lidar com esses elementos.</span><span class="sxs-lookup"><span data-stu-id="4b112-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="4b112-128">O esquema definido para os elementos filho é até o designer da classe.</span><span class="sxs-lookup"><span data-stu-id="4b112-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="4b112-129">O `<claimsAuthenticationManager>` elemento define a <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4b112-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b112-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4b112-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
