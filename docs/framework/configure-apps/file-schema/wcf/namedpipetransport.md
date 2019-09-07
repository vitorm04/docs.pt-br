---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: e5f1d49e0e3bb5f52c5e18577d556d25539434a9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400161"
---
# <a name="namedpipetransport"></a><span data-ttu-id="bbbbc-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="bbbbc-101">\<namedPipeTransport></span></span>
<span data-ttu-id="bbbbc-102">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados quando ele é incluído em uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="bbbbc-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bbbbc-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bbbbc-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bbbbc-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bbbbc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bbbbc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bbbbc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bbbbc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="bbbbc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="bbbbc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="bbbbc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> namedPipeTransport**</span><span class="sxs-lookup"><span data-stu-id="bbbbc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbbc-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbbbc-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbbbc-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bbbbc-110">Attributes and Elements</span></span>  
<span data-ttu-id="bbbbc-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbbbc-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="bbbbc-112">Attributes</span></span>  
<span data-ttu-id="bbbbc-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bbbbc-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bbbbc-114">Child Elements</span></span>  
  
|<span data-ttu-id="bbbbc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="bbbbc-115">Element</span></span>|<span data-ttu-id="bbbbc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbbbc-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbbbc-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="bbbbc-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="bbbbc-118">Obtém ou define um <xref:System.TimeSpan> que determina o tempo máximo que um canal pode estar com o status de inicialização antes de ser desconectado.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="bbbbc-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="bbbbc-119">ConnectionBufferSize</span></span>|<span data-ttu-id="bbbbc-120">Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="bbbbc-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="bbbbc-121">hostNameComparisonMode</span></span>|<span data-ttu-id="bbbbc-122">Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="bbbbc-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="bbbbc-123">manualAddressing</span></span>|<span data-ttu-id="bbbbc-124">Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="bbbbc-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="bbbbc-125">maxBufferPoolSize</span></span>|<span data-ttu-id="bbbbc-126">Obtém ou define o tamanho máximo, em bytes, de qualquer pool de buffer usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="bbbbc-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="bbbbc-127">maxBufferSize</span></span>|<span data-ttu-id="bbbbc-128">Obtém ou define o tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="bbbbc-129">Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="bbbbc-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="bbbbc-130">maxOutputDelay</span></span>|<span data-ttu-id="bbbbc-131">Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="bbbbc-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="bbbbc-132">maxPendingAccepts</span></span>|<span data-ttu-id="bbbbc-133">Obtém ou define o número máximo de canais que um serviço pode ter aguardando um ouvinte para processar conexões de entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="bbbbc-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="bbbbc-134">maxPendingConnections</span></span>|<span data-ttu-id="bbbbc-135">Obtém ou define o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="bbbbc-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="bbbbc-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="bbbbc-137">Obtém e define o tamanho de mensagem máximo permitido, em bytes, que pode ser recebido.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="bbbbc-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="bbbbc-138">transferMode</span></span>|<span data-ttu-id="bbbbc-139">Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="bbbbc-140">\<connectionPoolSettings > de \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="bbbbc-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="bbbbc-141">Especifica configurações de pool de conexões adicionais para uma associação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbbbc-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bbbbc-142">Parent Elements</span></span>  
  
|<span data-ttu-id="bbbbc-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="bbbbc-143">Element</span></span>|<span data-ttu-id="bbbbc-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="bbbbc-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbbbc-145">\<binding></span><span class="sxs-lookup"><span data-stu-id="bbbbc-145">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="bbbbc-146">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbbbc-147">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbbbc-147">Remarks</span></span>  
<span data-ttu-id="bbbbc-148">Esse transporte usa URIs no formato "net. pipe://hostname/Path".</span><span class="sxs-lookup"><span data-stu-id="bbbbc-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="bbbbc-149">Outros componentes de URI são opcionais.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="bbbbc-150">O `namedPipeTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte de pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="bbbbc-151">Esse transporte é usado para a comunicação WCF (Windows Communication Foundation no computador) para WCF.</span><span class="sxs-lookup"><span data-stu-id="bbbbc-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbbc-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbbbc-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bbbbc-153">Transportes</span><span class="sxs-lookup"><span data-stu-id="bbbbc-153">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="bbbbc-154">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="bbbbc-154">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="bbbbc-155">Associações</span><span class="sxs-lookup"><span data-stu-id="bbbbc-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bbbbc-156">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="bbbbc-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bbbbc-157">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bbbbc-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bbbbc-158">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bbbbc-158">\<customBinding></span></span>](custombinding.md)
