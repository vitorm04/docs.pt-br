---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 0aefaa808dfc32085a208420fcd582b1671acc64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942454"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="b115c-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="b115c-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="b115c-102">Fornece a configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="b115c-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="b115c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b115c-103">\<system.identityModel></span></span>  
<span data-ttu-id="b115c-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b115c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="b115c-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="b115c-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b115c-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="b115c-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b115c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b115c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b115c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b115c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b115c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b115c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b115c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b115c-110">Attributes</span></span>  
  
|<span data-ttu-id="b115c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b115c-111">Attribute</span></span>|<span data-ttu-id="b115c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b115c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b115c-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="b115c-113">saveBootstrapContext</span></span>|<span data-ttu-id="b115c-114">Especifica se os tokens de inicialização devem ser incluídos no token de sessão.</span><span class="sxs-lookup"><span data-stu-id="b115c-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="b115c-115">O valor também pode ser definido em uma coleção de manipuladores de token `saveBootstrapContext` , definindo o atributo [ \<no elemento identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="b115c-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="b115c-116">Um valor definido na coleção de manipuladores de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="b115c-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="b115c-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="b115c-117">maximumClockSkew</span></span>|<span data-ttu-id="b115c-118">Um <xref:System.TimeSpan> valor que especifica a distorção máxima permitida do relógio.</span><span class="sxs-lookup"><span data-stu-id="b115c-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="b115c-119">Controla o máximo permitido de distorção de relógio ao executar operações sensíveis ao tempo, como validar o tempo de expiração de uma sessão de entrada.</span><span class="sxs-lookup"><span data-stu-id="b115c-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="b115c-120">O padrão é 5 minutos, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="b115c-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="b115c-121">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [valores de TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="b115c-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="b115c-122">A distorção máxima do relógio também pode ser definida no nível de serviço definindo `maximumClockSkew` o atributo [ \<no elemento identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="b115c-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="b115c-123">Um valor definido na coleção de manipuladores de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="b115c-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b115c-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b115c-124">Child Elements</span></span>  
  
|<span data-ttu-id="b115c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b115c-125">Element</span></span>|<span data-ttu-id="b115c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b115c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b115c-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="b115c-127">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="b115c-128">Especifica o conjunto de URIs que são identificadores aceitáveis dessa terceira parte confiável.</span><span class="sxs-lookup"><span data-stu-id="b115c-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="b115c-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b115c-129">Optional.</span></span>|  
|[<span data-ttu-id="b115c-130">\<caches></span><span class="sxs-lookup"><span data-stu-id="b115c-130">\<caches></span></span>](caches.md)|<span data-ttu-id="b115c-131">Registra os caches usados para tokens de sessão e detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="b115c-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="b115c-132">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b115c-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="b115c-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b115c-133">Optional.</span></span>|  
|[<span data-ttu-id="b115c-134">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="b115c-134">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="b115c-135">Controla as configurações que os manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="b115c-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="b115c-136">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b115c-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="b115c-137">Essas configurações serão substituídas se um manipulador específico estiver configurado com seu próprio validador.</span><span class="sxs-lookup"><span data-stu-id="b115c-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="b115c-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b115c-138">Optional.</span></span>|  
|[<span data-ttu-id="b115c-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="b115c-139">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="b115c-140">Configura o registro de nome do emissor que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="b115c-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="b115c-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b115c-141">Optional.</span></span>|  
|[<span data-ttu-id="b115c-142">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="b115c-142">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="b115c-143">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="b115c-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="b115c-144">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="b115c-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="b115c-145">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b115c-145">Optional.</span></span>|  
|[<span data-ttu-id="b115c-146">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="b115c-146">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="b115c-147">Registra o resolvedor de token de serviço que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="b115c-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="b115c-148">O resolvedor de token de serviço é usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="b115c-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="b115c-149">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b115c-149">Optional.</span></span>|  
|[<span data-ttu-id="b115c-150">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="b115c-150">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="b115c-151">Habilita a detecção de reprodução de token e especifica o tempo de expiração para tokens.</span><span class="sxs-lookup"><span data-stu-id="b115c-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="b115c-152">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b115c-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="b115c-153">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b115c-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b115c-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b115c-154">Parent Elements</span></span>  
  
|<span data-ttu-id="b115c-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="b115c-155">Element</span></span>|<span data-ttu-id="b115c-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="b115c-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b115c-157">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="b115c-157">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="b115c-158">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b115c-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b115c-159">Comentários</span><span class="sxs-lookup"><span data-stu-id="b115c-159">Remarks</span></span>  
 <span data-ttu-id="b115c-160">Esta seção fornece valores de propriedade para <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> um objeto.</span><span class="sxs-lookup"><span data-stu-id="b115c-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="b115c-161">As configurações definidas nesta seção substituem aquelas configuradas no serviço.</span><span class="sxs-lookup"><span data-stu-id="b115c-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="b115c-162">Por sua vez, algumas dessas configurações podem ser substituídas pelas configurações que são especificadas quando um manipulador é adicionado à coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b115c-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b115c-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b115c-163">Example</span></span>  
  
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
