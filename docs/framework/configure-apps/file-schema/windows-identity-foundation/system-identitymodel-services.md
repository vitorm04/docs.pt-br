---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152498"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="e7d18-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="e7d18-102">\<system.identityModel.services></span></span>
<span data-ttu-id="e7d18-103">Seção de configuração para autenticação usando o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="e7d18-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="e7d18-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7d18-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e7d18-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span><span class="sxs-lookup"><span data-stu-id="e7d18-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d18-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7d18-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7d18-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e7d18-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e7d18-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e7d18-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7d18-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e7d18-109">Attributes</span></span>  
 <span data-ttu-id="e7d18-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e7d18-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7d18-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e7d18-111">Child Elements</span></span>  
  
|<span data-ttu-id="e7d18-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e7d18-112">Element</span></span>|<span data-ttu-id="e7d18-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7d18-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7d18-114">\<federaçãoconfiguração></span><span class="sxs-lookup"><span data-stu-id="e7d18-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="e7d18-115">Contém as configurações que <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> configuram os módulos <xref:System.IdentityModel.Services.SessionAuthenticationModule> HTTP (WSFAM) e (SAM).</span><span class="sxs-lookup"><span data-stu-id="e7d18-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7d18-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e7d18-116">Parent Elements</span></span>  
 <span data-ttu-id="e7d18-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e7d18-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7d18-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7d18-118">Remarks</span></span>  
 <span data-ttu-id="e7d18-119">Adicione `<system.identityModel.services>` uma seção ao arquivo de configuração do aplicativo para fornecer configurações para o SAM e o WSFAM.</span><span class="sxs-lookup"><span data-stu-id="e7d18-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e7d18-120">Ao usar <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou a classe para fornecer controle de<xref:System.Security.Claims.ClaimsAuthorizationManager>acesso baseado em sinistros em seu código, `<identityConfiguration>` o gerenciador de autorização de sinistros ( ) e a política que é usada para tomar decisões de autorização são configurados através de um elemento que é implicitamente ou explicitamente referenciado a partir de um `<federationConfiguration>` elemento nesta seção.</span><span class="sxs-lookup"><span data-stu-id="e7d18-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="e7d18-121">Para obter mais informações, consulte as **Observações** o elemento [ \<>de configuração da federação.](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e7d18-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="e7d18-122">A `<system.identityModel.services>` seção é <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> representada pela classe.</span><span class="sxs-lookup"><span data-stu-id="e7d18-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="e7d18-123">A coleção `<federationConfiguration>` de elementos infantis configurados <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> na seção é representada pela classe.</span><span class="sxs-lookup"><span data-stu-id="e7d18-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7d18-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7d18-124">Example</span></span>  
 <span data-ttu-id="e7d18-125">O XML a seguir `<system.identityModel.services>` mostra como adicionar uma seção a um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e7d18-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="e7d18-126">Você deve primeiro adicionar declarações `<system.identityModel.services>` de `<system.identityModel>` seção para a seção e as seções.</span><span class="sxs-lookup"><span data-stu-id="e7d18-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="e7d18-127">(Quando você `<system.identityModel.services>` adiciona uma seção, você `<system.identityModel>` também deve adicionar `<identityConfiguration>` uma declaração para a seção para garantir que uma seção padrão possa ser criada pelo tempo de execução, se necessário.) Depois que as declarações de seção foram adicionadas, você `<system.identityModel.services>` pode configurar configurações de autenticação federada o elemento.</span><span class="sxs-lookup"><span data-stu-id="e7d18-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
