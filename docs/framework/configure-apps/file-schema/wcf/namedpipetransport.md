---
title: '&lt;namedPipeTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 652cb551fb318d43d4284dbee48aeb994f056692
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="f32be-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="f32be-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="f32be-103">Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados quando ele é incluído em uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f32be-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="f32be-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f32be-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f32be-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="f32be-105">\<bindings></span></span>  
<span data-ttu-id="f32be-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f32be-106">\<customBinding></span></span>  
<span data-ttu-id="f32be-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f32be-107">\<binding></span></span>  
<span data-ttu-id="f32be-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="f32be-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f32be-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f32be-109">Syntax</span></span>  
  
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
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f32be-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f32be-110">Attributes and Elements</span></span>  
<span data-ttu-id="f32be-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f32be-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f32be-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f32be-112">Attributes</span></span>  
<span data-ttu-id="f32be-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f32be-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f32be-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f32be-114">Child Elements</span></span>  
  
|<span data-ttu-id="f32be-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f32be-115">Element</span></span>|<span data-ttu-id="f32be-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f32be-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f32be-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="f32be-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="f32be-118">Obtém ou define um <xref:System.TimeSpan> que determina o tempo máximo que um canal pode estar com o status de inicialização antes de ser desconectado.</span><span class="sxs-lookup"><span data-stu-id="f32be-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="f32be-119">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="f32be-119">ConnectionBufferSize</span></span>|<span data-ttu-id="f32be-120">Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="f32be-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="f32be-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="f32be-121">hostNameComparisonMode</span></span>|<span data-ttu-id="f32be-122">Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="f32be-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="f32be-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="f32be-123">manualAddressing</span></span>|<span data-ttu-id="f32be-124">Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.</span><span class="sxs-lookup"><span data-stu-id="f32be-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="f32be-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f32be-125">maxBufferPoolSize</span></span>|<span data-ttu-id="f32be-126">Obtém ou define o tamanho máximo, em bytes, de qualquer pool de buffer usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="f32be-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="f32be-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="f32be-127">maxBufferSize</span></span>|<span data-ttu-id="f32be-128">Obtém ou define o tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="f32be-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="f32be-129">Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.</span><span class="sxs-lookup"><span data-stu-id="f32be-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="f32be-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="f32be-130">maxOutputDelay</span></span>|<span data-ttu-id="f32be-131">Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="f32be-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="f32be-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="f32be-132">maxPendingAccepts</span></span>|<span data-ttu-id="f32be-133">Obtém ou define o número máximo de canais que um serviço pode ter aguardando um ouvinte para processar conexões de entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f32be-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="f32be-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="f32be-134">maxPendingConnections</span></span>|<span data-ttu-id="f32be-135">Obtém ou define o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="f32be-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="f32be-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="f32be-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="f32be-137">Obtém e define o tamanho de mensagem máximo permitido, em bytes, que pode ser recebido.</span><span class="sxs-lookup"><span data-stu-id="f32be-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="f32be-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="f32be-138">transferMode</span></span>|<span data-ttu-id="f32be-139">Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="f32be-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="f32be-140">\<connectionPoolSettings > de \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="f32be-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="f32be-141">Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="f32be-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f32be-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f32be-142">Parent Elements</span></span>  
  
|<span data-ttu-id="f32be-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="f32be-143">Element</span></span>|<span data-ttu-id="f32be-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="f32be-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f32be-145">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f32be-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f32be-146">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="f32be-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f32be-147">Comentários</span><span class="sxs-lookup"><span data-stu-id="f32be-147">Remarks</span></span>  
<span data-ttu-id="f32be-148">Esse transporte usa URIs no formato "net.pipe://hostname/path".</span><span class="sxs-lookup"><span data-stu-id="f32be-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="f32be-149">Outros componentes do URI são opcionais.</span><span class="sxs-lookup"><span data-stu-id="f32be-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="f32be-150">O `namedPipeTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte de pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="f32be-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="f32be-151">Esse transporte é usado para em computadores Windows Communication Foundation (WCF) - para - comunicação WCF.</span><span class="sxs-lookup"><span data-stu-id="f32be-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32be-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f32be-152">See Also</span></span>  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
<span data-ttu-id="f32be-153">[Transportes](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="f32be-153">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="f32be-154">[Selecionando um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="f32be-154">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="f32be-155">[Associações](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="f32be-155">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="f32be-156">[Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="f32be-156">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="f32be-157">[Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="f32be-157">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="f32be-158">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f32be-158">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
