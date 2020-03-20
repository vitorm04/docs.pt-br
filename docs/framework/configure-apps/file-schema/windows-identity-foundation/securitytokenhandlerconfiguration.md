---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152561"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="d3d3c-101">\<> de configuração dedecontatosdeproblemas de segurança</span><span class="sxs-lookup"><span data-stu-id="d3d3c-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="d3d3c-102">Fornece configuração para a coleção de manipuladores de tokens.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="d3d3c-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3d3c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3d3c-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d3d3c-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d3d3c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d3d3c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d3d3c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="d3d3c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="d3d3c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<Configuradodefalha>**</span><span class="sxs-lookup"><span data-stu-id="d3d3c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d3c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3d3c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3d3c-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d3d3c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d3d3c-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3d3c-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d3d3c-111">Attributes</span></span>  
  
|<span data-ttu-id="d3d3c-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="d3d3c-112">Attribute</span></span>|<span data-ttu-id="d3d3c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3d3c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3d3c-114">salvarBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="d3d3c-114">saveBootstrapContext</span></span>|<span data-ttu-id="d3d3c-115">Especifica se os tokens bootstrap devem ser incluídos no token da sessão.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="d3d3c-116">O valor também pode ser definido em uma `saveBootstrapContext` coleção de manipuladores de tokens definindo o atributo no elemento [ \<identityConfiguration>.](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d3d3c-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="d3d3c-117">Um valor definido na coleção do manipulador de tokens substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="d3d3c-118">máximoClockSkew</span><span class="sxs-lookup"><span data-stu-id="d3d3c-118">maximumClockSkew</span></span>|<span data-ttu-id="d3d3c-119">A <xref:System.TimeSpan> que especifica a distorção máxima permitida do relógio.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="d3d3c-120">Controla a distorção máxima do relógio permitida ao realizar operações sensíveis ao tempo, como validar o tempo de expiração de uma sessão de login.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="d3d3c-121">O padrão é 5 minutos, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="d3d3c-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="d3d3c-122">Para obter mais informações <xref:System.TimeSpan> sobre como especificar valores, consulte [Timespan Values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3d3c-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="d3d3c-123">A distorção máxima do relógio também pode ser `maximumClockSkew` definida no nível de serviço, definindo o atributo no elemento [ \<identityConfiguration>.](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d3d3c-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="d3d3c-124">Um valor definido na coleção do manipulador de tokens substitui o valor definido no serviço.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3d3c-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d3d3c-125">Child Elements</span></span>  
  
|<span data-ttu-id="d3d3c-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3d3c-126">Element</span></span>|<span data-ttu-id="d3d3c-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3d3c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3d3c-128">\<audiênciaUris></span><span class="sxs-lookup"><span data-stu-id="d3d3c-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="d3d3c-129">Especifica o conjunto de URIs que são identificadores aceitáveis desta parte que depende.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="d3d3c-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-130">Optional.</span></span>|  
|[<span data-ttu-id="d3d3c-131">\<caches></span><span class="sxs-lookup"><span data-stu-id="d3d3c-131">\<caches></span></span>](caches.md)|<span data-ttu-id="d3d3c-132">Registra os caches usados para tokens de sessão e detecção de replay de tokens.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="d3d3c-133">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="d3d3c-134">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-134">Optional.</span></span>|  
|[<span data-ttu-id="d3d3c-135">\<>de validação de certificados</span><span class="sxs-lookup"><span data-stu-id="d3d3c-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="d3d3c-136">Controla as configurações que os manipuladores de tokens usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="d3d3c-137">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="d3d3c-138">Essas configurações são substituídas se um manipulador específico estiver configurado com seu próprio validador.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="d3d3c-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-139">Optional.</span></span>|  
|[<span data-ttu-id="d3d3c-140">\<emissorNomeregistro></span><span class="sxs-lookup"><span data-stu-id="d3d3c-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="d3d3c-141">Configura o registro de nome do emissor que é usado pelos manipuladores na coleção do manipulador de tokens.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="d3d3c-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-142">Optional.</span></span>|  
|[<span data-ttu-id="d3d3c-143">\<emissorTokenResolver></span><span class="sxs-lookup"><span data-stu-id="d3d3c-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="d3d3c-144">Registra o resolver token emissor usado pelos manipuladores na coleção de manipuladores de tokens.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="d3d3c-145">O resolver token do emissor é usado para resolver o token de assinatura em tokens e mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="d3d3c-146">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-146">Optional.</span></span>|  
|[<span data-ttu-id="d3d3c-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="d3d3c-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="d3d3c-148">Registra o resolver token de serviço que é usado pelos manipuladores na coleção de manipuladores de tokens.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="d3d3c-149">O resolvede token de serviço é usado para resolver o token de criptografia em tokens e mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="d3d3c-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-150">Optional.</span></span>|  
|[<span data-ttu-id="d3d3c-151">\<ReproduçãoDetecção de erros></span><span class="sxs-lookup"><span data-stu-id="d3d3c-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="d3d3c-152">Permite a detecção de replay de token e especifica o tempo de expiração dos tokens.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="d3d3c-153">Pode ser especificado no nível de serviço ou em uma coleção de manipulador de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="d3d3c-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3d3c-155">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d3d3c-155">Parent Elements</span></span>  
  
|<span data-ttu-id="d3d3c-156">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3d3c-156">Element</span></span>|<span data-ttu-id="d3d3c-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3d3c-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3d3c-158">\<>de segurançaTokenHandlers</span><span class="sxs-lookup"><span data-stu-id="d3d3c-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="d3d3c-159">Especifica uma coleção de manipuladores de tokens de segurança que estão registrados com o ponto final.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3d3c-160">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3d3c-160">Remarks</span></span>  
 <span data-ttu-id="d3d3c-161">Esta seção fornece <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> valores de propriedade para um objeto.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="d3d3c-162">As configurações configuradas nesta seção sobrepõem as configuradas no serviço.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="d3d3c-163">Algumas dessas configurações podem, por sua vez, ser substituídas por configurações especificadas quando um manipulador é adicionado à coleção de manipuladores de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="d3d3c-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3d3c-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3d3c-164">Example</span></span>  
  
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
