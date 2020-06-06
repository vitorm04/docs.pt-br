---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152743"
---
# \<claimsAuthenticationManager>
<span data-ttu-id="370ff-101">Registra um Gerenciador de autenticação de declarações para as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="370ff-101">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="370ff-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="370ff-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="370ff-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="370ff-103">Attributes and Elements</span></span>  
 <span data-ttu-id="370ff-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="370ff-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="370ff-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="370ff-105">Attributes</span></span>  
  
|<span data-ttu-id="370ff-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="370ff-106">Attribute</span></span>|<span data-ttu-id="370ff-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="370ff-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="370ff-108">type</span><span class="sxs-lookup"><span data-stu-id="370ff-108">type</span></span>|<span data-ttu-id="370ff-109">Especifica um tipo personalizado que deriva da <xref:System.Security.Claims.ClaimsAuthenticationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="370ff-109">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="370ff-110">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="370ff-110">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="370ff-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="370ff-111">Child Elements</span></span>  
 <span data-ttu-id="370ff-112">Se não houver nenhum `type` atributo ou se o `type` atributo fizer referência à <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não assumirá elementos filho; no entanto, as classes derivadas de <xref:System.Security.Claims.ClaimsAuthenticationManager> podem definir elementos de configuração filho.</span><span class="sxs-lookup"><span data-stu-id="370ff-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="370ff-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="370ff-113">Parent Elements</span></span>  
  
|<span data-ttu-id="370ff-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="370ff-114">Element</span></span>|<span data-ttu-id="370ff-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="370ff-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="370ff-116">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="370ff-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="370ff-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="370ff-117">Remarks</span></span>  
 <span data-ttu-id="370ff-118">O comportamento padrão fornecido por meio da <xref:System.Security.Claims.ClaimsAuthenticationManager> classe ecoa as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="370ff-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="370ff-119">Se nenhum `type` atributo for especificado ou se o `type` atributo especificar a <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthenticationManager>` elemento não assumirá elementos filho.</span><span class="sxs-lookup"><span data-stu-id="370ff-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="370ff-120">Você pode especificar o `type` atributo para registrar um tipo derivado da <xref:System.Security.Claims.ClaimsAuthenticationManager> classe para implementar o comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="370ff-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="370ff-121">Classes derivadas podem dar suporte à configuração por meio de elementos filho do `<claimsAuthenticationManager>` elemento, substituindo o <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> método para lidar com esses elementos.</span><span class="sxs-lookup"><span data-stu-id="370ff-121">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="370ff-122">O esquema definido para os elementos filho é até o designer da classe.</span><span class="sxs-lookup"><span data-stu-id="370ff-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="370ff-123">O `<claimsAuthenticationManager>` elemento define a <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="370ff-123">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="370ff-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="370ff-124">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
