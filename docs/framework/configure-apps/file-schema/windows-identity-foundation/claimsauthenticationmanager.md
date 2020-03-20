---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152743"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="b022d-101">\<> de autenticação de autenticação</span><span class="sxs-lookup"><span data-stu-id="b022d-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="b022d-102">Registra um gerente de autenticação de sinistros para as reclamações recebidas.</span><span class="sxs-lookup"><span data-stu-id="b022d-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="b022d-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b022d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b022d-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="b022d-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="b022d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b022d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="b022d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span><span class="sxs-lookup"><span data-stu-id="b022d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b022d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b022d-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b022d-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b022d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b022d-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b022d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b022d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b022d-110">Attributes</span></span>  
  
|<span data-ttu-id="b022d-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b022d-111">Attribute</span></span>|<span data-ttu-id="b022d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b022d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b022d-113">type</span><span class="sxs-lookup"><span data-stu-id="b022d-113">type</span></span>|<span data-ttu-id="b022d-114">Especifica um tipo personalizado que <xref:System.Security.Claims.ClaimsAuthenticationManager> deriva da classe.</span><span class="sxs-lookup"><span data-stu-id="b022d-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="b022d-115">Para obter mais informações `type` sobre como especificar o atributo, consulte [Referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="b022d-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b022d-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b022d-116">Child Elements</span></span>  
 <span data-ttu-id="b022d-117">Se não `type` houver atributo, `type` ou se <xref:System.Security.Claims.ClaimsAuthenticationManager> o `<claimsAuthenticationManager>` atributo fizer referência à classe, o elemento não leva elementos da criança; no entanto, <xref:System.Security.Claims.ClaimsAuthenticationManager> classes derivadas podem definir elementos de configuração filho.</span><span class="sxs-lookup"><span data-stu-id="b022d-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b022d-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b022d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b022d-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b022d-119">Element</span></span>|<span data-ttu-id="b022d-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b022d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b022d-121">\<>de configuração de identidade</span><span class="sxs-lookup"><span data-stu-id="b022d-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="b022d-122">Especifica as configurações de identidade em nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="b022d-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b022d-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="b022d-123">Remarks</span></span>  
 <span data-ttu-id="b022d-124">O comportamento padrão fornecido <xref:System.Security.Claims.ClaimsAuthenticationManager> através da classe ecoa as reivindicações recebidas.</span><span class="sxs-lookup"><span data-stu-id="b022d-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="b022d-125">Se `type` nenhum atributo for `type` especificado ou <xref:System.Security.Claims.ClaimsAuthenticationManager> se `<claimsAuthenticationManager>` o atributo especificar a classe, o elemento não levará elementos da criança.</span><span class="sxs-lookup"><span data-stu-id="b022d-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="b022d-126">Você pode `type` especificar o atributo para <xref:System.Security.Claims.ClaimsAuthenticationManager> registrar um tipo derivado da classe para implementar comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="b022d-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="b022d-127">Classes derivadas podem suportar a `<claimsAuthenticationManager>` configuração através <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> de elementos infantis do elemento, substituindo o método para lidar com esses elementos.</span><span class="sxs-lookup"><span data-stu-id="b022d-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="b022d-128">O esquema definido para os elementos infantis cabe ao designer da classe.</span><span class="sxs-lookup"><span data-stu-id="b022d-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="b022d-129">O `<claimsAuthenticationManager>` elemento <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> define a propriedade.</span><span class="sxs-lookup"><span data-stu-id="b022d-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b022d-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b022d-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
