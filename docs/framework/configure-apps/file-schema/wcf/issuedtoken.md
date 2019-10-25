---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846866"
---
# <a name="issuedtoken"></a><span data-ttu-id="c2856-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="c2856-101">\<issuedToken></span></span>
<span data-ttu-id="c2856-102">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="c2856-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="c2856-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2856-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2856-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c2856-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c2856-105">&nbsp;&nbsp;&nbsp;&nbsp;\<[**comportamentos**](behaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="c2856-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\</span></span>
<span data-ttu-id="c2856-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c2856-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="c2856-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**comportamento**](behavior-of-endpointbehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="c2856-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="c2856-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientcredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c2856-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="c2856-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedToken >**</span><span class="sxs-lookup"><span data-stu-id="c2856-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2856-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2856-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2856-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c2856-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c2856-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c2856-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2856-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="c2856-113">Attributes</span></span>  
  
|<span data-ttu-id="c2856-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="c2856-114">Attribute</span></span>|<span data-ttu-id="c2856-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2856-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="c2856-116">Atributo booliano opcional que especifica se os tokens são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="c2856-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="c2856-117">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="c2856-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="c2856-118">Atributo de cadeia de caracteres opcional que especifica quais valores aleatórios (entropias) são usados para operações de handshake.</span><span class="sxs-lookup"><span data-stu-id="c2856-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="c2856-119">Os valores incluem `ClientEntropy`, `ServerEntropy`e `CombinedEntropy`, o padrão é `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="c2856-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="c2856-120">Este atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="c2856-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="c2856-121">Atributo inteiro opcional que especifica a porcentagem de um período de tempo válido (fornecido pelo emissor do token) que pode passar antes de um token ser renovado.</span><span class="sxs-lookup"><span data-stu-id="c2856-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="c2856-122">Os valores são de 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="c2856-122">Values are from 0 to 100.</span></span> <span data-ttu-id="c2856-123">O padrão é 60, que especifica 60% do tempo passado antes da tentativa de renovação.</span><span class="sxs-lookup"><span data-stu-id="c2856-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="c2856-124">Atributo opcional que especifica os comportamentos de canal a serem usados ao se comunicar com o emissor.</span><span class="sxs-lookup"><span data-stu-id="c2856-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="c2856-125">Atributo opcional que especifica os comportamentos de canal a serem usados ao se comunicar com o emissor local.</span><span class="sxs-lookup"><span data-stu-id="c2856-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="c2856-126">Atributo TimeSpan opcional que especifica a duração em que os tokens emitidos são armazenados em cache quando o emissor do token (um STS) não especifica uma hora.</span><span class="sxs-lookup"><span data-stu-id="c2856-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="c2856-127">O padrão é "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="c2856-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2856-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c2856-128">Child Elements</span></span>  
  
|<span data-ttu-id="c2856-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2856-129">Element</span></span>|<span data-ttu-id="c2856-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2856-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2856-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="c2856-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="c2856-132">Especifica o endereço do emissor local do token e a associação usada para se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c2856-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="c2856-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c2856-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="c2856-134">Especifica os comportamentos de ponto de extremidade a serem usados ao contatar um emissor local.</span><span class="sxs-lookup"><span data-stu-id="c2856-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2856-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c2856-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c2856-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2856-136">Element</span></span>|<span data-ttu-id="c2856-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2856-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2856-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c2856-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="c2856-139">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="c2856-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2856-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2856-140">Remarks</span></span>  
 <span data-ttu-id="c2856-141">Um token emitido é um tipo de credencial personalizado usado, por exemplo, ao autenticar com um serviço de token de segurança (STS) em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="c2856-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="c2856-142">Por padrão, o token é um token SAML.</span><span class="sxs-lookup"><span data-stu-id="c2856-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="c2856-143">Para obter mais informações, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)e [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="c2856-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="c2856-144">Esta seção contém os elementos usados para configurar um emissor local de tokens ou os comportamentos usados com um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="c2856-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="c2856-145">Para obter instruções sobre como configurar um cliente para usar um emissor local, consulte [como: configurar um emissor local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="c2856-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2856-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2856-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="c2856-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="c2856-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c2856-148">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c2856-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c2856-149">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c2856-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c2856-150">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="c2856-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c2856-151">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="c2856-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c2856-152">Como configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="c2856-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="c2856-153">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c2856-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
