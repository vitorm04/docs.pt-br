---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 59d47eda97e97629408ece12a1d1dfbe804feb3e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268087"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="c0f89-101">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="c0f89-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="c0f89-102">Registra um Gerenciador de autorização de declarações para as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0f89-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="c0f89-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c0f89-103">\<system.identityModel></span></span>  
<span data-ttu-id="c0f89-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c0f89-104">\<identityConfiguration></span></span>  
<span data-ttu-id="c0f89-105">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="c0f89-105">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0f89-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0f89-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0f89-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0f89-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c0f89-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c0f89-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0f89-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0f89-109">Attributes</span></span>  
  
|<span data-ttu-id="c0f89-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="c0f89-110">Attribute</span></span>|<span data-ttu-id="c0f89-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0f89-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0f89-112">tipo</span><span class="sxs-lookup"><span data-stu-id="c0f89-112">type</span></span>|<span data-ttu-id="c0f89-113">Um tipo personalizado que deriva de <xref:System.Security.Claims.ClaimsAuthorizationManager> classe.</span><span class="sxs-lookup"><span data-stu-id="c0f89-113">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="c0f89-114">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="c0f89-114">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0f89-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0f89-115">Child Elements</span></span>  
 <span data-ttu-id="c0f89-116">Se não houver nenhuma `type` atributo, ou se o `type` as referências ao atributo de <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthorizationManager>` elemento não tem elementos filho; no entanto, as classes derivadas de <xref:System.Security.Claims.ClaimsAuthorizationManager> pode definir os elementos de configuração filho.</span><span class="sxs-lookup"><span data-stu-id="c0f89-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0f89-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0f89-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c0f89-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0f89-118">Element</span></span>|<span data-ttu-id="c0f89-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0f89-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0f89-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c0f89-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="c0f89-121">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0f89-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0f89-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0f89-122">Remarks</span></span>  
 <span data-ttu-id="c0f89-123">O comportamento padrão fornecido por meio de <xref:System.Security.Claims.ClaimsAuthorizationManager> classe sempre autoriza as declarações de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0f89-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="c0f89-124">Se nenhum `type` atributo for especificado ou se o `type` atributo especifica a <xref:System.Security.Claims.ClaimsAuthorizationManager> classe, o `<claimsAuthorizationManager>` elemento não tem elementos filho.</span><span class="sxs-lookup"><span data-stu-id="c0f89-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="c0f89-125">Você pode especificar o `type` atributo para registrar um tipo derivado do <xref:System.Security.Claims.ClaimsAuthorizationManager> classe para implementar comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="c0f89-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="c0f89-126">Classes derivadas podem dar suporte a configuração por meio de elementos filho do `<claimsAuthorizationManager>` elemento, substituindo o <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> método para lidar com esses elementos.</span><span class="sxs-lookup"><span data-stu-id="c0f89-126">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="c0f89-127">O esquema definido para os elementos filho é até o designer da classe.</span><span class="sxs-lookup"><span data-stu-id="c0f89-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c0f89-128">Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou o <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, a configuração de identidade que é referenciado pelo `<federationConfiguration>` elemento configura o Gerenciador de autorização de declarações e a política que é usada para fazer decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="c0f89-128">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="c0f89-129">Isso é verdadeiro, mesmo em cenários que não são cenários passivos na Web, por exemplo, aplicativos do Windows Communication Foundation (WCF) ou um aplicativo que não é baseado na Web.</span><span class="sxs-lookup"><span data-stu-id="c0f89-129">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="c0f89-130">Se o aplicativo não for um aplicativo da Web passivo, o `<claimsAuthorizationManager>` elemento (e seus elementos de política filho, se presente) da configuração de identidade referenciada são as únicas configurações aplicadas.</span><span class="sxs-lookup"><span data-stu-id="c0f89-130">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="c0f89-131">Todas as outras configurações são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="c0f89-131">All other settings are ignored.</span></span> <span data-ttu-id="c0f89-132">Para obter mais informações, consulte o [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c0f89-132">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="c0f89-133">Esse elemento define o <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c0f89-133">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0f89-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0f89-134">Example</span></span>  
 <span data-ttu-id="c0f89-135">O XML a seguir mostra a configuração para a autorização de declarações Gerenciador que implementa a política composta de pares de ação de recurso de cada um deles especifica combinações booleanas as declarações que um solicitante deve ter para executar a ação no recurso.</span><span class="sxs-lookup"><span data-stu-id="c0f89-135">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="c0f89-136">O código que implementa o Gerenciador de autorização de declarações capaz de usar essa política pode ser encontrado na `ClaimsBasedAuthorization` exemplo.</span><span class="sxs-lookup"><span data-stu-id="c0f89-136">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
