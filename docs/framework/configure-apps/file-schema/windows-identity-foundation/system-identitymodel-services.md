---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e9488c0681e1a5f0fe94112a36b65ec73bf9fd09
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251805"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="1617e-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="1617e-102">\<system.identityModel.services></span></span>
<span data-ttu-id="1617e-103">A seção de configuração para autenticação usando o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="1617e-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="1617e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1617e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1617e-105">&nbsp;&nbsp; **\<System. identityModel. Services >**</span><span class="sxs-lookup"><span data-stu-id="1617e-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1617e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1617e-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1617e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1617e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1617e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1617e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1617e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="1617e-109">Attributes</span></span>  
 <span data-ttu-id="1617e-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1617e-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1617e-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1617e-111">Child Elements</span></span>  
  
|<span data-ttu-id="1617e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="1617e-112">Element</span></span>|<span data-ttu-id="1617e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1617e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1617e-114">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="1617e-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="1617e-115">Contém as configurações que definem <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> os módulos http (WSFAM <xref:System.IdentityModel.Services.SessionAuthenticationModule> ) e (Sam).</span><span class="sxs-lookup"><span data-stu-id="1617e-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1617e-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1617e-116">Parent Elements</span></span>  
 <span data-ttu-id="1617e-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1617e-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1617e-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="1617e-118">Remarks</span></span>  
 <span data-ttu-id="1617e-119">Adicione uma `<system.identityModel.services>` seção ao arquivo de configuração do aplicativo para fornecer as configurações para o Sam e o WSFAM.</span><span class="sxs-lookup"><span data-stu-id="1617e-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1617e-120">Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, o Gerenciador de autorização<xref:System.Security.Claims.ClaimsAuthorizationManager>de declarações () e a política que é usada para tomar decisões de `<identityConfiguration>` autorização são configurados por meio de um elemento que é implicitamente ou explicitamente referenciado de `<federationConfiguration>` um elemento nesta seção.</span><span class="sxs-lookup"><span data-stu-id="1617e-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="1617e-121">Para obter mais informações, consulte os **comentários** no [ \<elemento federationConfiguration >](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="1617e-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="1617e-122">A `<system.identityModel.services>` seção é representada <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> pela classe.</span><span class="sxs-lookup"><span data-stu-id="1617e-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="1617e-123">A coleção de elementos `<federationConfiguration>` filho configurados na seção é representada <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> pela classe.</span><span class="sxs-lookup"><span data-stu-id="1617e-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1617e-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1617e-124">Example</span></span>  
 <span data-ttu-id="1617e-125">O XML a seguir mostra como adicionar uma `<system.identityModel.services>` seção a um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1617e-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="1617e-126">Você deve primeiro adicionar declarações de seção para a `<system.identityModel.services>` seção e as `<system.identityModel>` seções.</span><span class="sxs-lookup"><span data-stu-id="1617e-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="1617e-127">(Ao adicionar uma `<system.identityModel.services>` seção, você também deve adicionar uma declaração para a `<system.identityModel>` seção para garantir que uma seção padrão `<identityConfiguration>` possa ser criada pelo tempo de execução, se necessário.) Depois que as declarações de seção tiverem sido adicionadas, você poderá definir as configurações `<system.identityModel.services>` de autenticação federada no elemento.</span><span class="sxs-lookup"><span data-stu-id="1617e-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"   
        issuer="http://localhost:15839/wsFederationSTS/Issue"   
        realm="http://localhost:50969/" reply="http://localhost:50969/"   
        requireHttps="false"   
        signOutReply="http://localhost:50969/SignedOutPage.html"   
        signOutQueryString="Param1=value2&Param2=value2"   
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
