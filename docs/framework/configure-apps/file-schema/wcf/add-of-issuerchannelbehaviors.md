---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398326"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="fc7e2-102">\<Adicionar > de \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fc7e2-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="fc7e2-103">Adiciona um comportamento de ponto de extremidade a ser usado ao se comunicar com um STS.</span><span class="sxs-lookup"><span data-stu-id="fc7e2-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="fc7e2-104">Se qualquer comportamento de ponto de extremidade contiver um elemento de [ \<> ClientCredentials](clientcredentials.md) , uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="fc7e2-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="fc7e2-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fc7e2-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fc7e2-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fc7e2-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fc7e2-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fc7e2-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fc7e2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fc7e2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="fc7e2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fc7e2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="fc7e2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="fc7e2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="fc7e2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedToken**](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="fc7e2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="fc7e2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuerChannelBehaviors**](issuerchannelbehaviors-element.md)</span><span class="sxs-lookup"><span data-stu-id="fc7e2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)</span></span>\
<span data-ttu-id="fc7e2-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="fc7e2-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="fc7e2-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc7e2-114">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc7e2-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fc7e2-115">Attributes and Elements</span></span>

<span data-ttu-id="fc7e2-116">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="fc7e2-116">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="fc7e2-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="fc7e2-117">Attributes</span></span>

|<span data-ttu-id="fc7e2-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="fc7e2-118">Attribute</span></span>|<span data-ttu-id="fc7e2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc7e2-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fc7e2-120">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="fc7e2-120">issuerAddress</span></span>|<span data-ttu-id="fc7e2-121">O URI do emissor do token de segurança com o qual se comunicar.</span><span class="sxs-lookup"><span data-stu-id="fc7e2-121">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="fc7e2-122">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc7e2-122">behaviorConfiguration</span></span>|<span data-ttu-id="fc7e2-123">O nome de um comportamento de ponto de extremidade definido no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="fc7e2-123">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="fc7e2-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fc7e2-124">Child Elements</span></span>

<span data-ttu-id="fc7e2-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fc7e2-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc7e2-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fc7e2-126">Parent Elements</span></span>

|<span data-ttu-id="fc7e2-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc7e2-127">Element</span></span>|<span data-ttu-id="fc7e2-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc7e2-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc7e2-129">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="fc7e2-129">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="fc7e2-130">Contém uma coleção de comportamentos de ponto de extremidade de cliente do Windows Communication Foundation (WCF) a ser usada ao se comunicar com os serviços de token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="fc7e2-130">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fc7e2-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc7e2-131">Remarks</span></span>

<span data-ttu-id="fc7e2-132">`issuerAddress`contém o URI do serviço de token de segurança com o qual o cliente deseja se comunicar.</span><span class="sxs-lookup"><span data-stu-id="fc7e2-132">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="fc7e2-133">`behaviorConfiguration`aponta para um comportamento de ponto de extremidade que o aplicativo usa nos canais criados por Windows Communication Foundation (WCF) para obter os tokens emitidos dos serviços de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="fc7e2-133">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc7e2-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc7e2-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="fc7e2-135">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="fc7e2-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fc7e2-136">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="fc7e2-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="fc7e2-137">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="fc7e2-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fc7e2-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="fc7e2-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fc7e2-139">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="fc7e2-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="fc7e2-140">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="fc7e2-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="fc7e2-141">Como: Configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="fc7e2-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="fc7e2-142">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="fc7e2-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fc7e2-143">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="fc7e2-143">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
