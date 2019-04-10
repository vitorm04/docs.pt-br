---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 660497012dd057e4ecf95524833e2573fe03a8b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224540"
---
# <a name="headers"></a><span data-ttu-id="9aae2-101">\<headers></span><span class="sxs-lookup"><span data-stu-id="9aae2-101">\<headers></span></span>
<span data-ttu-id="9aae2-102">Um ponto de extremidade pode ser tratado por um ou mais cabeçalhos SOAP, além de seu URI básico.</span><span class="sxs-lookup"><span data-stu-id="9aae2-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="9aae2-103">Um conjunto de cenários em que isso é útil é um conjunto de cenários de intermediários SOAP em que um ponto de extremidade requer que os clientes desse ponto de extremidade incluir os cabeçalhos SOAP destinados a intermediários.</span><span class="sxs-lookup"><span data-stu-id="9aae2-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="9aae2-104">Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizado.</span><span class="sxs-lookup"><span data-stu-id="9aae2-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="9aae2-105">As entradas na coleção de cabeçalho do ponto de extremidade são os elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9aae2-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="9aae2-106">Cada elemento tem que ser bem formada XML.</span><span class="sxs-lookup"><span data-stu-id="9aae2-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="9aae2-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9aae2-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="9aae2-108">\<client></span><span class="sxs-lookup"><span data-stu-id="9aae2-108">\<client></span></span>  
<span data-ttu-id="9aae2-109">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="9aae2-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aae2-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9aae2-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9aae2-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9aae2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9aae2-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9aae2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9aae2-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="9aae2-113">Attributes</span></span>  
 <span data-ttu-id="9aae2-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9aae2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9aae2-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9aae2-115">Child Elements</span></span>  
 <span data-ttu-id="9aae2-116">Elementos XML definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9aae2-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9aae2-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9aae2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9aae2-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9aae2-118">Element</span></span>|<span data-ttu-id="9aae2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9aae2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9aae2-120">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="9aae2-120">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="9aae2-121">Configura os diferentes tipos de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9aae2-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aae2-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9aae2-122">Remarks</span></span>  
 <span data-ttu-id="9aae2-123">Os cabeçalhos opcionais fornecem informações mais detalhadas de endereçamento para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9aae2-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="9aae2-124">Por exemplo, os cabeçalhos podem indicar qual instância de um serviço para usar para processar uma mensagem de entrada de um determinado usuário, quando várias instâncias estiverem disponíveis, onde o ponto de extremidade deve enviar uma mensagem de resposta ou como processar uma mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="9aae2-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aae2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9aae2-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="9aae2-126">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="9aae2-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
