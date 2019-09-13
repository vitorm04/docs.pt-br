---
title: Elemento <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: cbbfb9d3b5af47a360aa82cf837cd6749f61b641
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893150"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="b0aa8-102">\<Elemento de > issuerChannelBehaviors</span><span class="sxs-lookup"><span data-stu-id="b0aa8-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="b0aa8-103">Contém uma coleção de comportamentos de ponto de extremidade de cliente do Windows Communication Foundation (WCF) (definida na configuração) a ser usada na comunicação com os serviços de token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="b0aa8-104">Os comportamentos definidos não podem incluir [ \<ClientCredentials >](clientcredentials.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="b0aa8-105">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b0aa8-105">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="b0aa8-106">&nbsp;&nbsp;[\<> de System. serviceModel](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b0aa8-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="b0aa8-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<comportamentos >](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b0aa8-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="b0aa8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> endpointBehaviors](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b0aa8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="b0aa8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> de comportamento](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b0aa8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="b0aa8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials >](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b0aa8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="b0aa8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> issuedToken](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="b0aa8-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="b0aa8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<> issuerChannelBehaviors</span><span class="sxs-lookup"><span data-stu-id="b0aa8-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="b0aa8-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0aa8-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b0aa8-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b0aa8-114">Attributes and elements</span></span>

<span data-ttu-id="b0aa8-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b0aa8-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="b0aa8-116">Attributes</span></span>

<span data-ttu-id="b0aa8-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b0aa8-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b0aa8-118">Child elements</span></span>

|<span data-ttu-id="b0aa8-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b0aa8-119">Element</span></span>|<span data-ttu-id="b0aa8-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0aa8-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0aa8-121">\<add></span><span class="sxs-lookup"><span data-stu-id="b0aa8-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="b0aa8-122">Adiciona um comportamento à coleção.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b0aa8-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b0aa8-123">Parent elements</span></span>

|<span data-ttu-id="b0aa8-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="b0aa8-124">Element</span></span>|<span data-ttu-id="b0aa8-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0aa8-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b0aa8-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="b0aa8-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="b0aa8-127">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b0aa8-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0aa8-128">Remarks</span></span>

<span data-ttu-id="b0aa8-129">Use este elemento quando quaisquer comportamentos (que não sejam os comportamentos `<clientCredentials>` que incluem elementos) devem ser usados para se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="b0aa8-130">Por exemplo, se um elemento de comportamento de [ \<> do DataContractSerializer](datacontractserializer-element.md) precisar ser incluído.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0aa8-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0aa8-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="b0aa8-132">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="b0aa8-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b0aa8-133">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b0aa8-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b0aa8-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b0aa8-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b0aa8-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b0aa8-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b0aa8-136">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="b0aa8-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b0aa8-137">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="b0aa8-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="b0aa8-138">Como: Configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="b0aa8-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="b0aa8-139">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b0aa8-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
