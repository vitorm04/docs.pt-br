---
title: <add> De <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 65c76cba696ae388d6184eaaa70a1f2f5a301e1c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271782"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="e5252-102">\<Adicionar > de \<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e5252-102">\<add> of \<issuerChannelBehaviors></span></span>
<span data-ttu-id="e5252-103">Adiciona um comportamento de ponto de extremidade a ser usado ao se comunicar com um STS.</span><span class="sxs-lookup"><span data-stu-id="e5252-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5252-104">Se qualquer comportamento de ponto de extremidade contém um [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="e5252-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="e5252-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e5252-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5252-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="e5252-106">\<behaviors></span></span>  
<span data-ttu-id="e5252-107">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="e5252-107">endpointBehaviors section</span></span>  
<span data-ttu-id="e5252-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e5252-108">\<behavior></span></span>  
<span data-ttu-id="e5252-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e5252-109">\<clientCredentials></span></span>  
<span data-ttu-id="e5252-110">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="e5252-110">\<issuedToken></span></span>  
<span data-ttu-id="e5252-111">\<issuerChannelBehaviors > elemento</span><span class="sxs-lookup"><span data-stu-id="e5252-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="e5252-112">\<add></span><span class="sxs-lookup"><span data-stu-id="e5252-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5252-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5252-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"
     behaviorConfiguraton="string" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5252-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e5252-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e5252-115">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="e5252-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5252-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="e5252-116">Attributes</span></span>  
  
|<span data-ttu-id="e5252-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="e5252-117">Attribute</span></span>|<span data-ttu-id="e5252-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5252-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5252-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="e5252-119">issuerAddress</span></span>|<span data-ttu-id="e5252-120">O URI do emissor do token de segurança para se comunicar com.</span><span class="sxs-lookup"><span data-stu-id="e5252-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="e5252-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5252-121">behaviorConfiguration</span></span>|<span data-ttu-id="e5252-122">O nome de um comportamento de ponto de extremidade definido no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e5252-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5252-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e5252-123">Child Elements</span></span>  
 <span data-ttu-id="e5252-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e5252-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5252-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e5252-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e5252-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5252-126">Element</span></span>|<span data-ttu-id="e5252-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5252-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5252-128">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="e5252-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="e5252-129">Contém uma coleção de comportamentos de ponto de extremidade do cliente Windows Communication Foundation (WCF) a ser usado ao se comunicar com os serviços de Token de serviço especificados.</span><span class="sxs-lookup"><span data-stu-id="e5252-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5252-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5252-130">Remarks</span></span>  
 <span data-ttu-id="e5252-131">`issuerAddress` contém o URI do serviço de Token de segurança que o cliente quer se comunicar com.</span><span class="sxs-lookup"><span data-stu-id="e5252-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="e5252-132">`behaviorConfiguration` aponta para um comportamento de ponto de extremidade que o aplicativo usa nos canais criados pelo Windows Communication Foundation (WCF) para obter os tokens emitidos de serviços de Token de segurança.</span><span class="sxs-lookup"><span data-stu-id="e5252-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5252-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5252-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="e5252-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="e5252-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e5252-135">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="e5252-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e5252-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="e5252-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e5252-137">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e5252-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e5252-138">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="e5252-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="e5252-139">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="e5252-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="e5252-140">Como: Configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="e5252-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="e5252-141">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="e5252-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e5252-142">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="e5252-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
