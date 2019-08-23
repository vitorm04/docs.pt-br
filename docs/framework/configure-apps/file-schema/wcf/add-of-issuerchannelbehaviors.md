---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920119"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="ec152-102">\<Adicionar > de \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ec152-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="ec152-103">Adiciona um comportamento de ponto de extremidade a ser usado ao se comunicar com um STS.</span><span class="sxs-lookup"><span data-stu-id="ec152-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="ec152-104">Se qualquer comportamento de ponto de extremidade contiver um elemento de [ \<> ClientCredentials](clientcredentials.md) , uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="ec152-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="ec152-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ec152-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="ec152-106">\<comportamentos > </span><span class="sxs-lookup"><span data-stu-id="ec152-106">\<behaviors></span></span>\
<span data-ttu-id="ec152-107">comportamento da \<seção EndpointBehaviors > </span><span class="sxs-lookup"><span data-stu-id="ec152-107">endpointBehaviors section \<behavior></span></span>\
<span data-ttu-id="ec152-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ec152-108">\<clientCredentials></span></span>\
<span data-ttu-id="ec152-109">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="ec152-109">\<issuedToken></span></span>\
<span data-ttu-id="ec152-110">\<Elemento de > issuerChannelBehaviors </span><span class="sxs-lookup"><span data-stu-id="ec152-110">\<issuerChannelBehaviors> Element</span></span>\
<span data-ttu-id="ec152-111">\<add></span><span class="sxs-lookup"><span data-stu-id="ec152-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="ec152-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec152-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec152-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec152-113">Attributes and Elements</span></span>

<span data-ttu-id="ec152-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec152-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="ec152-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec152-115">Attributes</span></span>

|<span data-ttu-id="ec152-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="ec152-116">Attribute</span></span>|<span data-ttu-id="ec152-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec152-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="ec152-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="ec152-118">issuerAddress</span></span>|<span data-ttu-id="ec152-119">O URI do emissor do token de segurança com o qual se comunicar.</span><span class="sxs-lookup"><span data-stu-id="ec152-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="ec152-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ec152-120">behaviorConfiguration</span></span>|<span data-ttu-id="ec152-121">O nome de um comportamento de ponto de extremidade definido no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ec152-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ec152-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ec152-122">Child Elements</span></span>

<span data-ttu-id="ec152-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ec152-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec152-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec152-124">Parent Elements</span></span>

|<span data-ttu-id="ec152-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec152-125">Element</span></span>|<span data-ttu-id="ec152-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec152-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec152-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="ec152-127">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="ec152-128">Contém uma coleção de comportamentos de ponto de extremidade de cliente do Windows Communication Foundation (WCF) a ser usada ao se comunicar com os serviços de token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="ec152-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ec152-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec152-129">Remarks</span></span>

<span data-ttu-id="ec152-130">`issuerAddress`contém o URI do serviço de token de segurança com o qual o cliente deseja se comunicar.</span><span class="sxs-lookup"><span data-stu-id="ec152-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="ec152-131">`behaviorConfiguration`aponta para um comportamento de ponto de extremidade que o aplicativo usa nos canais criados por Windows Communication Foundation (WCF) para obter os tokens emitidos dos serviços de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ec152-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec152-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec152-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="ec152-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="ec152-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ec152-134">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="ec152-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ec152-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ec152-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ec152-136">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ec152-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ec152-137">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="ec152-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ec152-138">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="ec152-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="ec152-139">Como: Configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="ec152-139">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="ec152-140">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="ec152-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ec152-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="ec152-141">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
