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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70893150"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="20608-102">Elemento \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="20608-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="20608-103">Contém uma coleção de comportamentos de ponto de extremidade de cliente do Windows Communication Foundation (WCF) (definida na configuração) a ser usada na comunicação com os serviços de token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="20608-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="20608-104">Os comportamentos definidos não podem incluir nenhum [\<clientCredentials>](clientcredentials.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="20608-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors>

## <a name="syntax"></a><span data-ttu-id="20608-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20608-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20608-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="20608-106">Attributes and elements</span></span>

<span data-ttu-id="20608-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="20608-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="20608-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="20608-108">Attributes</span></span>

<span data-ttu-id="20608-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="20608-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20608-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="20608-110">Child elements</span></span>

|<span data-ttu-id="20608-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="20608-111">Element</span></span>|<span data-ttu-id="20608-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="20608-112">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="20608-113">Adiciona um comportamento à coleção.</span><span class="sxs-lookup"><span data-stu-id="20608-113">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20608-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="20608-114">Parent elements</span></span>

|<span data-ttu-id="20608-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="20608-115">Element</span></span>|<span data-ttu-id="20608-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="20608-116">Description</span></span>|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="20608-117">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="20608-117">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20608-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="20608-118">Remarks</span></span>

<span data-ttu-id="20608-119">Use este elemento quando quaisquer comportamentos (que não sejam os comportamentos que incluem `<clientCredentials>` elementos) devem ser usados para se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="20608-119">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="20608-120">Por exemplo, se um [\<dataContractSerializer>](datacontractserializer-element.md) elemento de comportamento deve ser incluído.</span><span class="sxs-lookup"><span data-stu-id="20608-120">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="20608-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="20608-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="20608-122">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="20608-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="20608-123">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="20608-123">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="20608-124">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="20608-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="20608-125">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="20608-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="20608-126">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="20608-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="20608-127">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="20608-127">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="20608-128">Como configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="20608-128">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="20608-129">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="20608-129">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
