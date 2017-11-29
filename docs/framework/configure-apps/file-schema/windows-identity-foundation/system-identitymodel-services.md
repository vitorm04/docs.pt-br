---
title: '&lt;System&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a5f0b6b207fbd51504149fd5c245f41ef89f17f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemidentitymodelservicesgt"></a><span data-ttu-id="708aa-102">&lt;System&gt;</span><span class="sxs-lookup"><span data-stu-id="708aa-102">&lt;system.identityModel.services&gt;</span></span>
<span data-ttu-id="708aa-103">Seção de configuração para a autenticação usando o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="708aa-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="708aa-104">\<System ></span><span class="sxs-lookup"><span data-stu-id="708aa-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="708aa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="708aa-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="708aa-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="708aa-106">Attributes and Elements</span></span>  
 <span data-ttu-id="708aa-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="708aa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="708aa-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="708aa-108">Attributes</span></span>  
 <span data-ttu-id="708aa-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="708aa-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="708aa-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="708aa-110">Child Elements</span></span>  
  
|<span data-ttu-id="708aa-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="708aa-111">Element</span></span>|<span data-ttu-id="708aa-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="708aa-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="708aa-113">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="708aa-113">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="708aa-114">Contém as configurações que definir o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> módulos HTTP (SAM).</span><span class="sxs-lookup"><span data-stu-id="708aa-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="708aa-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="708aa-115">Parent Elements</span></span>  
 <span data-ttu-id="708aa-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="708aa-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="708aa-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="708aa-117">Remarks</span></span>  
 <span data-ttu-id="708aa-118">Adicionar um `<system.identityModel.services>` seção ao arquivo de configuração do aplicativo para fornecer configurações para o SAM e WSFAM.</span><span class="sxs-lookup"><span data-stu-id="708aa-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="708aa-119">Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, o Gerenciador de autorização de declarações (<xref:System.Security.Claims.ClaimsAuthorizationManager>) e a política que é usada para tomar decisões de autorização são configurados por meio de um `<identityConfiguration>` elemento que é implicitamente ou explicitamente referenciado em um `<federationConfiguration>` elemento nesta seção.</span><span class="sxs-lookup"><span data-stu-id="708aa-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="708aa-120">Para obter mais informações, consulte o **comentários** sob o [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="708aa-120">For more information, see the **Remarks** under the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="708aa-121">O `<system.identityModel.services>` seção é representada pela <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe.</span><span class="sxs-lookup"><span data-stu-id="708aa-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="708aa-122">A coleção de filhos `<federationConfiguration>` configurados na seção de elementos é representado pela <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="708aa-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="708aa-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="708aa-123">Example</span></span>  
 <span data-ttu-id="708aa-124">O XML a seguir mostra como adicionar um `<system.identityModel.services>` seção para um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="708aa-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="708aa-125">Você deve primeiro adicionar declarações de seção para ambos os `<system.identityModel.services>` seção e o `<system.identityModel>` seções.</span><span class="sxs-lookup"><span data-stu-id="708aa-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="708aa-126">(Quando você adiciona um `<system.identityModel.services>` seção, você deve adicionar uma declaração para o `<system.identityModel>` seção para garantir que um padrão `<identityConfiguration>` seção pode ser criada pelo tempo de execução, se necessário.) Depois que as declarações de seção forem adicionadas, você pode definir configurações de autenticação federada sob o `<system.identityModel.services>` elemento.</span><span class="sxs-lookup"><span data-stu-id="708aa-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
