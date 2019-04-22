---
title: Elemento <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7cbd50daa82b0ca937a1bba93786545898b03c8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890469"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="d6ff9-102">\<issuerChannelBehaviors > elemento</span><span class="sxs-lookup"><span data-stu-id="d6ff9-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="d6ff9-103">Contém uma coleção de comportamentos de ponto de extremidade do cliente do Windows Communication Foundation (WCF) (definido na configuração) para ser usado ao se comunicar com os serviços de Token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="d6ff9-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="d6ff9-104">Os comportamentos definidos não podem incluir nenhum [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="d6ff9-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="d6ff9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6ff9-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d6ff9-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d6ff9-106">Attributes and Elements</span></span>

<span data-ttu-id="d6ff9-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d6ff9-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d6ff9-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6ff9-108">Attributes</span></span>

<span data-ttu-id="d6ff9-109">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d6ff9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d6ff9-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d6ff9-110">Child Elements</span></span>

|<span data-ttu-id="d6ff9-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6ff9-111">Element</span></span>|<span data-ttu-id="d6ff9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6ff9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6ff9-113">\<add></span><span class="sxs-lookup"><span data-stu-id="d6ff9-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="d6ff9-114">Adiciona um comportamento à coleção.</span><span class="sxs-lookup"><span data-stu-id="d6ff9-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d6ff9-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d6ff9-115">Parent Elements</span></span>

|<span data-ttu-id="d6ff9-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6ff9-116">Element</span></span>|<span data-ttu-id="d6ff9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6ff9-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6ff9-118">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="d6ff9-118">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="d6ff9-119">Especifica um token personalizado usado para autenticar um cliente a um serviço.</span><span class="sxs-lookup"><span data-stu-id="d6ff9-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d6ff9-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6ff9-120">Remarks</span></span>

<span data-ttu-id="d6ff9-121">Use esse elemento quando qualquer comportamentos (diferente de comportamentos que incluem `<clientCredentials>` elementos) deve ser usado para se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="d6ff9-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="d6ff9-122">Por exemplo, se um [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) elemento de comportamento deve ser incluído.</span><span class="sxs-lookup"><span data-stu-id="d6ff9-122">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6ff9-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6ff9-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="d6ff9-124">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="d6ff9-124">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d6ff9-125">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="d6ff9-125">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d6ff9-126">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d6ff9-126">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d6ff9-127">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d6ff9-127">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d6ff9-128">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="d6ff9-128">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="d6ff9-129">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="d6ff9-129">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d6ff9-130">Como: Configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="d6ff9-130">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="d6ff9-131">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d6ff9-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
