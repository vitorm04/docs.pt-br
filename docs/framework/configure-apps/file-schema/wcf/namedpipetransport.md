---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: e30fcd5952fadc3b6cf30cb352a3bb51c86cc117
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285891"
---
# <a name="namedpipetransport"></a><span data-ttu-id="c94cd-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="c94cd-101">\<namedPipeTransport></span></span>
<span data-ttu-id="c94cd-102">Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados quando ele é incluído em uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c94cd-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="c94cd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c94cd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c94cd-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c94cd-104">\<bindings></span></span>  
<span data-ttu-id="c94cd-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c94cd-105">\<customBinding></span></span>  
<span data-ttu-id="c94cd-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="c94cd-106">\<binding></span></span>  
<span data-ttu-id="c94cd-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="c94cd-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94cd-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c94cd-108">Syntax</span></span>  
  
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
                          maxOutboundConnectionsPerEndpopint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c94cd-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c94cd-109">Attributes and Elements</span></span>  
<span data-ttu-id="c94cd-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c94cd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c94cd-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c94cd-111">Attributes</span></span>  
<span data-ttu-id="c94cd-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c94cd-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c94cd-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c94cd-113">Child Elements</span></span>  
  
|<span data-ttu-id="c94cd-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c94cd-114">Element</span></span>|<span data-ttu-id="c94cd-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c94cd-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c94cd-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="c94cd-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="c94cd-117">Obtém ou define um <xref:System.TimeSpan> que determina o tempo máximo que um canal pode estar com o status de inicialização antes de ser desconectado.</span><span class="sxs-lookup"><span data-stu-id="c94cd-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="c94cd-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="c94cd-118">ConnectionBufferSize</span></span>|<span data-ttu-id="c94cd-119">Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="c94cd-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="c94cd-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c94cd-120">hostNameComparisonMode</span></span>|<span data-ttu-id="c94cd-121">Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="c94cd-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="c94cd-122">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="c94cd-122">manualAddressing</span></span>|<span data-ttu-id="c94cd-123">Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.</span><span class="sxs-lookup"><span data-stu-id="c94cd-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="c94cd-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c94cd-124">maxBufferPoolSize</span></span>|<span data-ttu-id="c94cd-125">Obtém ou define o tamanho máximo, em bytes, de qualquer pool de buffer usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="c94cd-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="c94cd-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="c94cd-126">maxBufferSize</span></span>|<span data-ttu-id="c94cd-127">Obtém ou define o tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c94cd-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="c94cd-128">Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.</span><span class="sxs-lookup"><span data-stu-id="c94cd-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="c94cd-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="c94cd-129">maxOutputDelay</span></span>|<span data-ttu-id="c94cd-130">Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="c94cd-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="c94cd-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="c94cd-131">maxPendingAccepts</span></span>|<span data-ttu-id="c94cd-132">Obtém ou define o número máximo de canais que um serviço pode ter aguardando um ouvinte para processar conexões de entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="c94cd-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="c94cd-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="c94cd-133">maxPendingConnections</span></span>|<span data-ttu-id="c94cd-134">Obtém ou define o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="c94cd-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="c94cd-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c94cd-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="c94cd-136">Obtém e define o tamanho de mensagem máximo permitido, em bytes, que pode ser recebido.</span><span class="sxs-lookup"><span data-stu-id="c94cd-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="c94cd-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="c94cd-137">transferMode</span></span>|<span data-ttu-id="c94cd-138">Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="c94cd-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="c94cd-139">\<connectionPoolSettings > de \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="c94cd-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="c94cd-140">Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="c94cd-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c94cd-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c94cd-141">Parent Elements</span></span>  
  
|<span data-ttu-id="c94cd-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="c94cd-142">Element</span></span>|<span data-ttu-id="c94cd-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="c94cd-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c94cd-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="c94cd-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c94cd-145">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c94cd-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c94cd-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="c94cd-146">Remarks</span></span>  
<span data-ttu-id="c94cd-147">Esse transporte usa URIs do formulário "net.pipe://hostname/path".</span><span class="sxs-lookup"><span data-stu-id="c94cd-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="c94cd-148">Outros componentes do URI são opcionais.</span><span class="sxs-lookup"><span data-stu-id="c94cd-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="c94cd-149">O `namedPipeTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte de pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="c94cd-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="c94cd-150">Esse transporte é usada para em computadores Windows Communication Foundation (WCF) - para - comunicação WCF.</span><span class="sxs-lookup"><span data-stu-id="c94cd-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94cd-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c94cd-151">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c94cd-152">Transportes</span><span class="sxs-lookup"><span data-stu-id="c94cd-152">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="c94cd-153">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="c94cd-153">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="c94cd-154">Associações</span><span class="sxs-lookup"><span data-stu-id="c94cd-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c94cd-155">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="c94cd-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c94cd-156">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c94cd-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c94cd-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c94cd-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
