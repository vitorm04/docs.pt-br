---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 168bdc4fbf640b201ebc61462d04727c23f838f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="39ab4-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="39ab4-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="39ab4-103">Fornece configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="39ab4-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="39ab4-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="39ab4-104">\<system.identityModel></span></span>  
<span data-ttu-id="39ab4-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="39ab4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="39ab4-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="39ab4-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="39ab4-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="39ab4-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39ab4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39ab4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39ab4-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39ab4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="39ab4-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="39ab4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39ab4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="39ab4-111">Attributes</span></span>  
  
|<span data-ttu-id="39ab4-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="39ab4-112">Attribute</span></span>|<span data-ttu-id="39ab4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="39ab4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39ab4-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="39ab4-114">saveBootstrapContext</span></span>|<span data-ttu-id="39ab4-115">Especifica se os tokens de inicialização devem ser incluídos no token de sessão.</span><span class="sxs-lookup"><span data-stu-id="39ab4-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="39ab4-116">O valor também pode ser definido em uma coleção de manipulador de token, definindo o `saveBootstrapContext` atributo no [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="39ab4-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="39ab4-117">Um valor definido na coleção de manipulador de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="39ab4-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="39ab4-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="39ab4-118">maximumClockSkew</span></span>|<span data-ttu-id="39ab4-119">Um <xref:System.TimeSpan> que especifica a distorção máxima permitida do relógio.</span><span class="sxs-lookup"><span data-stu-id="39ab4-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="39ab4-120">Controla a distorção máxima permitida do relógio ao executar operações de detecção de hora, como validar o tempo de expiração de uma sessão de logon.</span><span class="sxs-lookup"><span data-stu-id="39ab4-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="39ab4-121">O padrão é 5 minutos, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="39ab4-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="39ab4-122">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [Timespan valores](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="39ab4-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="39ab4-123">O máximo do relógio também pode ser definido no nível de serviço, definindo o `maximumClockSkew` atributo no [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="39ab4-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="39ab4-124">Um valor definido na coleção de manipulador de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="39ab4-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39ab4-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39ab4-125">Child Elements</span></span>  
  
|<span data-ttu-id="39ab4-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="39ab4-126">Element</span></span>|<span data-ttu-id="39ab4-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="39ab4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39ab4-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="39ab4-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="39ab4-129">Especifica o conjunto de URIs que são aceitáveis identificadores da terceira parte confiável.</span><span class="sxs-lookup"><span data-stu-id="39ab4-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="39ab4-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39ab4-130">Optional.</span></span>|  
|[<span data-ttu-id="39ab4-131">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="39ab4-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="39ab4-132">Registra os caches usados para detecção de reprodução de token e tokens de sessão.</span><span class="sxs-lookup"><span data-stu-id="39ab4-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="39ab4-133">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="39ab4-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="39ab4-134">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39ab4-134">Optional.</span></span>|  
|[<span data-ttu-id="39ab4-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="39ab4-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="39ab4-136">Controla as configurações que manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="39ab4-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="39ab4-137">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="39ab4-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="39ab4-138">Essas configurações são substituídas se um manipulador específico é configurado com seu próprio validados.</span><span class="sxs-lookup"><span data-stu-id="39ab4-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="39ab4-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39ab4-139">Optional.</span></span>|  
|[<span data-ttu-id="39ab4-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="39ab4-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="39ab4-141">Configura o registro de nome de emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="39ab4-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="39ab4-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39ab4-142">Optional.</span></span>|  
|[<span data-ttu-id="39ab4-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="39ab4-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="39ab4-144">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="39ab4-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="39ab4-145">O resolvedor de token do emissor é usado para resolver o token de assinatura em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="39ab4-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="39ab4-146">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39ab4-146">Optional.</span></span>|  
|[<span data-ttu-id="39ab4-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="39ab4-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="39ab4-148">Registra o resolvedor de token de serviço que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="39ab4-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="39ab4-149">O resolvedor de token de serviço é usado para resolver o token de criptografia em tokens de entrada e de mensagens.</span><span class="sxs-lookup"><span data-stu-id="39ab4-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="39ab4-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39ab4-150">Optional.</span></span>|  
|[<span data-ttu-id="39ab4-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="39ab4-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="39ab4-152">Habilita a detecção de reprodução de token e especifica a hora de expiração de tokens.</span><span class="sxs-lookup"><span data-stu-id="39ab4-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="39ab4-153">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="39ab4-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="39ab4-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39ab4-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39ab4-155">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39ab4-155">Parent Elements</span></span>  
  
|<span data-ttu-id="39ab4-156">Elemento</span><span class="sxs-lookup"><span data-stu-id="39ab4-156">Element</span></span>|<span data-ttu-id="39ab4-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="39ab4-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39ab4-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="39ab4-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="39ab4-159">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="39ab4-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39ab4-160">Comentários</span><span class="sxs-lookup"><span data-stu-id="39ab4-160">Remarks</span></span>  
 <span data-ttu-id="39ab4-161">Esta seção fornece valores de propriedade para um <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objeto.</span><span class="sxs-lookup"><span data-stu-id="39ab4-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="39ab4-162">As configurações definidas nesta seção substituem aquelas configuradas no serviço.</span><span class="sxs-lookup"><span data-stu-id="39ab4-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="39ab4-163">Algumas dessas configurações, por sua vez, podem ser substituídas pelas configurações que são especificadas quando um manipulador é adicionado à coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="39ab4-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39ab4-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39ab4-164">Example</span></span>  
  
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
