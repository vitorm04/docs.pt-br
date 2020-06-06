---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "72846866"
---
# \<issuedToken>
<span data-ttu-id="b995c-101">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b995c-101">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="b995c-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b995c-102">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b995c-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b995c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b995c-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b995c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b995c-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="b995c-105">Attributes</span></span>  
  
|<span data-ttu-id="b995c-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="b995c-106">Attribute</span></span>|<span data-ttu-id="b995c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b995c-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="b995c-108">Atributo booliano opcional que especifica se os tokens são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="b995c-108">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="b995c-109">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b995c-109">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="b995c-110">Atributo de cadeia de caracteres opcional que especifica quais valores aleatórios (entropias) são usados para operações de handshake.</span><span class="sxs-lookup"><span data-stu-id="b995c-110">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="b995c-111">Os valores incluem `ClientEntropy` , `ServerEntropy` e `CombinedEntropy` , o padrão é `CombinedEntropy` .</span><span class="sxs-lookup"><span data-stu-id="b995c-111">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="b995c-112">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> .</span><span class="sxs-lookup"><span data-stu-id="b995c-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="b995c-113">Atributo inteiro opcional que especifica a porcentagem de um período de tempo válido (fornecido pelo emissor do token) que pode passar antes de um token ser renovado.</span><span class="sxs-lookup"><span data-stu-id="b995c-113">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="b995c-114">Os valores são de 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="b995c-114">Values are from 0 to 100.</span></span> <span data-ttu-id="b995c-115">O padrão é 60, que especifica 60% do tempo passado antes da tentativa de renovação.</span><span class="sxs-lookup"><span data-stu-id="b995c-115">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="b995c-116">Atributo opcional que especifica os comportamentos de canal a serem usados ao se comunicar com o emissor.</span><span class="sxs-lookup"><span data-stu-id="b995c-116">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="b995c-117">Atributo opcional que especifica os comportamentos de canal a serem usados ao se comunicar com o emissor local.</span><span class="sxs-lookup"><span data-stu-id="b995c-117">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="b995c-118">Atributo TimeSpan opcional que especifica a duração em que os tokens emitidos são armazenados em cache quando o emissor do token (um STS) não especifica uma hora.</span><span class="sxs-lookup"><span data-stu-id="b995c-118">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="b995c-119">O padrão é "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="b995c-119">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b995c-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b995c-120">Child Elements</span></span>  
  
|<span data-ttu-id="b995c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="b995c-121">Element</span></span>|<span data-ttu-id="b995c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b995c-122">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="b995c-123">Especifica o endereço do emissor local do token e a associação usada para se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b995c-123">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="b995c-124">Especifica os comportamentos de ponto de extremidade a serem usados ao contatar um emissor local.</span><span class="sxs-lookup"><span data-stu-id="b995c-124">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b995c-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b995c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b995c-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="b995c-126">Element</span></span>|<span data-ttu-id="b995c-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="b995c-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="b995c-128">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b995c-128">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b995c-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="b995c-129">Remarks</span></span>  
 <span data-ttu-id="b995c-130">Um token emitido é um tipo de credencial personalizado usado, por exemplo, ao autenticar com um serviço de token de segurança (STS) em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="b995c-130">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="b995c-131">Por padrão, o token é um token SAML.</span><span class="sxs-lookup"><span data-stu-id="b995c-131">By default, the token is a SAML token.</span></span> <span data-ttu-id="b995c-132">Para obter mais informações, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md)e [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="b995c-132">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="b995c-133">Esta seção contém os elementos usados para configurar um emissor local de tokens ou os comportamentos usados com um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="b995c-133">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="b995c-134">Para obter instruções sobre como configurar um cliente para usar um emissor local, consulte [como: configurar um emissor local](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="b995c-134">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b995c-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="b995c-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="b995c-136">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b995c-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b995c-137">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b995c-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b995c-138">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b995c-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b995c-139">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="b995c-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b995c-140">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="b995c-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="b995c-141">Como configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="b995c-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="b995c-142">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b995c-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
