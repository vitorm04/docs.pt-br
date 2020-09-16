---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: b2ff39e1292cfaad1165e14e693acda2518477a6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559038"
---
# \<udpBinding>
<span data-ttu-id="1a187-101">Um elemento de configuração usado para configurar a <xref:System.ServiceModel.UdpBinding> associação.</span><span class="sxs-lookup"><span data-stu-id="1a187-101">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1a187-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="1a187-102">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a187-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1a187-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1a187-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1a187-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a187-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="1a187-105">Attributes</span></span>  
  
|<span data-ttu-id="1a187-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="1a187-106">Attribute</span></span>|<span data-ttu-id="1a187-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a187-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1a187-108">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="1a187-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1a187-109">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1a187-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1a187-110">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1a187-110">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="1a187-111">Um valor inteiro que especifica o comprimento do histórico de mensagens duplicado.</span><span class="sxs-lookup"><span data-stu-id="1a187-111">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="1a187-112">Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagens que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="1a187-112">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="1a187-113">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="1a187-113">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="1a187-114">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto elas são processadas para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="1a187-114">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="1a187-115">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="1a187-115">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="1a187-116">Um valor inteiro que especifica o número máximo de mensagens que são recebidas, mas ainda não foram removidas da fila de entrada para uma instância de canal individual.</span><span class="sxs-lookup"><span data-stu-id="1a187-116">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="1a187-117">Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, para uma mensagem que pode ser recebida em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="1a187-117">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1a187-118">O remetente receberá uma falha de SOAP se a mensagem for muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="1a187-118">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="1a187-119">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="1a187-119">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1a187-120">O padrão é de 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="1a187-120">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="1a187-121">Um valor inteiro que especifica o número máximo de mensagens de retransmissão.</span><span class="sxs-lookup"><span data-stu-id="1a187-121">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="1a187-122">Um valor inteiro que especifica a ID da interface multicast.</span><span class="sxs-lookup"><span data-stu-id="1a187-122">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="1a187-123">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="1a187-123">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1a187-124">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="1a187-124">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1a187-125">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="1a187-125">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1a187-126">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1a187-126">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1a187-127">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="1a187-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1a187-128">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1a187-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1a187-129">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1a187-129">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1a187-130">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="1a187-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1a187-131">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1a187-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1a187-132">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1a187-132">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1a187-133">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="1a187-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1a187-134">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1a187-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1a187-135">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1a187-135">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="1a187-136">Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="1a187-136">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="1a187-137">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="1a187-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1a187-138">-BigEndianUnicode: codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="1a187-138">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="1a187-139">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="1a187-139">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="1a187-140">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="1a187-140">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="1a187-141">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="1a187-141">The default is UTF8.</span></span> <span data-ttu-id="1a187-142">Esse atributo é do tipo <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="1a187-142">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="1a187-143">Um valor TimeSpan que especifica a vida útil para a associação.</span><span class="sxs-lookup"><span data-stu-id="1a187-143">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a187-144">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1a187-144">Child Elements</span></span>  
  
|<span data-ttu-id="1a187-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="1a187-145">Element</span></span>|<span data-ttu-id="1a187-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a187-146">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="1a187-147">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="1a187-147">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1a187-148">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="1a187-148">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a187-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1a187-149">Parent Elements</span></span>  
  
|<span data-ttu-id="1a187-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="1a187-150">Element</span></span>|<span data-ttu-id="1a187-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a187-151">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="1a187-152">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="1a187-152">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a187-153">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a187-153">Remarks</span></span>  
 <span data-ttu-id="1a187-154">O UdpBinding permite que os serviços WCF se comuniquem por meio do transporte UDP.</span><span class="sxs-lookup"><span data-stu-id="1a187-154">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="1a187-155">Ele permite trocas de mensagens de "incêndio e esquecido" onde um cliente envia uma mensagem a um serviço e não espera resposta.</span><span class="sxs-lookup"><span data-stu-id="1a187-155">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a187-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a187-156">Example</span></span>  
 <span data-ttu-id="1a187-157">O exemplo a seguir mostra como configurar o <xref:System.ServiceModel.UdpBinding> usando o `udpBinding` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="1a187-157">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="1a187-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="1a187-158">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="1a187-159">Associações</span><span class="sxs-lookup"><span data-stu-id="1a187-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1a187-160">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="1a187-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1a187-161">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1a187-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
