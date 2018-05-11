---
title: '&lt;adicionar&gt; &lt;issuerChannelBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 75531e8ed50ae89f379db23d228804612f4bfccb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="cc802-102">&lt;adicionar&gt; &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="cc802-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="cc802-103">Adiciona um comportamento de ponto de extremidade a ser usado ao se comunicar com um STS.</span><span class="sxs-lookup"><span data-stu-id="cc802-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc802-104">Se qualquer comportamento de ponto de extremidade contém um [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="cc802-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="cc802-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cc802-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc802-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="cc802-106">\<behaviors></span></span>  
<span data-ttu-id="cc802-107">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="cc802-107">endpointBehaviors section</span></span>  
<span data-ttu-id="cc802-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="cc802-108">\<behavior></span></span>  
<span data-ttu-id="cc802-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="cc802-109">\<clientCredentials></span></span>  
<span data-ttu-id="cc802-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="cc802-110">\<issuedToken></span></span>  
<span data-ttu-id="cc802-111">\<issuerChannelBehaviors > elemento</span><span class="sxs-lookup"><span data-stu-id="cc802-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="cc802-112">\<add></span><span class="sxs-lookup"><span data-stu-id="cc802-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc802-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc802-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc802-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cc802-114">Attributes and Elements</span></span>  
 <span data-ttu-id="cc802-115">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="cc802-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc802-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="cc802-116">Attributes</span></span>  
  
|<span data-ttu-id="cc802-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="cc802-117">Attribute</span></span>|<span data-ttu-id="cc802-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc802-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc802-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="cc802-119">issuerAddress</span></span>|<span data-ttu-id="cc802-120">O URI do emissor do token de segurança para se comunicar com.</span><span class="sxs-lookup"><span data-stu-id="cc802-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="cc802-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc802-121">behaviorConfiguration</span></span>|<span data-ttu-id="cc802-122">O nome de um comportamento de ponto de extremidade definido no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cc802-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc802-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cc802-123">Child Elements</span></span>  
 <span data-ttu-id="cc802-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cc802-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc802-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cc802-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cc802-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc802-126">Element</span></span>|<span data-ttu-id="cc802-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc802-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc802-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cc802-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="cc802-129">Contém uma coleção de comportamentos de ponto de extremidade de cliente do Windows Communication Foundation (WCF) a ser usado ao se comunicar com os serviços de Token de serviço especificado.</span><span class="sxs-lookup"><span data-stu-id="cc802-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc802-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc802-130">Remarks</span></span>  
 <span data-ttu-id="cc802-131">`issuerAddress` contém o URI do serviço de Token de segurança que o cliente deseja se comunicar com.</span><span class="sxs-lookup"><span data-stu-id="cc802-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="cc802-132">`behaviorConfiguration` aponta para um comportamento de ponto de extremidade que o aplicativo usa os canais criados pelo Windows Communication Foundation (WCF) para obter os tokens emitidos de serviços de Token de segurança.</span><span class="sxs-lookup"><span data-stu-id="cc802-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc802-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc802-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="cc802-134">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="cc802-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="cc802-135">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="cc802-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="cc802-136">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="cc802-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="cc802-137">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="cc802-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cc802-138">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="cc802-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="cc802-139">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="cc802-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="cc802-140">Como configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="cc802-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="cc802-141">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="cc802-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="cc802-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cc802-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
