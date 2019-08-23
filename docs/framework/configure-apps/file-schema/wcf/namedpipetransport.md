---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 473d0fbd543a056ec2b152f43a76a0417a18016f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933200"
---
# <a name="namedpipetransport"></a><span data-ttu-id="56ea3-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="56ea3-101">\<namedPipeTransport></span></span>
<span data-ttu-id="56ea3-102">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados quando ele é incluído em uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="56ea3-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="56ea3-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="56ea3-103">\<system.serviceModel></span></span>  
<span data-ttu-id="56ea3-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="56ea3-104">\<bindings></span></span>  
<span data-ttu-id="56ea3-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="56ea3-105">\<customBinding></span></span>  
<span data-ttu-id="56ea3-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="56ea3-106">\<binding></span></span>  
<span data-ttu-id="56ea3-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="56ea3-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ea3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56ea3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56ea3-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="56ea3-109">Attributes and Elements</span></span>  
<span data-ttu-id="56ea3-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="56ea3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56ea3-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="56ea3-111">Attributes</span></span>  
<span data-ttu-id="56ea3-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="56ea3-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="56ea3-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="56ea3-113">Child Elements</span></span>  
  
|<span data-ttu-id="56ea3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="56ea3-114">Element</span></span>|<span data-ttu-id="56ea3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="56ea3-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56ea3-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="56ea3-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="56ea3-117">Obtém ou define um <xref:System.TimeSpan> que determina o tempo máximo que um canal pode estar com o status de inicialização antes de ser desconectado.</span><span class="sxs-lookup"><span data-stu-id="56ea3-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="56ea3-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="56ea3-118">ConnectionBufferSize</span></span>|<span data-ttu-id="56ea3-119">Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="56ea3-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="56ea3-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="56ea3-120">hostNameComparisonMode</span></span>|<span data-ttu-id="56ea3-121">Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="56ea3-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="56ea3-122">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="56ea3-122">manualAddressing</span></span>|<span data-ttu-id="56ea3-123">Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.</span><span class="sxs-lookup"><span data-stu-id="56ea3-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="56ea3-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="56ea3-124">maxBufferPoolSize</span></span>|<span data-ttu-id="56ea3-125">Obtém ou define o tamanho máximo, em bytes, de qualquer pool de buffer usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="56ea3-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="56ea3-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="56ea3-126">maxBufferSize</span></span>|<span data-ttu-id="56ea3-127">Obtém ou define o tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="56ea3-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="56ea3-128">Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.</span><span class="sxs-lookup"><span data-stu-id="56ea3-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="56ea3-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="56ea3-129">maxOutputDelay</span></span>|<span data-ttu-id="56ea3-130">Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="56ea3-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="56ea3-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="56ea3-131">maxPendingAccepts</span></span>|<span data-ttu-id="56ea3-132">Obtém ou define o número máximo de canais que um serviço pode ter aguardando um ouvinte para processar conexões de entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="56ea3-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="56ea3-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="56ea3-133">maxPendingConnections</span></span>|<span data-ttu-id="56ea3-134">Obtém ou define o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="56ea3-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="56ea3-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="56ea3-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="56ea3-136">Obtém e define o tamanho de mensagem máximo permitido, em bytes, que pode ser recebido.</span><span class="sxs-lookup"><span data-stu-id="56ea3-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="56ea3-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="56ea3-137">transferMode</span></span>|<span data-ttu-id="56ea3-138">Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="56ea3-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="56ea3-139">\<connectionPoolSettings > de \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="56ea3-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="56ea3-140">Especifica configurações de pool de conexões adicionais para uma associação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="56ea3-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56ea3-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="56ea3-141">Parent Elements</span></span>  
  
|<span data-ttu-id="56ea3-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="56ea3-142">Element</span></span>|<span data-ttu-id="56ea3-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="56ea3-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56ea3-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="56ea3-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="56ea3-145">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="56ea3-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56ea3-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="56ea3-146">Remarks</span></span>  
<span data-ttu-id="56ea3-147">Esse transporte usa URIs no formato "net. pipe://hostname/Path".</span><span class="sxs-lookup"><span data-stu-id="56ea3-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="56ea3-148">Outros componentes de URI são opcionais.</span><span class="sxs-lookup"><span data-stu-id="56ea3-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="56ea3-149">O `namedPipeTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte de pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="56ea3-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="56ea3-150">Esse transporte é usado para a comunicação WCF (Windows Communication Foundation no computador) para WCF.</span><span class="sxs-lookup"><span data-stu-id="56ea3-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ea3-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56ea3-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="56ea3-152">Transportes</span><span class="sxs-lookup"><span data-stu-id="56ea3-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="56ea3-153">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="56ea3-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="56ea3-154">Associações</span><span class="sxs-lookup"><span data-stu-id="56ea3-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="56ea3-155">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="56ea3-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="56ea3-156">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="56ea3-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="56ea3-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="56ea3-157">\<customBinding></span></span>](custombinding.md)
