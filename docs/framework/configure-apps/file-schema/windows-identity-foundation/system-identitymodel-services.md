---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e909756a58d5008d917fca84af0e478fc4878d2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156804"
---
# \<system.identityModel.services>

<span data-ttu-id="fbbe6-102">A seção de configuração para autenticação usando o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="fbbe6-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="fbbe6-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbbe6-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fbbe6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fbbe6-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbbe6-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="fbbe6-106">Attributes</span></span>  

 <span data-ttu-id="fbbe6-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="fbbe6-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbbe6-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fbbe6-108">Child Elements</span></span>  
  
|<span data-ttu-id="fbbe6-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="fbbe6-109">Element</span></span>|<span data-ttu-id="fbbe6-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbbe6-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="fbbe6-111">Contém as configurações que definem os <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> módulos http (WSFAM) e <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="fbbe6-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbbe6-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fbbe6-112">Parent Elements</span></span>  

 <span data-ttu-id="fbbe6-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="fbbe6-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbbe6-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbbe6-114">Remarks</span></span>  

 <span data-ttu-id="fbbe6-115">Adicione uma `<system.identityModel.services>` seção ao arquivo de configuração do aplicativo para fornecer as configurações para o Sam e o WSFAM.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fbbe6-116">Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, o Gerenciador de autorização de declarações ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) e a política usada para tomar decisões de autorização são configurados por meio de um `<identityConfiguration>` elemento que é implicitamente ou explicitamente referenciado de um `<federationConfiguration>` elemento nesta seção.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="fbbe6-117">Para obter mais informações, consulte os **comentários** sob o [\<federationConfiguration>](federationconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="fbbe6-118">A `<system.identityModel.services>` seção é representada pela <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="fbbe6-119">A coleção de `<federationConfiguration>` elementos filho configurados na seção é representada pela <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbbe6-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fbbe6-120">Example</span></span>  

 <span data-ttu-id="fbbe6-121">O XML a seguir mostra como adicionar uma `<system.identityModel.services>` seção a um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="fbbe6-122">Você deve primeiro adicionar declarações de seção para a `<system.identityModel.services>` seção e as `<system.identityModel>` seções.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="fbbe6-123">(Ao adicionar uma `<system.identityModel.services>` seção, você também deve adicionar uma declaração para a `<system.identityModel>` seção para garantir que uma seção padrão `<identityConfiguration>` possa ser criada pelo tempo de execução, se necessário.) Depois que as declarações de seção tiverem sido adicionadas, você poderá definir as configurações de autenticação federada no `<system.identityModel.services>` elemento.</span><span class="sxs-lookup"><span data-stu-id="fbbe6-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
