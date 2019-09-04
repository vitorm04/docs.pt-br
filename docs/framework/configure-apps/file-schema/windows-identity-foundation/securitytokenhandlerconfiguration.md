---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 330e52bd73a8032e4073fe434c852e5bdf8e1d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251884"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="ddc93-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="ddc93-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="ddc93-102">Fornece a configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="ddc93-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="ddc93-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ddc93-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ddc93-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ddc93-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ddc93-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ddc93-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ddc93-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="ddc93-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="ddc93-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> securityTokenHandlerConfiguration**</span><span class="sxs-lookup"><span data-stu-id="ddc93-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddc93-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ddc93-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddc93-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ddc93-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ddc93-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ddc93-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddc93-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ddc93-111">Attributes</span></span>  
  
|<span data-ttu-id="ddc93-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="ddc93-112">Attribute</span></span>|<span data-ttu-id="ddc93-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddc93-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ddc93-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="ddc93-114">saveBootstrapContext</span></span>|<span data-ttu-id="ddc93-115">Especifica se os tokens de inicialização devem ser incluídos no token de sessão.</span><span class="sxs-lookup"><span data-stu-id="ddc93-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="ddc93-116">O valor também pode ser definido em uma coleção de manipuladores de token `saveBootstrapContext` , definindo o atributo [ \<no elemento identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="ddc93-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="ddc93-117">Um valor definido na coleção de manipuladores de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="ddc93-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="ddc93-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="ddc93-118">maximumClockSkew</span></span>|<span data-ttu-id="ddc93-119">Um <xref:System.TimeSpan> valor que especifica a distorção máxima permitida do relógio.</span><span class="sxs-lookup"><span data-stu-id="ddc93-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="ddc93-120">Controla o máximo permitido de distorção de relógio ao executar operações sensíveis ao tempo, como validar o tempo de expiração de uma sessão de entrada.</span><span class="sxs-lookup"><span data-stu-id="ddc93-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="ddc93-121">O padrão é 5 minutos, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="ddc93-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="ddc93-122">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [valores de TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="ddc93-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="ddc93-123">A distorção máxima do relógio também pode ser definida no nível de serviço definindo `maximumClockSkew` o atributo [ \<no elemento identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="ddc93-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="ddc93-124">Um valor definido na coleção de manipuladores de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="ddc93-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddc93-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ddc93-125">Child Elements</span></span>  
  
|<span data-ttu-id="ddc93-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="ddc93-126">Element</span></span>|<span data-ttu-id="ddc93-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddc93-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddc93-128">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="ddc93-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="ddc93-129">Especifica o conjunto de URIs que são identificadores aceitáveis dessa terceira parte confiável.</span><span class="sxs-lookup"><span data-stu-id="ddc93-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="ddc93-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ddc93-130">Optional.</span></span>|  
|[<span data-ttu-id="ddc93-131">\<caches></span><span class="sxs-lookup"><span data-stu-id="ddc93-131">\<caches></span></span>](caches.md)|<span data-ttu-id="ddc93-132">Registra os caches usados para tokens de sessão e detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="ddc93-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="ddc93-133">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ddc93-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ddc93-134">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ddc93-134">Optional.</span></span>|  
|[<span data-ttu-id="ddc93-135">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="ddc93-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="ddc93-136">Controla as configurações que os manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="ddc93-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="ddc93-137">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ddc93-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ddc93-138">Essas configurações serão substituídas se um manipulador específico estiver configurado com seu próprio validador.</span><span class="sxs-lookup"><span data-stu-id="ddc93-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="ddc93-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ddc93-139">Optional.</span></span>|  
|[<span data-ttu-id="ddc93-140">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="ddc93-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="ddc93-141">Configura o registro de nome do emissor que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="ddc93-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ddc93-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ddc93-142">Optional.</span></span>|  
|[<span data-ttu-id="ddc93-143">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="ddc93-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="ddc93-144">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="ddc93-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ddc93-145">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="ddc93-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="ddc93-146">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ddc93-146">Optional.</span></span>|  
|[<span data-ttu-id="ddc93-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="ddc93-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="ddc93-148">Registra o resolvedor de token de serviço que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="ddc93-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="ddc93-149">O resolvedor de token de serviço é usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="ddc93-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="ddc93-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ddc93-150">Optional.</span></span>|  
|[<span data-ttu-id="ddc93-151">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="ddc93-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="ddc93-152">Habilita a detecção de reprodução de token e especifica o tempo de expiração para tokens.</span><span class="sxs-lookup"><span data-stu-id="ddc93-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="ddc93-153">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ddc93-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="ddc93-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ddc93-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddc93-155">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ddc93-155">Parent Elements</span></span>  
  
|<span data-ttu-id="ddc93-156">Elemento</span><span class="sxs-lookup"><span data-stu-id="ddc93-156">Element</span></span>|<span data-ttu-id="ddc93-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddc93-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddc93-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ddc93-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="ddc93-159">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ddc93-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddc93-160">Comentários</span><span class="sxs-lookup"><span data-stu-id="ddc93-160">Remarks</span></span>  
 <span data-ttu-id="ddc93-161">Esta seção fornece valores de propriedade para <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> um objeto.</span><span class="sxs-lookup"><span data-stu-id="ddc93-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="ddc93-162">As configurações definidas nesta seção substituem aquelas configuradas no serviço.</span><span class="sxs-lookup"><span data-stu-id="ddc93-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="ddc93-163">Por sua vez, algumas dessas configurações podem ser substituídas pelas configurações que são especificadas quando um manipulador é adicionado à coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ddc93-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddc93-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ddc93-164">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
