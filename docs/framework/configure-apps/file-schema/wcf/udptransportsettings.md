---
title: '&lt;udpTransportSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88b38fc7c67c404446000ca79d2c6191bfc7eed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltudptransportsettingsgt"></a><span data-ttu-id="75fbd-102">&lt;udpTransportSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="75fbd-102">&lt;udpTransportSettings&gt;</span></span>
<span data-ttu-id="75fbd-103">Este elemento de configuração expõe configurações de transporte UDP para [ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).</span><span class="sxs-lookup"><span data-stu-id="75fbd-103">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).</span></span>  
  
<span data-ttu-id="75fbd-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="75fbd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="75fbd-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="75fbd-105">\<standardEndpoints></span></span>  
<span data-ttu-id="75fbd-106">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="75fbd-106">\<udpDiscoveryEndpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75fbd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75fbd-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer" 
                              maxBufferPoolSize="Integer" 
                              maxMulticastRetransmitCount="Integer" 
                              maxPendingMessageCount="Integer" 
                              maxReceivedMessageSize="Integer" 
                              maxUnicastRetransmitCount="Integer" 
                              multicastInterfaceId="String" 
                              socketReceiveBufferSize="Integer" 
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75fbd-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="75fbd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="75fbd-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="75fbd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75fbd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="75fbd-110">Attributes</span></span>  
  
|<span data-ttu-id="75fbd-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="75fbd-111">Attribute</span></span>|<span data-ttu-id="75fbd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="75fbd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75fbd-113">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="75fbd-113">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="75fbd-114">Um inteiro que especifica o número máximo de mensagens de hash usado pelo transporte para identificar mensagens duplicadas.</span><span class="sxs-lookup"><span data-stu-id="75fbd-114">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="75fbd-115">Detecção de duplicidades será feita no nível de TransportManager.</span><span class="sxs-lookup"><span data-stu-id="75fbd-115">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="75fbd-116">Definir essa propriedade como 0 desabilita a detecção de duplicidades.</span><span class="sxs-lookup"><span data-stu-id="75fbd-116">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="75fbd-117">Este atributo permite aos administradores de sistema ou desenvolvedores para desativar os algoritmos de detecção de mensagens duplicadas.</span><span class="sxs-lookup"><span data-stu-id="75fbd-117">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="75fbd-118">Isso pode ser desejável para implementar seu próprio algoritmo de detecção de duplicidades.</span><span class="sxs-lookup"><span data-stu-id="75fbd-118">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="75fbd-119">O padrão é 4112.</span><span class="sxs-lookup"><span data-stu-id="75fbd-119">The default is 4112.</span></span>|  
|<span data-ttu-id="75fbd-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="75fbd-120">maxBufferPoolSize</span></span>|<span data-ttu-id="75fbd-121">Um inteiro que especifica o tamanho máximo de qualquer pools de buffers usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="75fbd-121">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="75fbd-122">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="75fbd-122">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="75fbd-123">Um inteiro que especifica o número máximo de vezes que a mensagem deve ser retransmitida (além do primeiro envio).</span><span class="sxs-lookup"><span data-stu-id="75fbd-123">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="75fbd-124">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="75fbd-124">The default is 2.</span></span>|  
|<span data-ttu-id="75fbd-125">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="75fbd-125">maxPendingMessageCount</span></span>|<span data-ttu-id="75fbd-126">Um inteiro que especifica o número máximo de mensagens que foram recebidos, mas ainda não foram removidas do InputQueue para uma instância de canal individual.</span><span class="sxs-lookup"><span data-stu-id="75fbd-126">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="75fbd-127">Se o InputQueue atingiu seu limite de contagem de mensagens pendentes, a mensagem será descartada.</span><span class="sxs-lookup"><span data-stu-id="75fbd-127">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="75fbd-128">O padrão é 32.</span><span class="sxs-lookup"><span data-stu-id="75fbd-128">The default is 32.</span></span>|  
|<span data-ttu-id="75fbd-129">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="75fbd-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="75fbd-130">Um inteiro que especifica o tamanho máximo para uma mensagem que pode ser processada por meio da associação.</span><span class="sxs-lookup"><span data-stu-id="75fbd-130">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="75fbd-131">O valor padrão é 65507.</span><span class="sxs-lookup"><span data-stu-id="75fbd-131">The default value is 65507.</span></span>|  
|<span data-ttu-id="75fbd-132">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="75fbd-132">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="75fbd-133">Um inteiro que especifica o número máximo de vezes que a mensagem deve ser retransmitida (além do primeiro envio).</span><span class="sxs-lookup"><span data-stu-id="75fbd-133">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="75fbd-134">Se a mensagem é enviada a um endereço de unicast e uma mensagem de resposta é recebida com um cabeçalho RelatesTo correspondente, retransmissão pode terminar cedo (antes de retransmitir o número configurado de vezes).</span><span class="sxs-lookup"><span data-stu-id="75fbd-134">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="75fbd-135">O valor padrão é 1.</span><span class="sxs-lookup"><span data-stu-id="75fbd-135">The default value is 1.</span></span>|  
|<span data-ttu-id="75fbd-136">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="75fbd-136">multicastInterfaceId</span></span>|<span data-ttu-id="75fbd-137">Uma cadeia de caracteres que identifica exclusivamente o adaptador de rede que deve ser usado ao enviar e receber tráfego multicast em computadores multihomed.</span><span class="sxs-lookup"><span data-stu-id="75fbd-137">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="75fbd-138">Em tempo de execução, o transporte usará esse valor de atributo para pesquisar o índice de interface, que é usado para definir o `IP_MULTICAST_IF` e `IPV6_MULTICAST_IF` opções de soquete.</span><span class="sxs-lookup"><span data-stu-id="75fbd-138">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="75fbd-139">O mesmo índice será usado ao ingressar em um grupo de difusão seletiva, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="75fbd-139">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="75fbd-140">O valor padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="75fbd-140">The default value is `null`.</span></span>|  
|<span data-ttu-id="75fbd-141">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="75fbd-141">socketReceiveBufferSize</span></span>|<span data-ttu-id="75fbd-142">Um inteiro que especifica o tamanho do buffer de recebimento no soquete WinSock subjacente.</span><span class="sxs-lookup"><span data-stu-id="75fbd-142">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="75fbd-143">Um usuário de um canal de recebimento pode usar esse atributo na ligação para controlar como o sistema se comporta quando ele recebe dados.</span><span class="sxs-lookup"><span data-stu-id="75fbd-143">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="75fbd-144">Por exemplo, devido a um aplicativo que está consumindo entradas mensagens do WCF no limite máximo, usar um valor mais alto para esse atributo deve permitir que as mensagens empilhar no buffer de WinSock enquanto aguarda o aplicativo possa processá-los.</span><span class="sxs-lookup"><span data-stu-id="75fbd-144">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="75fbd-145">Usar um valor mais baixo na mesma situação pode resultar em mensagens sendo descartadas. Esse atributo expõe o WinSock subjacente `SO_RCVBUF` opção de soquete. O valor do atributo deve ser pelo menos o tamanho do `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="75fbd-145">Using a lower value in the same situation would result in messages getting dropped.This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="75fbd-146">Configurá-lo como um valor menor do que o `maxReceivedMessageSize` resultará na exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="75fbd-146">Setting it to a value smaller than the `maxReceivedMessageSize` will result in runtime exception.</span></span><br /><br /> <span data-ttu-id="75fbd-147">O valor padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="75fbd-147">The default value is 65536.</span></span>|  
|<span data-ttu-id="75fbd-148">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="75fbd-148">timeToLive</span></span>|<span data-ttu-id="75fbd-149">Um inteiro que especifica o número de saltos de segmento de rede que um pacote de multicast pode percorrer.</span><span class="sxs-lookup"><span data-stu-id="75fbd-149">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="75fbd-150">Esse atributo expõe a funcionalidade associada a `IP_MULTICAST_TTL` e `IP_TTL` opções de soquete.</span><span class="sxs-lookup"><span data-stu-id="75fbd-150">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="75fbd-151">O valor padrão é 1.</span><span class="sxs-lookup"><span data-stu-id="75fbd-151">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75fbd-152">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="75fbd-152">Child Elements</span></span>  
 <span data-ttu-id="75fbd-153">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="75fbd-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75fbd-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="75fbd-154">Parent Elements</span></span>  
  
|<span data-ttu-id="75fbd-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="75fbd-155">Element</span></span>|<span data-ttu-id="75fbd-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="75fbd-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75fbd-157">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="75fbd-157">\<udpDiscoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|<span data-ttu-id="75fbd-158">Um ponto de extremidade padrão que corrigiu descoberta de associação de transporte do contrato e UDP.</span><span class="sxs-lookup"><span data-stu-id="75fbd-158">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75fbd-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75fbd-159">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpTransportSettings>
