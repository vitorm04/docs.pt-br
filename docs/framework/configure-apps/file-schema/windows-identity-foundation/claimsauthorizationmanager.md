---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252077"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="a070e-101">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="a070e-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="a070e-102">Registra um Gerenciador de autorização de declarações para as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="a070e-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
<span data-ttu-id="a070e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a070e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a070e-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="a070e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="a070e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a070e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="a070e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> claimsAuthorizationManager**</span><span class="sxs-lookup"><span data-stu-id="a070e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a070e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a070e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a070e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a070e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a070e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a070e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a070e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a070e-110">Attributes</span></span>  
  
|<span data-ttu-id="a070e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="a070e-111">Attribute</span></span>|<span data-ttu-id="a070e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a070e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a070e-113">tipo</span><span class="sxs-lookup"><span data-stu-id="a070e-113">type</span></span>|<span data-ttu-id="a070e-114">Um tipo personalizado que deriva da <xref:System.Security.Claims.ClaimsAuthorizationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="a070e-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="a070e-115">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="a070e-115">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a070e-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a070e-116">Child Elements</span></span>  
 <span data-ttu-id="a070e-117">Se não houver nenhum `type` atributo ou se o `type` atributo fizer referência à <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthorizationManager>` elemento não assumirá elementos filho; no entanto, as <xref:System.Security.Claims.ClaimsAuthorizationManager> classes derivadas de podem definir elementos de configuração filho.</span><span class="sxs-lookup"><span data-stu-id="a070e-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a070e-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a070e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a070e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a070e-119">Element</span></span>|<span data-ttu-id="a070e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a070e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a070e-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a070e-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="a070e-122">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="a070e-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a070e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="a070e-123">Remarks</span></span>  
 <span data-ttu-id="a070e-124">O comportamento padrão fornecido por meio <xref:System.Security.Claims.ClaimsAuthorizationManager> da classe sempre autoriza as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="a070e-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="a070e-125">Se nenhum `type` atributo for especificado ou se o `type` atributo especificar a <xref:System.Security.Claims.ClaimsAuthorizationManager> classe, o `<claimsAuthorizationManager>` elemento não assumirá elementos filho.</span><span class="sxs-lookup"><span data-stu-id="a070e-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="a070e-126">Você pode especificar o `type` atributo para registrar um tipo derivado <xref:System.Security.Claims.ClaimsAuthorizationManager> da classe para implementar o comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="a070e-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="a070e-127">Classes derivadas podem dar suporte à configuração por meio de `<claimsAuthorizationManager>` elementos filho do elemento <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> , substituindo o método para lidar com esses elementos.</span><span class="sxs-lookup"><span data-stu-id="a070e-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="a070e-128">O esquema definido para os elementos filho é até o designer da classe.</span><span class="sxs-lookup"><span data-stu-id="a070e-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a070e-129">Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, a configuração de identidade referenciada pelo `<federationConfiguration>` elemento configura o Gerenciador de autorização de declarações e a política que é usada para fazer decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="a070e-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="a070e-130">Isso é verdade, mesmo em cenários que não são cenários da Web passivos, por exemplo Windows Communication Foundation (WCF) ou um aplicativo que não é baseado na Web.</span><span class="sxs-lookup"><span data-stu-id="a070e-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="a070e-131">Se o aplicativo não for um aplicativo Web passivo, o `<claimsAuthorizationManager>` elemento (e seus elementos de política filho, se presentes) da configuração de identidade referenciada serão as únicas configurações aplicadas.</span><span class="sxs-lookup"><span data-stu-id="a070e-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="a070e-132">Todas as outras configurações são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="a070e-132">All other settings are ignored.</span></span> <span data-ttu-id="a070e-133">Para obter mais informações, consulte o [ \<elemento federationConfiguration >](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="a070e-133">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="a070e-134">Esse elemento define a <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a070e-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a070e-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a070e-135">Example</span></span>  
 <span data-ttu-id="a070e-136">O XML a seguir mostra a configuração de um Gerenciador de autorização de declarações que implementa a política composta por pares de recurso-ação, cada um dos quais especifica combinações booleanas das declarações que um solicitante deve ter para executar a ação no recurso.</span><span class="sxs-lookup"><span data-stu-id="a070e-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="a070e-137">O código que implementa o Gerenciador de autorização de declarações capaz de usar essa política pode ser encontrado `ClaimsBasedAuthorization` no exemplo.</span><span class="sxs-lookup"><span data-stu-id="a070e-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
