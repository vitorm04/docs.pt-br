---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855175"
---
# <a name="headers"></a><span data-ttu-id="0fe86-101">\<cabeçalhos ></span><span class="sxs-lookup"><span data-stu-id="0fe86-101">\<headers></span></span>
<span data-ttu-id="0fe86-102">Um ponto de extremidade pode ser resolvido por um ou mais cabeçalhos SOAP além de seu URI básico.</span><span class="sxs-lookup"><span data-stu-id="0fe86-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="0fe86-103">Um conjunto de cenários em que isso é útil é um conjunto de cenários intermediários de SOAP em que um ponto de extremidade exige que clientes desse ponto de extremidade incluam cabeçalhos SOAP direcionados a intermediários.</span><span class="sxs-lookup"><span data-stu-id="0fe86-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="0fe86-104">Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizados.</span><span class="sxs-lookup"><span data-stu-id="0fe86-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="0fe86-105">As entradas na coleção de cabeçalhos do ponto de extremidade são elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0fe86-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="0fe86-106">Cada elemento deve ser um XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="0fe86-106">Each element has to be well-formed XML.</span></span>  
  
<span data-ttu-id="0fe86-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fe86-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0fe86-108">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0fe86-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0fe86-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="0fe86-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="0fe86-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do ponto de extremidade**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="0fe86-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="0fe86-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cabeçalhos >**</span><span class="sxs-lookup"><span data-stu-id="0fe86-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe86-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fe86-112">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fe86-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0fe86-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0fe86-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0fe86-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fe86-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="0fe86-115">Attributes</span></span>  
 <span data-ttu-id="0fe86-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0fe86-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fe86-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0fe86-117">Child Elements</span></span>  
 <span data-ttu-id="0fe86-118">Elementos XML definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0fe86-118">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fe86-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0fe86-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0fe86-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="0fe86-120">Element</span></span>|<span data-ttu-id="0fe86-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fe86-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fe86-122">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="0fe86-122">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="0fe86-123">Configura tipos diferentes de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0fe86-123">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fe86-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="0fe86-124">Remarks</span></span>  
 <span data-ttu-id="0fe86-125">Os cabeçalhos opcionais fornecem informações de endereçamento mais detalhadas para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0fe86-125">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="0fe86-126">Por exemplo, os cabeçalhos podem indicar como processar uma mensagem de entrada, em que o ponto de extremidade deve enviar uma mensagem de resposta ou qual instância de um serviço usar para processar uma mensagem de entrada de um usuário específico quando várias instâncias estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0fe86-126">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe86-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fe86-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="0fe86-128">Extremidade Endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="0fe86-128">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
