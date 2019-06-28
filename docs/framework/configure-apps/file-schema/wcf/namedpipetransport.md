---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 819639eabf0332a34d6a7250159d24e42552f874
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423098"
---
# <a name="namedpipetransport"></a><span data-ttu-id="d7460-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="d7460-101">\<namedPipeTransport></span></span>
<span data-ttu-id="d7460-102">Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados quando ele é incluído em uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d7460-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="d7460-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d7460-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d7460-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d7460-104">\<bindings></span></span>  
<span data-ttu-id="d7460-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d7460-105">\<customBinding></span></span>  
<span data-ttu-id="d7460-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="d7460-106">\<binding></span></span>  
<span data-ttu-id="d7460-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="d7460-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7460-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7460-108">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7460-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7460-109">Attributes and Elements</span></span>  
<span data-ttu-id="d7460-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7460-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7460-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7460-111">Attributes</span></span>  
<span data-ttu-id="d7460-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d7460-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7460-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7460-113">Child Elements</span></span>  
  
|<span data-ttu-id="d7460-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7460-114">Element</span></span>|<span data-ttu-id="d7460-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7460-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7460-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="d7460-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="d7460-117">Obtém ou define um <xref:System.TimeSpan> que determina o tempo máximo que um canal pode estar com o status de inicialização antes de ser desconectado.</span><span class="sxs-lookup"><span data-stu-id="d7460-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="d7460-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="d7460-118">ConnectionBufferSize</span></span>|<span data-ttu-id="d7460-119">Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="d7460-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="d7460-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="d7460-120">hostNameComparisonMode</span></span>|<span data-ttu-id="d7460-121">Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="d7460-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="d7460-122">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="d7460-122">manualAddressing</span></span>|<span data-ttu-id="d7460-123">Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.</span><span class="sxs-lookup"><span data-stu-id="d7460-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="d7460-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="d7460-124">maxBufferPoolSize</span></span>|<span data-ttu-id="d7460-125">Obtém ou define o tamanho máximo, em bytes, de qualquer pool de buffer usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="d7460-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="d7460-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="d7460-126">maxBufferSize</span></span>|<span data-ttu-id="d7460-127">Obtém ou define o tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d7460-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="d7460-128">Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.</span><span class="sxs-lookup"><span data-stu-id="d7460-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="d7460-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="d7460-129">maxOutputDelay</span></span>|<span data-ttu-id="d7460-130">Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="d7460-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="d7460-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="d7460-131">maxPendingAccepts</span></span>|<span data-ttu-id="d7460-132">Obtém ou define o número máximo de canais que um serviço pode ter aguardando um ouvinte para processar conexões de entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="d7460-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="d7460-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="d7460-133">maxPendingConnections</span></span>|<span data-ttu-id="d7460-134">Obtém ou define o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="d7460-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="d7460-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="d7460-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="d7460-136">Obtém e define o tamanho de mensagem máximo permitido, em bytes, que pode ser recebido.</span><span class="sxs-lookup"><span data-stu-id="d7460-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="d7460-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="d7460-137">transferMode</span></span>|<span data-ttu-id="d7460-138">Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="d7460-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="d7460-139">\<connectionPoolSettings > de \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="d7460-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="d7460-140">Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="d7460-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7460-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7460-141">Parent Elements</span></span>  
  
|<span data-ttu-id="d7460-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7460-142">Element</span></span>|<span data-ttu-id="d7460-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7460-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7460-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="d7460-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d7460-145">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d7460-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7460-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7460-146">Remarks</span></span>  
<span data-ttu-id="d7460-147">Esse transporte usa URIs do formulário "net.pipe://hostname/path".</span><span class="sxs-lookup"><span data-stu-id="d7460-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="d7460-148">Outros componentes do URI são opcionais.</span><span class="sxs-lookup"><span data-stu-id="d7460-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="d7460-149">O `namedPipeTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte de pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="d7460-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="d7460-150">Esse transporte é usada para em computadores Windows Communication Foundation (WCF) - para - comunicação WCF.</span><span class="sxs-lookup"><span data-stu-id="d7460-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7460-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7460-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d7460-152">Transportes</span><span class="sxs-lookup"><span data-stu-id="d7460-152">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="d7460-153">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="d7460-153">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d7460-154">Associações</span><span class="sxs-lookup"><span data-stu-id="d7460-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d7460-155">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="d7460-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d7460-156">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d7460-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d7460-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d7460-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
