---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152561"
---
# \<securityTokenHandlerConfiguration>
<span data-ttu-id="4f288-101">Fornece a configuração para a coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="4f288-101">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="4f288-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f288-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f288-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f288-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4f288-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f288-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f288-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f288-105">Attributes</span></span>  
  
|<span data-ttu-id="4f288-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="4f288-106">Attribute</span></span>|<span data-ttu-id="4f288-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f288-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f288-108">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="4f288-108">saveBootstrapContext</span></span>|<span data-ttu-id="4f288-109">Especifica se os tokens de inicialização devem ser incluídos no token de sessão.</span><span class="sxs-lookup"><span data-stu-id="4f288-109">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="4f288-110">O valor também pode ser definido em uma coleção de manipuladores de token, definindo o `saveBootstrapContext` atributo no [\<identityConfiguration>](identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="4f288-110">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="4f288-111">Um valor definido na coleção de manipuladores de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="4f288-111">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="4f288-112">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="4f288-112">maximumClockSkew</span></span>|<span data-ttu-id="4f288-113">Um <xref:System.TimeSpan> valor que especifica a distorção máxima permitida do relógio.</span><span class="sxs-lookup"><span data-stu-id="4f288-113">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="4f288-114">Controla o máximo permitido de distorção de relógio ao executar operações sensíveis ao tempo, como validar o tempo de expiração de uma sessão de entrada.</span><span class="sxs-lookup"><span data-stu-id="4f288-114">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="4f288-115">O padrão é 5 minutos, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="4f288-115">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="4f288-116">Para obter mais informações sobre como especificar <xref:System.TimeSpan> valores, consulte [valores de TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f288-116">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="4f288-117">A distorção máxima do relógio também pode ser definida no nível de serviço definindo o `maximumClockSkew` atributo no [\<identityConfiguration>](identityconfiguration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="4f288-117">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="4f288-118">Um valor definido na coleção de manipuladores de token substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="4f288-118">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f288-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f288-119">Child Elements</span></span>  
  
|<span data-ttu-id="4f288-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f288-120">Element</span></span>|<span data-ttu-id="4f288-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f288-121">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="4f288-122">Especifica o conjunto de URIs que são identificadores aceitáveis dessa terceira parte confiável.</span><span class="sxs-lookup"><span data-stu-id="4f288-122">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="4f288-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f288-123">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="4f288-124">Registra os caches usados para tokens de sessão e detecção de reprodução de token.</span><span class="sxs-lookup"><span data-stu-id="4f288-124">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="4f288-125">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="4f288-125">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4f288-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f288-126">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="4f288-127">Controla as configurações que os manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="4f288-127">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="4f288-128">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="4f288-128">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4f288-129">Essas configurações serão substituídas se um manipulador específico estiver configurado com seu próprio validador.</span><span class="sxs-lookup"><span data-stu-id="4f288-129">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="4f288-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f288-130">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="4f288-131">Configura o registro de nome do emissor que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="4f288-131">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4f288-132">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f288-132">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="4f288-133">Registra o resolvedor de token do emissor que é usado por manipuladores na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="4f288-133">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4f288-134">O resolvedor de token do emissor é usado para resolver o token de assinatura em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="4f288-134">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="4f288-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f288-135">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="4f288-136">Registra o resolvedor de token de serviço que é usado pelos manipuladores na coleção de manipuladores de token.</span><span class="sxs-lookup"><span data-stu-id="4f288-136">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="4f288-137">O resolvedor de token de serviço é usado para resolver o token de criptografia em mensagens e tokens de entrada.</span><span class="sxs-lookup"><span data-stu-id="4f288-137">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="4f288-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f288-138">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="4f288-139">Habilita a detecção de reprodução de token e especifica o tempo de expiração para tokens.</span><span class="sxs-lookup"><span data-stu-id="4f288-139">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="4f288-140">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="4f288-140">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="4f288-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f288-141">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f288-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f288-142">Parent Elements</span></span>  
  
|<span data-ttu-id="4f288-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f288-143">Element</span></span>|<span data-ttu-id="4f288-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f288-144">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="4f288-145">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4f288-145">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f288-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f288-146">Remarks</span></span>  
 <span data-ttu-id="4f288-147">Esta seção fornece valores de propriedade para um <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objeto.</span><span class="sxs-lookup"><span data-stu-id="4f288-147">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="4f288-148">As configurações definidas nesta seção substituem aquelas configuradas no serviço.</span><span class="sxs-lookup"><span data-stu-id="4f288-148">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="4f288-149">Por sua vez, algumas dessas configurações podem ser substituídas pelas configurações que são especificadas quando um manipulador é adicionado à coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="4f288-149">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f288-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f288-150">Example</span></span>  
  
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
