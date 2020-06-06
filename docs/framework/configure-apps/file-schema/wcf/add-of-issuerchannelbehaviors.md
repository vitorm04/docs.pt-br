---
title: <add> de <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398326"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="75319-102">\<add> de \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="75319-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="75319-103">Adiciona um comportamento de ponto de extremidade a ser usado ao se comunicar com um STS.</span><span class="sxs-lookup"><span data-stu-id="75319-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="75319-104">Se qualquer comportamento de ponto de extremidade contiver um [\<clientCredentials>](clientcredentials.md) elemento, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="75319-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="75319-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75319-105">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75319-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="75319-106">Attributes and Elements</span></span>

<span data-ttu-id="75319-107">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="75319-107">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="75319-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="75319-108">Attributes</span></span>

|<span data-ttu-id="75319-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="75319-109">Attribute</span></span>|<span data-ttu-id="75319-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="75319-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="75319-111">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="75319-111">issuerAddress</span></span>|<span data-ttu-id="75319-112">O URI do emissor do token de segurança com o qual se comunicar.</span><span class="sxs-lookup"><span data-stu-id="75319-112">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="75319-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="75319-113">behaviorConfiguration</span></span>|<span data-ttu-id="75319-114">O nome de um comportamento de ponto de extremidade definido no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="75319-114">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="75319-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="75319-115">Child Elements</span></span>

<span data-ttu-id="75319-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="75319-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75319-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="75319-117">Parent Elements</span></span>

|<span data-ttu-id="75319-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="75319-118">Element</span></span>|<span data-ttu-id="75319-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="75319-119">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="75319-120">Contém uma coleção de comportamentos de ponto de extremidade de cliente do Windows Communication Foundation (WCF) a ser usada ao se comunicar com os serviços de token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="75319-120">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75319-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="75319-121">Remarks</span></span>

<span data-ttu-id="75319-122">`issuerAddress`contém o URI do serviço de token de segurança com o qual o cliente deseja se comunicar.</span><span class="sxs-lookup"><span data-stu-id="75319-122">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="75319-123">`behaviorConfiguration`aponta para um comportamento de ponto de extremidade que o aplicativo usa nos canais criados por Windows Communication Foundation (WCF) para obter os tokens emitidos dos serviços de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="75319-123">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="75319-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="75319-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="75319-125">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="75319-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="75319-126">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="75319-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="75319-127">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="75319-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="75319-128">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="75319-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="75319-129">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="75319-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="75319-130">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="75319-130">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="75319-131">Como configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="75319-131">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="75319-132">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="75319-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
