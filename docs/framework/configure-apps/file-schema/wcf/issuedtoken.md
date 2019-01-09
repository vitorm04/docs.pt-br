---
title: '&lt;IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: a06d59c5dfb14e5f3346ff2424339659568a369a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150182"
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="99290-102">&lt;IssuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="99290-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="99290-103">Especifica um token personalizado usado para autenticar um cliente a um serviço.</span><span class="sxs-lookup"><span data-stu-id="99290-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="99290-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="99290-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="99290-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="99290-105">\<behaviors></span></span>  
<span data-ttu-id="99290-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="99290-106">endpointBehaviors section</span></span>  
<span data-ttu-id="99290-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="99290-107">\<behavior></span></span>  
<span data-ttu-id="99290-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="99290-108">\<clientCredentials></span></span>  
<span data-ttu-id="99290-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="99290-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99290-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99290-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99290-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="99290-111">Attributes and Elements</span></span>  
 <span data-ttu-id="99290-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="99290-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99290-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="99290-113">Attributes</span></span>  
  
|<span data-ttu-id="99290-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="99290-114">Attribute</span></span>|<span data-ttu-id="99290-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="99290-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="99290-116">Atributo booleano opcional que especifica se tokens são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="99290-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="99290-117">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="99290-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="99290-118">Atributo de cadeia de caracteres opcional que especifica quais valores aleatórios (entropias) são usados para operações de handshake.</span><span class="sxs-lookup"><span data-stu-id="99290-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="99290-119">Os valores incluem `ClientEntropy`, `ServerEntropy`, e `CombinedEntropy`, o padrão é `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="99290-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="99290-120">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="99290-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="99290-121">Atributo inteiro opcional que especifica a porcentagem de um período válido (fornecido pelo emissor de token) que pode decorrer antes que um token seja renovado.</span><span class="sxs-lookup"><span data-stu-id="99290-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="99290-122">Os valores são de 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="99290-122">Values are from 0 to 100.</span></span> <span data-ttu-id="99290-123">O padrão é 60, que especifica a 60% de tempo passa antes da tentativa de uma renovação.</span><span class="sxs-lookup"><span data-stu-id="99290-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="99290-124">Atributo opcional que especifica os comportamentos do canal para usar ao se comunicar com o emissor.</span><span class="sxs-lookup"><span data-stu-id="99290-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="99290-125">Atributo opcional que especifica os comportamentos do canal para usar ao se comunicar com o emissor local.</span><span class="sxs-lookup"><span data-stu-id="99290-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="99290-126">Atributo Timespan opcional que especifica a duração que tokens emitidos são armazenados em cache quando o emissor do token (STS) não especifica uma hora.</span><span class="sxs-lookup"><span data-stu-id="99290-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="99290-127">O padrão é "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="99290-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99290-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="99290-128">Child Elements</span></span>  
  
|<span data-ttu-id="99290-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="99290-129">Element</span></span>|<span data-ttu-id="99290-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="99290-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99290-131">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="99290-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="99290-132">Especifica o endereço do emissor do token e a associação usada para se comunicar com o ponto de extremidade local.</span><span class="sxs-lookup"><span data-stu-id="99290-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="99290-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="99290-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="99290-134">Especifica os comportamentos de ponto de extremidade a ser usado ao entrar em contato com um emissor local.</span><span class="sxs-lookup"><span data-stu-id="99290-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99290-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="99290-135">Parent Elements</span></span>  
  
|<span data-ttu-id="99290-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="99290-136">Element</span></span>|<span data-ttu-id="99290-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="99290-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99290-138">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="99290-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="99290-139">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="99290-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99290-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="99290-140">Remarks</span></span>  
 <span data-ttu-id="99290-141">Um token emitido é um tipo de credencial personalizada usado, por exemplo, ao autenticar com um Secure Token Service (STS) em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="99290-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="99290-142">Por padrão, o token é um token SAML.</span><span class="sxs-lookup"><span data-stu-id="99290-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="99290-143">Para obter mais informações, consulte [federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="99290-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="99290-144">e [federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="99290-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="99290-145">Esta seção contém os elementos usados para configurar um emissor local de tokens ou comportamentos usados com um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="99290-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="99290-146">Para obter instruções sobre como configurar um cliente para usar um emissor local, consulte [como: Configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="99290-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99290-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99290-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="99290-148">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="99290-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="99290-149">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="99290-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="99290-150">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="99290-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="99290-151">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="99290-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="99290-152">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="99290-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="99290-153">Como: Configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="99290-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="99290-154">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="99290-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
