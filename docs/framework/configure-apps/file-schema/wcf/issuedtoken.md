---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 83061b283c9430af7bcda9cbc832811fa805ed4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104943"
---
# <a name="issuedtoken"></a><span data-ttu-id="058de-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="058de-101">\<issuedToken></span></span>
<span data-ttu-id="058de-102">Especifica um token personalizado usado para autenticar um cliente a um serviço.</span><span class="sxs-lookup"><span data-stu-id="058de-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="058de-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="058de-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="058de-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="058de-104">\<behaviors></span></span>  
<span data-ttu-id="058de-105">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="058de-105">endpointBehaviors section</span></span>  
<span data-ttu-id="058de-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="058de-106">\<behavior></span></span>  
<span data-ttu-id="058de-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="058de-107">\<clientCredentials></span></span>  
<span data-ttu-id="058de-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="058de-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="058de-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="058de-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="058de-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="058de-110">Attributes and Elements</span></span>  
 <span data-ttu-id="058de-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="058de-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="058de-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="058de-112">Attributes</span></span>  
  
|<span data-ttu-id="058de-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="058de-113">Attribute</span></span>|<span data-ttu-id="058de-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="058de-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="058de-115">Atributo booleano opcional que especifica se tokens são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="058de-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="058de-116">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="058de-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="058de-117">Atributo de cadeia de caracteres opcional que especifica quais valores aleatórios (entropias) são usados para operações de handshake.</span><span class="sxs-lookup"><span data-stu-id="058de-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="058de-118">Os valores incluem `ClientEntropy`, `ServerEntropy`, e `CombinedEntropy`, o padrão é `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="058de-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="058de-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="058de-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="058de-120">Atributo inteiro opcional que especifica a porcentagem de um período válido (fornecido pelo emissor de token) que pode decorrer antes que um token seja renovado.</span><span class="sxs-lookup"><span data-stu-id="058de-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="058de-121">Os valores são de 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="058de-121">Values are from 0 to 100.</span></span> <span data-ttu-id="058de-122">O padrão é 60, que especifica a 60% de tempo passa antes da tentativa de uma renovação.</span><span class="sxs-lookup"><span data-stu-id="058de-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="058de-123">Atributo opcional que especifica os comportamentos do canal para usar ao se comunicar com o emissor.</span><span class="sxs-lookup"><span data-stu-id="058de-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="058de-124">Atributo opcional que especifica os comportamentos do canal para usar ao se comunicar com o emissor local.</span><span class="sxs-lookup"><span data-stu-id="058de-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="058de-125">Atributo Timespan opcional que especifica a duração que tokens emitidos são armazenados em cache quando o emissor do token (STS) não especifica uma hora.</span><span class="sxs-lookup"><span data-stu-id="058de-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="058de-126">O padrão é "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="058de-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="058de-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="058de-127">Child Elements</span></span>  
  
|<span data-ttu-id="058de-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="058de-128">Element</span></span>|<span data-ttu-id="058de-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="058de-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="058de-130">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="058de-130">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="058de-131">Especifica o endereço do emissor do token e a associação usada para se comunicar com o ponto de extremidade local.</span><span class="sxs-lookup"><span data-stu-id="058de-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="058de-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="058de-132">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="058de-133">Especifica os comportamentos de ponto de extremidade a ser usado ao entrar em contato com um emissor local.</span><span class="sxs-lookup"><span data-stu-id="058de-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="058de-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="058de-134">Parent Elements</span></span>  
  
|<span data-ttu-id="058de-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="058de-135">Element</span></span>|<span data-ttu-id="058de-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="058de-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="058de-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="058de-137">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="058de-138">Especifica as credenciais usadas para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="058de-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="058de-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="058de-139">Remarks</span></span>  
 <span data-ttu-id="058de-140">Um token emitido é um tipo de credencial personalizada usado, por exemplo, ao autenticar com um Secure Token Service (STS) em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="058de-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="058de-141">Por padrão, o token é um token SAML.</span><span class="sxs-lookup"><span data-stu-id="058de-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="058de-142">Para obter mais informações, consulte [federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="058de-142">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="058de-143">e [federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="058de-143">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="058de-144">Esta seção contém os elementos usados para configurar um emissor local de tokens ou comportamentos usados com um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="058de-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="058de-145">Para obter instruções sobre como configurar um cliente para usar um emissor local, consulte [como: Configurar um emissor Local](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="058de-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="058de-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="058de-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="058de-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="058de-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="058de-148">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="058de-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="058de-149">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="058de-149">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="058de-150">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="058de-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="058de-151">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="058de-151">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="058de-152">Como: configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="058de-152">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="058de-153">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="058de-153">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
