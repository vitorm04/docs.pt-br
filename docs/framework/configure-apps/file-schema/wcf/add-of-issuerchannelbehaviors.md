---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 5c9937cb6302a194228461f3e2e06ecdf4d43269
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673609"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="2698c-102">\<Adicionar > de \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2698c-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="2698c-103">Adiciona um comportamento de ponto de extremidade a ser usado ao se comunicar com um STS.</span><span class="sxs-lookup"><span data-stu-id="2698c-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="2698c-104">Se qualquer comportamento de ponto de extremidade contém um [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="2698c-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="2698c-105">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="2698c-105">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="2698c-106">\<comportamentos > \\</span><span class="sxs-lookup"><span data-stu-id="2698c-106">\<behaviors>\\</span></span>
<span data-ttu-id="2698c-107">seção endpointBehaviors \<comportamento > \\</span><span class="sxs-lookup"><span data-stu-id="2698c-107">endpointBehaviors section \<behavior>\\</span></span>
<span data-ttu-id="2698c-108">\<clientCredentials>\\</span><span class="sxs-lookup"><span data-stu-id="2698c-108">\<clientCredentials>\\</span></span>
<span data-ttu-id="2698c-109">\<issuedToken>\\</span><span class="sxs-lookup"><span data-stu-id="2698c-109">\<issuedToken>\\</span></span>
<span data-ttu-id="2698c-110">\<issuerChannelBehaviors > Element\\</span><span class="sxs-lookup"><span data-stu-id="2698c-110">\<issuerChannelBehaviors> Element\\</span></span>
<span data-ttu-id="2698c-111">\<add></span><span class="sxs-lookup"><span data-stu-id="2698c-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="2698c-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2698c-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2698c-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2698c-113">Attributes and Elements</span></span>

<span data-ttu-id="2698c-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="2698c-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="2698c-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="2698c-115">Attributes</span></span>

|<span data-ttu-id="2698c-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="2698c-116">Attribute</span></span>|<span data-ttu-id="2698c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2698c-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="2698c-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="2698c-118">issuerAddress</span></span>|<span data-ttu-id="2698c-119">O URI do emissor do token de segurança para se comunicar com.</span><span class="sxs-lookup"><span data-stu-id="2698c-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="2698c-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="2698c-120">behaviorConfiguration</span></span>|<span data-ttu-id="2698c-121">O nome de um comportamento de ponto de extremidade definido no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2698c-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2698c-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2698c-122">Child Elements</span></span>

<span data-ttu-id="2698c-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2698c-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2698c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2698c-124">Parent Elements</span></span>

|<span data-ttu-id="2698c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="2698c-125">Element</span></span>|<span data-ttu-id="2698c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="2698c-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2698c-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="2698c-127">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="2698c-128">Contém uma coleção de comportamentos de ponto de extremidade do cliente Windows Communication Foundation (WCF) a ser usado ao se comunicar com os serviços de Token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="2698c-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2698c-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="2698c-129">Remarks</span></span>

<span data-ttu-id="2698c-130">`issuerAddress` contém o URI do serviço de Token de segurança que o cliente quer se comunicar com.</span><span class="sxs-lookup"><span data-stu-id="2698c-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="2698c-131">`behaviorConfiguration` aponta para um comportamento de ponto de extremidade que o aplicativo usa nos canais criados pelo Windows Communication Foundation (WCF) para obter os tokens emitidos de serviços de Token de segurança.</span><span class="sxs-lookup"><span data-stu-id="2698c-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="2698c-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2698c-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="2698c-133">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="2698c-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2698c-134">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="2698c-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2698c-135">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="2698c-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2698c-136">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2698c-136">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2698c-137">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="2698c-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="2698c-138">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="2698c-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="2698c-139">Como: Configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="2698c-139">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="2698c-140">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="2698c-140">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2698c-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="2698c-141">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
