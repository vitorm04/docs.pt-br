---
title: '&lt;Cabeçalhos&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 84b9a9437d4b0dfae72a6e625b21f2b830eb28d8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147857"
---
# <a name="ltheadersgt"></a><span data-ttu-id="c0575-102">&lt;Cabeçalhos&gt;</span><span class="sxs-lookup"><span data-stu-id="c0575-102">&lt;headers&gt;</span></span>
<span data-ttu-id="c0575-103">Um ponto de extremidade pode ser tratado por um ou mais cabeçalhos SOAP, além de seu URI básico.</span><span class="sxs-lookup"><span data-stu-id="c0575-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="c0575-104">Um conjunto de cenários em que isso é útil é um conjunto de cenários de intermediários SOAP em que um ponto de extremidade requer que os clientes desse ponto de extremidade incluir os cabeçalhos SOAP destinados a intermediários.</span><span class="sxs-lookup"><span data-stu-id="c0575-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="c0575-105">Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizado.</span><span class="sxs-lookup"><span data-stu-id="c0575-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="c0575-106">As entradas na coleção de cabeçalho do ponto de extremidade são os elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c0575-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="c0575-107">Cada elemento tem que ser bem formada XML.</span><span class="sxs-lookup"><span data-stu-id="c0575-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="c0575-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c0575-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="c0575-109">\<client></span><span class="sxs-lookup"><span data-stu-id="c0575-109">\<client></span></span>  
<span data-ttu-id="c0575-110">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="c0575-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0575-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0575-111">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0575-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0575-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c0575-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c0575-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0575-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0575-114">Attributes</span></span>  
 <span data-ttu-id="c0575-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c0575-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0575-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0575-116">Child Elements</span></span>  
  
|<span data-ttu-id="c0575-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0575-117">Element</span></span>|<span data-ttu-id="c0575-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0575-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0575-119">Região</span><span class="sxs-lookup"><span data-stu-id="c0575-119">Region</span></span>||  
|<span data-ttu-id="c0575-120">Membro</span><span class="sxs-lookup"><span data-stu-id="c0575-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="c0575-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0575-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c0575-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0575-122">Element</span></span>|<span data-ttu-id="c0575-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0575-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0575-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="c0575-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="c0575-125">Configura os diferentes tipos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c0575-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0575-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0575-126">Remarks</span></span>  
 <span data-ttu-id="c0575-127">Os cabeçalhos opcionais fornecem informações mais detalhadas de endereçamento para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c0575-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="c0575-128">Por exemplo, os cabeçalhos podem indicar qual instância de um serviço para usar para processar uma mensagem de entrada de um determinado usuário, quando várias instâncias estiverem disponíveis, onde o ponto de extremidade deve enviar uma mensagem de resposta ou como processar uma mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0575-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0575-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0575-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="c0575-130">Pontos de extremidade: Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="c0575-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
