---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152498"
---
# \<system.identityModel.services>
<span data-ttu-id="3e8de-102">A seção de configuração para autenticação usando o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="3e8de-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="3e8de-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e8de-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e8de-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e8de-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3e8de-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e8de-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e8de-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e8de-106">Attributes</span></span>  
 <span data-ttu-id="3e8de-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e8de-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e8de-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e8de-108">Child Elements</span></span>  
  
|<span data-ttu-id="3e8de-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e8de-109">Element</span></span>|<span data-ttu-id="3e8de-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e8de-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="3e8de-111">Contém as configurações que definem os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> módulos http (WSFAM) e <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="3e8de-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e8de-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e8de-112">Parent Elements</span></span>  
 <span data-ttu-id="3e8de-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e8de-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e8de-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e8de-114">Remarks</span></span>  
 <span data-ttu-id="3e8de-115">Adicione uma `<system.identityModel.services>` seção ao arquivo de configuração do aplicativo para fornecer as configurações para o Sam e o WSFAM.</span><span class="sxs-lookup"><span data-stu-id="3e8de-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3e8de-116">Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, o Gerenciador de autorização de declarações ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) e a política usada para tomar decisões de autorização são configurados por meio de um `<identityConfiguration>` elemento que é implicitamente ou explicitamente referenciado de um `<federationConfiguration>` elemento nesta seção.</span><span class="sxs-lookup"><span data-stu-id="3e8de-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="3e8de-117">Para obter mais informações, consulte os **comentários** sob o [\<federationConfiguration>](federationconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="3e8de-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="3e8de-118">A `<system.identityModel.services>` seção é representada pela <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe.</span><span class="sxs-lookup"><span data-stu-id="3e8de-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="3e8de-119">A coleção de `<federationConfiguration>` elementos filho configurados na seção é representada pela <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="3e8de-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e8de-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e8de-120">Example</span></span>  
 <span data-ttu-id="3e8de-121">O XML a seguir mostra como adicionar uma `<system.identityModel.services>` seção a um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3e8de-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="3e8de-122">Você deve primeiro adicionar declarações de seção para a `<system.identityModel.services>` seção e as `<system.identityModel>` seções.</span><span class="sxs-lookup"><span data-stu-id="3e8de-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="3e8de-123">(Ao adicionar uma `<system.identityModel.services>` seção, você também deve adicionar uma declaração para a `<system.identityModel>` seção para garantir que uma seção padrão `<identityConfiguration>` possa ser criada pelo tempo de execução, se necessário.) Depois que as declarações de seção tiverem sido adicionadas, você poderá definir as configurações de autenticação federada no `<system.identityModel.services>` elemento.</span><span class="sxs-lookup"><span data-stu-id="3e8de-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
