---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: a982fa87ab84725e36ee913f00200cd34f0b8f6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925571"
---
# <a name="headers"></a><span data-ttu-id="baef5-101">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="baef5-101">\<headers></span></span>
<span data-ttu-id="baef5-102">Um ponto de extremidade pode ser resolvido por um ou mais cabeçalhos SOAP além de seu URI básico.</span><span class="sxs-lookup"><span data-stu-id="baef5-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="baef5-103">Um conjunto de cenários em que isso é útil é um conjunto de cenários intermediários de SOAP em que um ponto de extremidade exige que clientes desse ponto de extremidade incluam cabeçalhos SOAP direcionados a intermediários.</span><span class="sxs-lookup"><span data-stu-id="baef5-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="baef5-104">Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizados.</span><span class="sxs-lookup"><span data-stu-id="baef5-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="baef5-105">As entradas na coleção de cabeçalhos do ponto de extremidade são elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="baef5-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="baef5-106">Cada elemento deve ser um XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="baef5-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="baef5-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="baef5-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="baef5-108">\<client></span><span class="sxs-lookup"><span data-stu-id="baef5-108">\<client></span></span>  
<span data-ttu-id="baef5-109">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="baef5-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baef5-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="baef5-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baef5-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="baef5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="baef5-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="baef5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baef5-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="baef5-113">Attributes</span></span>  
 <span data-ttu-id="baef5-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="baef5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="baef5-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="baef5-115">Child Elements</span></span>  
 <span data-ttu-id="baef5-116">Elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="baef5-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="baef5-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="baef5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="baef5-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="baef5-118">Element</span></span>|<span data-ttu-id="baef5-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="baef5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baef5-120">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="baef5-120">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="baef5-121">Configura tipos diferentes de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="baef5-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baef5-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="baef5-122">Remarks</span></span>  
 <span data-ttu-id="baef5-123">Os cabeçalhos opcionais fornecem informações de endereçamento mais detalhadas para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="baef5-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="baef5-124">Por exemplo, os cabeçalhos podem indicar como processar uma mensagem de entrada, em que o ponto de extremidade deve enviar uma mensagem de resposta ou qual instância de um serviço usar para processar uma mensagem de entrada de um usuário específico quando várias instâncias estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="baef5-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baef5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baef5-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="baef5-126">Extremidade Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="baef5-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
