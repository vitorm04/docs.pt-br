---
title: Elemento &lt;issuerChannelBehaviors&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 051525738f0138955358587a8fd25272dfdb9d28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="29634-102">Elemento &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="29634-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="29634-103">Contém uma coleção de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] comportamentos de ponto de extremidade do cliente (definidos na configuração) a ser usado ao se comunicar com os serviços de Token de serviço especificado.</span><span class="sxs-lookup"><span data-stu-id="29634-103">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="29634-104">Os comportamentos definidos não podem incluir nenhum [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="29634-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="29634-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="29634-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="29634-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="29634-106">\<behaviors></span></span>  
<span data-ttu-id="29634-107">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="29634-107">endpointBehaviors section</span></span>  
<span data-ttu-id="29634-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="29634-108">\<behavior></span></span>  
<span data-ttu-id="29634-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="29634-109">\<clientCredentials></span></span>  
<span data-ttu-id="29634-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="29634-110">\<issuedToken></span></span>  
<span data-ttu-id="29634-111">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="29634-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29634-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29634-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29634-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="29634-113">Attributes and Elements</span></span>  
 <span data-ttu-id="29634-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="29634-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29634-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="29634-115">Attributes</span></span>  
 <span data-ttu-id="29634-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="29634-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29634-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="29634-117">Child Elements</span></span>  
  
|<span data-ttu-id="29634-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="29634-118">Element</span></span>|<span data-ttu-id="29634-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="29634-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29634-120">\<add></span><span class="sxs-lookup"><span data-stu-id="29634-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="29634-121">Adiciona um comportamento à coleção.</span><span class="sxs-lookup"><span data-stu-id="29634-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29634-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="29634-122">Parent Elements</span></span>  
  
|<span data-ttu-id="29634-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="29634-123">Element</span></span>|<span data-ttu-id="29634-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="29634-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29634-125">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="29634-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="29634-126">Especifica um token personalizado usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="29634-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29634-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="29634-127">Remarks</span></span>  
 <span data-ttu-id="29634-128">Use esse elemento quando qualquer comportamentos (diferente de comportamentos que incluem `<clientCredentials>` elementos) deve ser usado para se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="29634-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="29634-129">Por exemplo, se um [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) elemento de comportamento deve ser incluído.</span><span class="sxs-lookup"><span data-stu-id="29634-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29634-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29634-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="29634-131">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="29634-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="29634-132">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="29634-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="29634-133">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="29634-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="29634-134">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="29634-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="29634-135">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)</span><span class="sxs-lookup"><span data-stu-id="29634-135">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md)</span></span>  
 [<span data-ttu-id="29634-136">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="29634-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="29634-137">Como: configurar um emissor Local</span><span class="sxs-lookup"><span data-stu-id="29634-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="29634-138">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="29634-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
