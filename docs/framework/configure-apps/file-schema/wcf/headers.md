---
title: '&lt;headers&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: f47462ba63b9bd8868420ee9d3a320ba18c83c65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557819"
---
# <a name="ltheadersgt"></a><span data-ttu-id="2a7a2-102">&lt;headers&gt;</span><span class="sxs-lookup"><span data-stu-id="2a7a2-102">&lt;headers&gt;</span></span>
<span data-ttu-id="2a7a2-103">Um ponto de extremidade pode ser tratado por um ou mais cabeçalhos SOAP, além de seu URI básico.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="2a7a2-104">Um conjunto de cenários em que isso é útil é um conjunto de cenários de intermediários SOAP em que um ponto de extremidade requer que os clientes desse ponto de extremidade incluir os cabeçalhos SOAP destinados a intermediários.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="2a7a2-105">Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizado.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="2a7a2-106">As entradas na coleção de cabeçalho do ponto de extremidade são os elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="2a7a2-107">Cada elemento tem que ser bem formada XML.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="2a7a2-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a7a2-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a7a2-109">\<client></span><span class="sxs-lookup"><span data-stu-id="2a7a2-109">\<client></span></span>  
<span data-ttu-id="2a7a2-110">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2a7a2-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a7a2-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a7a2-111">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a7a2-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a7a2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2a7a2-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a7a2-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a7a2-114">Attributes</span></span>  
 <span data-ttu-id="2a7a2-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2a7a2-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a7a2-116">Child Elements</span></span>  
 <span data-ttu-id="2a7a2-117">Elementos XML definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-117">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a7a2-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a7a2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2a7a2-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a7a2-119">Element</span></span>|<span data-ttu-id="2a7a2-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a7a2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a7a2-121">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2a7a2-121">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="2a7a2-122">Configura os diferentes tipos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-122">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a7a2-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a7a2-123">Remarks</span></span>  
 <span data-ttu-id="2a7a2-124">Os cabeçalhos opcionais fornecem informações mais detalhadas de endereçamento para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-124">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="2a7a2-125">Por exemplo, os cabeçalhos podem indicar qual instância de um serviço para usar para processar uma mensagem de entrada de um determinado usuário, quando várias instâncias estiverem disponíveis, onde o ponto de extremidade deve enviar uma mensagem de resposta ou como processar uma mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="2a7a2-125">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7a2-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a7a2-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="2a7a2-127">Pontos de extremidade: Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="2a7a2-127">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
