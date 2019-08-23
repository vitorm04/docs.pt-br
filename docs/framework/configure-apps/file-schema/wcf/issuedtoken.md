---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925377"
---
# <a name="issuedtoken"></a><span data-ttu-id="8c824-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="8c824-101">\<issuedToken></span></span>
<span data-ttu-id="8c824-102">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="8c824-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="8c824-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8c824-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8c824-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="8c824-104">\<behaviors></span></span>  
<span data-ttu-id="8c824-105">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="8c824-105">endpointBehaviors section</span></span>  
<span data-ttu-id="8c824-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="8c824-106">\<behavior></span></span>  
<span data-ttu-id="8c824-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8c824-107">\<clientCredentials></span></span>  
<span data-ttu-id="8c824-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="8c824-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c824-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c824-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c824-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8c824-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c824-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8c824-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c824-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8c824-112">Attributes</span></span>  
  
|<span data-ttu-id="8c824-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8c824-113">Attribute</span></span>|<span data-ttu-id="8c824-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c824-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="8c824-115">Atributo booliano opcional que especifica se os tokens são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="8c824-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="8c824-116">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="8c824-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="8c824-117">Atributo de cadeia de caracteres opcional que especifica quais valores aleatórios (entropias) são usados para operações de handshake.</span><span class="sxs-lookup"><span data-stu-id="8c824-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="8c824-118">Os valores `ClientEntropy`incluem `ServerEntropy`, e `CombinedEntropy`, o padrão é `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="8c824-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="8c824-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="8c824-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="8c824-120">Atributo inteiro opcional que especifica a porcentagem de um período de tempo válido (fornecido pelo emissor do token) que pode passar antes de um token ser renovado.</span><span class="sxs-lookup"><span data-stu-id="8c824-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="8c824-121">Os valores são de 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="8c824-121">Values are from 0 to 100.</span></span> <span data-ttu-id="8c824-122">O padrão é 60, que especifica 60% do tempo passado antes da tentativa de renovação.</span><span class="sxs-lookup"><span data-stu-id="8c824-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="8c824-123">Atributo opcional que especifica os comportamentos de canal a serem usados ao se comunicar com o emissor.</span><span class="sxs-lookup"><span data-stu-id="8c824-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="8c824-124">Atributo opcional que especifica os comportamentos de canal a serem usados ao se comunicar com o emissor local.</span><span class="sxs-lookup"><span data-stu-id="8c824-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="8c824-125">Atributo TimeSpan opcional que especifica a duração em que os tokens emitidos são armazenados em cache quando o emissor do token (um STS) não especifica uma hora.</span><span class="sxs-lookup"><span data-stu-id="8c824-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="8c824-126">O padrão é "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="8c824-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c824-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8c824-127">Child Elements</span></span>  
  
|<span data-ttu-id="8c824-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c824-128">Element</span></span>|<span data-ttu-id="8c824-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c824-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c824-130">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="8c824-130">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="8c824-131">Especifica o endereço do emissor local do token e a associação usada para se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8c824-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="8c824-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="8c824-132">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="8c824-133">Especifica os comportamentos de ponto de extremidade a serem usados ao contatar um emissor local.</span><span class="sxs-lookup"><span data-stu-id="8c824-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c824-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8c824-134">Parent Elements</span></span>  
  
|<span data-ttu-id="8c824-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="8c824-135">Element</span></span>|<span data-ttu-id="8c824-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c824-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c824-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8c824-137">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="8c824-138">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="8c824-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c824-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c824-139">Remarks</span></span>  
 <span data-ttu-id="8c824-140">Um token emitido é um tipo de credencial personalizado usado, por exemplo, ao autenticar com um serviço de token de segurança (STS) em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="8c824-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="8c824-141">Por padrão, o token é um token SAML.</span><span class="sxs-lookup"><span data-stu-id="8c824-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="8c824-142">Para obter mais informações, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="8c824-142">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="8c824-143">e a [Federação e](../../../wcf/feature-details/federation-and-issued-tokens.md)os tokens emitidos.</span><span class="sxs-lookup"><span data-stu-id="8c824-143">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="8c824-144">Esta seção contém os elementos usados para configurar um emissor local de tokens ou os comportamentos usados com um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="8c824-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="8c824-145">Para obter instruções sobre como configurar um cliente para usar um emissor local, [consulte Como: Configure um emissor](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)local.</span><span class="sxs-lookup"><span data-stu-id="8c824-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c824-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c824-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="8c824-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="8c824-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8c824-148">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8c824-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8c824-149">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="8c824-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8c824-150">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="8c824-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="8c824-151">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="8c824-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="8c824-152">Como: Configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="8c824-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="8c824-153">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="8c824-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
