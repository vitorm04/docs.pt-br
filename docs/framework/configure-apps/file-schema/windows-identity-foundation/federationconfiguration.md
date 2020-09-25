---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 39e96a161a2e75d5f00b73f6b08b1e4a0c109aee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201350"
---
# \<federationConfiguration>

<span data-ttu-id="80830-101">Configura o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) ao usar a autenticação federada por meio do protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="80830-101">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="80830-102">Configura o <xref:System.Security.Claims.ClaimsAuthorizationManager> ao usar a <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou para fornecer controle de acesso baseado em declarações.</span><span class="sxs-lookup"><span data-stu-id="80830-102">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="80830-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80830-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80830-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="80830-104">Attributes and Elements</span></span>  

 <span data-ttu-id="80830-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="80830-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80830-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="80830-106">Attributes</span></span>  
  
|<span data-ttu-id="80830-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="80830-107">Attribute</span></span>|<span data-ttu-id="80830-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="80830-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80830-109">name</span><span class="sxs-lookup"><span data-stu-id="80830-109">name</span></span>|<span data-ttu-id="80830-110">O nome deste elemento de configuração da Federação.</span><span class="sxs-lookup"><span data-stu-id="80830-110">The name of this federation configuration element.</span></span> <span data-ttu-id="80830-111">Esse atributo fornece principalmente um ponto de extensibilidade para protocolos futuros.</span><span class="sxs-lookup"><span data-stu-id="80830-111">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="80830-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="80830-112">Optional.</span></span>|  
|<span data-ttu-id="80830-113">identityConfigurationName</span><span class="sxs-lookup"><span data-stu-id="80830-113">identityConfigurationName</span></span>|<span data-ttu-id="80830-114">O nome da seção de configuração de identidade, conforme especificado em um [\<identityConfiguration>](identityconfiguration.md) elemento a ser usado.</span><span class="sxs-lookup"><span data-stu-id="80830-114">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="80830-115">Se esse atributo não for especificado, a seção de configuração de identidade padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="80830-115">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="80830-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="80830-116">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80830-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="80830-117">Child Elements</span></span>  
  
|<span data-ttu-id="80830-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="80830-118">Element</span></span>|<span data-ttu-id="80830-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="80830-119">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="80830-120">Configura o manipulador de cookies usado pelo SAM.</span><span class="sxs-lookup"><span data-stu-id="80830-120">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="80830-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="80830-121">Optional.</span></span>|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="80830-122">Configura o certificado que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="80830-122">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="80830-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="80830-123">Optional.</span></span>|  
|[\<wsFederation>](wsfederation.md)|<span data-ttu-id="80830-124">Configura o módulo de autenticação do WS-Federation (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="80830-124">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="80830-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="80830-125">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80830-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="80830-126">Parent Elements</span></span>  
  
|<span data-ttu-id="80830-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="80830-127">Element</span></span>|<span data-ttu-id="80830-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="80830-128">Description</span></span>|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|<span data-ttu-id="80830-129">A seção de configuração para autenticação usando o protocolo WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="80830-129">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80830-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="80830-130">Remarks</span></span>  

 <span data-ttu-id="80830-131">O \<federationConfiguration> elemento fornece configurações em dois cenários diferentes:</span><span class="sxs-lookup"><span data-stu-id="80830-131">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="80830-132">Ao usar o WS-Federation em um aplicativo Web passivo, o elemento contém configurações que definem o <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) e o <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="80830-132">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="80830-133">Ele também faz referência à configuração de identidade a ser usada para configurar manipuladores de token de segurança e certificados, além de componentes como o Gerenciador de autorização de declarações e o Gerenciador de autenticação de declarações.</span><span class="sxs-lookup"><span data-stu-id="80830-133">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="80830-134">Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou a <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, o elemento faz referência à configuração de identidade que configura o Gerenciador de autorização de declarações e a política que é usada para tomar decisões de autorização.</span><span class="sxs-lookup"><span data-stu-id="80830-134">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="80830-135">Isso é verdade, mesmo em cenários que não são cenários da Web passivos; por exemplo, aplicativos Windows Communication Foundation (WCF) ou um aplicativo que não é baseado na Web.</span><span class="sxs-lookup"><span data-stu-id="80830-135">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="80830-136">Se o aplicativo não for um aplicativo Web passivo, o [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) elemento (e seus elementos filho de política, se presente) da configuração de identidade referenciada pelo `<federationConfiguration>` elemento serão as únicas configurações aplicadas.</span><span class="sxs-lookup"><span data-stu-id="80830-136">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="80830-137">Todos os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="80830-137">All others are ignored.</span></span>  
  
 <span data-ttu-id="80830-138">Independentemente do cenário, o tempo de execução carrega a configuração de Federação padrão.</span><span class="sxs-lookup"><span data-stu-id="80830-138">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="80830-139">O comportamento é definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="80830-139">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="80830-140">Se não houver nenhum `<federationConfiguration>` elemento presente, o tempo de execução criará uma configuração de Federação e a preencherá com valores padrão.</span><span class="sxs-lookup"><span data-stu-id="80830-140">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="80830-141">Essa configuração de Federação padrão fará referência à configuração de identidade padrão.</span><span class="sxs-lookup"><span data-stu-id="80830-141">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="80830-142">Se um único `<federationConfiguration>` elemento estiver presente, será a configuração de Federação padrão, independentemente de ter sido nomeada ou não nomeada.</span><span class="sxs-lookup"><span data-stu-id="80830-142">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="80830-143">Se seu `identityConfiguration` atributo for especificado, a configuração de identidade nomeada será referenciada; caso contrário, a configuração de identidade padrão será referenciada.</span><span class="sxs-lookup"><span data-stu-id="80830-143">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="80830-144">Se um elemento sem nome `<federationConfiguration>` estiver presente, será a configuração de Federação padrão.</span><span class="sxs-lookup"><span data-stu-id="80830-144">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="80830-145">Se seu `identityConfiguration` atributo for especificado, a configuração de identidade nomeada será referenciada; caso contrário, a configuração de identidade padrão será referenciada.</span><span class="sxs-lookup"><span data-stu-id="80830-145">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="80830-146">Se vários elementos nomeados `<federationConfiguration>` estiverem presentes e nenhum elemento sem nome `<federationConfiguration>` estiver presente, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="80830-146">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="80830-147">Normalmente, apenas uma única `<federationConfiguration>` seção é definida.</span><span class="sxs-lookup"><span data-stu-id="80830-147">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="80830-148">Esta seção é a configuração de Federação padrão.</span><span class="sxs-lookup"><span data-stu-id="80830-148">This section is the default federation configuration.</span></span> <span data-ttu-id="80830-149">Você pode especificar vários elementos nomeados com exclusividade `<federationConfiguration>` ; no entanto, nesse caso, se quiser carregar uma configuração de Federação diferente da que não foi nomeada, você deverá fornecer um manipulador para o.</span><span class="sxs-lookup"><span data-stu-id="80830-149">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="80830-150"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> e defina a <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> propriedade dentro do manipulador para um <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objeto inicializado com valores do elemento apropriado `<federationConfiguration>` no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="80830-150"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="80830-151">O `<federationConfiguration>` elemento é representado pela <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> classe.</span><span class="sxs-lookup"><span data-stu-id="80830-151">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="80830-152">O próprio objeto de configuração é representado pela <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> classe.</span><span class="sxs-lookup"><span data-stu-id="80830-152">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="80830-153">Uma única <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instância é definida na <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriedade e fornece configuração federada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="80830-153">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80830-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80830-154">Example</span></span>  

 <span data-ttu-id="80830-155">O XML a seguir mostra um `<federationConfiguration>` elemento que especifica as configurações para o WSFAM e especifica que o manipulador de cookie padrão (uma instância da <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe) seja usado pelo Sam.</span><span class="sxs-lookup"><span data-stu-id="80830-155">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="80830-156">Neste exemplo, nem o manipulador de cookie nem WSFAM são necessários para usar HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80830-156">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="80830-157">Isso ocorre porque o `requireHttps` atributo no `<wsFederation>` elemento e o `requireSsl` atributo no `<cookieHandlerElement>` são `false` .</span><span class="sxs-lookup"><span data-stu-id="80830-157">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="80830-158">Essas configurações não são recomendadas para a maioria dos ambientes de produção, pois podem representar um risco de segurança.</span><span class="sxs-lookup"><span data-stu-id="80830-158">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
```xml  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="80830-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="80830-159">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)
