---
title: Elemento <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: e0e41b4f6d66cd4455c43dda7c77798553f2b58f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929936"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="b206e-102">\<Elemento de > issuerChannelBehaviors</span><span class="sxs-lookup"><span data-stu-id="b206e-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="b206e-103">Contém uma coleção de comportamentos de ponto de extremidade de cliente do Windows Communication Foundation (WCF) (definida na configuração) a ser usada na comunicação com os serviços de token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="b206e-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="b206e-104">Os comportamentos definidos não podem incluir [ \<ClientCredentials >](clientcredentials.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="b206e-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="b206e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b206e-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b206e-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b206e-106">Attributes and Elements</span></span>

<span data-ttu-id="b206e-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b206e-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b206e-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="b206e-108">Attributes</span></span>

<span data-ttu-id="b206e-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b206e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b206e-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b206e-110">Child Elements</span></span>

|<span data-ttu-id="b206e-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="b206e-111">Element</span></span>|<span data-ttu-id="b206e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b206e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b206e-113">\<add></span><span class="sxs-lookup"><span data-stu-id="b206e-113">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="b206e-114">Adiciona um comportamento à coleção.</span><span class="sxs-lookup"><span data-stu-id="b206e-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b206e-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b206e-115">Parent Elements</span></span>

|<span data-ttu-id="b206e-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="b206e-116">Element</span></span>|<span data-ttu-id="b206e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b206e-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b206e-118">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="b206e-118">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="b206e-119">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b206e-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b206e-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="b206e-120">Remarks</span></span>

<span data-ttu-id="b206e-121">Use este elemento quando quaisquer comportamentos (que não sejam os comportamentos `<clientCredentials>` que incluem elementos) devem ser usados para se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="b206e-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="b206e-122">Por exemplo, se um elemento de comportamento de [ \<> do DataContractSerializer](datacontractserializer-element.md) precisar ser incluído.</span><span class="sxs-lookup"><span data-stu-id="b206e-122">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="b206e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b206e-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="b206e-124">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="b206e-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b206e-125">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b206e-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b206e-126">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b206e-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b206e-127">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b206e-127">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b206e-128">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="b206e-128">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b206e-129">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="b206e-129">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="b206e-130">Como: Configurar um emissor local</span><span class="sxs-lookup"><span data-stu-id="b206e-130">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="b206e-131">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b206e-131">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
