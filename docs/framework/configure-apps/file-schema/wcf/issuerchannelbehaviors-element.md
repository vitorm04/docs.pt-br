---
title: Elemento <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 3386a287d577681b67bd3ad54a75b0276e29da1f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357242"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="50767-102">\<issuerChannelBehaviors > elemento</span><span class="sxs-lookup"><span data-stu-id="50767-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="50767-103">Contém uma coleção de comportamentos de ponto de extremidade do cliente do Windows Communication Foundation (WCF) (definido na configuração) para ser usado ao se comunicar com os serviços de Token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="50767-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="50767-104">Os comportamentos definidos não podem incluir nenhum [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="50767-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>

<span data-ttu-id="50767-105">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="50767-105">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="50767-106">\<comportamentos > \\</span><span class="sxs-lookup"><span data-stu-id="50767-106">\<behaviors>\\</span></span>
<span data-ttu-id="50767-107">section\ endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="50767-107">endpointBehaviors section\\</span></span>
<span data-ttu-id="50767-108">\<behavior>\\</span><span class="sxs-lookup"><span data-stu-id="50767-108">\<behavior>\\</span></span>
<span data-ttu-id="50767-109">\<clientCredentials>\\</span><span class="sxs-lookup"><span data-stu-id="50767-109">\<clientCredentials>\\</span></span>
<span data-ttu-id="50767-110">\<issuedToken>\\</span><span class="sxs-lookup"><span data-stu-id="50767-110">\<issuedToken>\\</span></span>
<span data-ttu-id="50767-111">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="50767-111">\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="50767-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50767-112">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50767-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="50767-113">Attributes and Elements</span></span>

<span data-ttu-id="50767-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="50767-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="50767-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="50767-115">Attributes</span></span>

<span data-ttu-id="50767-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="50767-116">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50767-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="50767-117">Child Elements</span></span>

|<span data-ttu-id="50767-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="50767-118">Element</span></span>|<span data-ttu-id="50767-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="50767-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50767-120">\<add></span><span class="sxs-lookup"><span data-stu-id="50767-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="50767-121">Adiciona um comportamento à coleção.</span><span class="sxs-lookup"><span data-stu-id="50767-121">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50767-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="50767-122">Parent Elements</span></span>

|<span data-ttu-id="50767-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="50767-123">Element</span></span>|<span data-ttu-id="50767-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="50767-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50767-125">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="50767-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="50767-126">Especifica um token personalizado usado para autenticar um cliente a um serviço.</span><span class="sxs-lookup"><span data-stu-id="50767-126">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50767-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="50767-127">Remarks</span></span>

<span data-ttu-id="50767-128">Use esse elemento quando qualquer comportamentos (diferente de comportamentos que incluem `<clientCredentials>` elementos) deve ser usado para se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="50767-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="50767-129">Por exemplo, se um [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) elemento de comportamento deve ser incluído.</span><span class="sxs-lookup"><span data-stu-id="50767-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="50767-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50767-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="50767-131">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="50767-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="50767-132">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="50767-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="50767-133">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="50767-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="50767-134">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="50767-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="50767-135">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="50767-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="50767-136">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="50767-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="50767-137">Como: Configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="50767-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="50767-138">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="50767-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
