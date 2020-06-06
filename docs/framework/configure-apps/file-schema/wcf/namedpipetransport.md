---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 00631ad88d771ed8f45638f28c84df05917fd3a0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736589"
---
# \<namedPipeTransport>
<span data-ttu-id="79db5-101">Define um transporte que faz com que um canal transfira mensagens usando pipes nomeados quando ele é incluído em uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="79db5-101">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="79db5-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79db5-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79db5-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="79db5-103">Attributes and Elements</span></span>  
<span data-ttu-id="79db5-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="79db5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79db5-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="79db5-105">Attributes</span></span>  
<span data-ttu-id="79db5-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="79db5-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79db5-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="79db5-107">Child Elements</span></span>  
  
|<span data-ttu-id="79db5-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="79db5-108">Element</span></span>|<span data-ttu-id="79db5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="79db5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79db5-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="79db5-110">ChannelInitializationTimeout</span></span>|<span data-ttu-id="79db5-111">Obtém ou define um <xref:System.TimeSpan> que determina o tempo máximo que um canal pode estar com o status de inicialização antes de ser desconectado.</span><span class="sxs-lookup"><span data-stu-id="79db5-111">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="79db5-112">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="79db5-112">ConnectionBufferSize</span></span>|<span data-ttu-id="79db5-113">Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="79db5-113">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="79db5-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="79db5-114">hostNameComparisonMode</span></span>|<span data-ttu-id="79db5-115">Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.</span><span class="sxs-lookup"><span data-stu-id="79db5-115">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="79db5-116">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="79db5-116">manualAddressing</span></span>|<span data-ttu-id="79db5-117">Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.</span><span class="sxs-lookup"><span data-stu-id="79db5-117">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="79db5-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="79db5-118">maxBufferPoolSize</span></span>|<span data-ttu-id="79db5-119">Obtém ou define o tamanho máximo, em bytes, de qualquer pool de buffer usado pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="79db5-119">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="79db5-120">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="79db5-120">maxBufferSize</span></span>|<span data-ttu-id="79db5-121">Obtém ou define o tamanho máximo do buffer a ser usado.</span><span class="sxs-lookup"><span data-stu-id="79db5-121">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="79db5-122">Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.</span><span class="sxs-lookup"><span data-stu-id="79db5-122">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="79db5-123">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="79db5-123">maxOutputDelay</span></span>|<span data-ttu-id="79db5-124">Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.</span><span class="sxs-lookup"><span data-stu-id="79db5-124">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="79db5-125">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="79db5-125">maxPendingAccepts</span></span>|<span data-ttu-id="79db5-126">Obtém ou define o número máximo de canais que um serviço pode ter aguardando um ouvinte para processar conexões de entrada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="79db5-126">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="79db5-127">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="79db5-127">maxPendingConnections</span></span>|<span data-ttu-id="79db5-128">Obtém ou define o número máximo de conexões aguardando a expedição no serviço.</span><span class="sxs-lookup"><span data-stu-id="79db5-128">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="79db5-129">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="79db5-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="79db5-130">Obtém e define o tamanho de mensagem máximo permitido, em bytes, que pode ser recebido.</span><span class="sxs-lookup"><span data-stu-id="79db5-130">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="79db5-131">transferMode</span><span class="sxs-lookup"><span data-stu-id="79db5-131">transferMode</span></span>|<span data-ttu-id="79db5-132">Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.</span><span class="sxs-lookup"><span data-stu-id="79db5-132">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="79db5-133">\<connectionPoolSettings>desse\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="79db5-133">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="79db5-134">Especifica configurações de pool de conexões adicionais para uma associação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="79db5-134">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79db5-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="79db5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="79db5-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="79db5-136">Element</span></span>|<span data-ttu-id="79db5-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="79db5-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="79db5-138">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="79db5-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79db5-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="79db5-139">Remarks</span></span>  
<span data-ttu-id="79db5-140">Esse transporte usa URIs no formato "net. pipe://hostname/Path".</span><span class="sxs-lookup"><span data-stu-id="79db5-140">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="79db5-141">Outros componentes de URI são opcionais.</span><span class="sxs-lookup"><span data-stu-id="79db5-141">Other URI components are optional.</span></span>  
  
<span data-ttu-id="79db5-142">O `namedPipeTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte de pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="79db5-142">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="79db5-143">Esse transporte é usado para a comunicação WCF (Windows Communication Foundation no computador) para WCF.</span><span class="sxs-lookup"><span data-stu-id="79db5-143">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79db5-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="79db5-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="79db5-145">Transportes</span><span class="sxs-lookup"><span data-stu-id="79db5-145">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="79db5-146">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="79db5-146">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="79db5-147">Associações</span><span class="sxs-lookup"><span data-stu-id="79db5-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="79db5-148">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="79db5-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="79db5-149">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="79db5-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
