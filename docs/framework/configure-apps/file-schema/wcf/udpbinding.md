---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 84a5bc763f898b3d323a6cee468c6e22d27d85a0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229596"
---
# <a name="udpbinding"></a><span data-ttu-id="6631a-101">\<udpBinding></span><span class="sxs-lookup"><span data-stu-id="6631a-101">\<udpBinding></span></span>
<span data-ttu-id="6631a-102">Um elemento de configuração usado para configurar o <xref:System.ServiceModel.UdpBinding> associação.</span><span class="sxs-lookup"><span data-stu-id="6631a-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="6631a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6631a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6631a-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6631a-104">\<bindings></span></span>  
<span data-ttu-id="6631a-105">\<udpBinding></span><span class="sxs-lookup"><span data-stu-id="6631a-105">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6631a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6631a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6631a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6631a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6631a-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6631a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6631a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="6631a-109">Attributes</span></span>  
  
|<span data-ttu-id="6631a-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="6631a-110">Attribute</span></span>|<span data-ttu-id="6631a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6631a-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="6631a-112">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="6631a-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6631a-113">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6631a-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6631a-114">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="6631a-114">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="6631a-115">Um valor inteiro que especifica o comprimento do histórico de mensagens duplicadas.</span><span class="sxs-lookup"><span data-stu-id="6631a-115">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="6631a-116">Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="6631a-116">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="6631a-117">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="6631a-117">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="6631a-118">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena as mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="6631a-118">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="6631a-119">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="6631a-119">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="6631a-120">Um valor inteiro que especifica o número máximo de mensagens que são recebidas, mas ainda não foram removidas da fila de entrada para uma instância de canal individual.</span><span class="sxs-lookup"><span data-stu-id="6631a-120">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="6631a-121">Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos de mensagem pode ser recebida em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="6631a-121">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6631a-122">O remetente recebe uma falha de SOAP, se a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="6631a-122">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="6631a-123">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6631a-123">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6631a-124">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="6631a-124">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="6631a-125">Um valor inteiro que especifica o número máximo de mensagens de retransmissão.</span><span class="sxs-lookup"><span data-stu-id="6631a-125">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="6631a-126">Um valor inteiro que especifica a ID de interface de multicast.</span><span class="sxs-lookup"><span data-stu-id="6631a-126">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="6631a-127">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="6631a-127">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6631a-128">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="6631a-128">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6631a-129">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="6631a-129">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="6631a-130">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="6631a-130">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="6631a-131">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="6631a-131">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6631a-132">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6631a-132">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="6631a-133">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="6631a-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6631a-134">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6631a-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6631a-135">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="6631a-135">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6631a-136">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="6631a-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6631a-137">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6631a-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6631a-138">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="6631a-138">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6631a-139">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="6631a-139">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6631a-140">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6631a-140">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6631a-141">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="6631a-141">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="6631a-142">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6631a-142">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="6631a-143">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6631a-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6631a-144">-   BigEndianUnicode: Unicode BigEndian de codificação.</span><span class="sxs-lookup"><span data-stu-id="6631a-144">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="6631a-145">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="6631a-145">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="6631a-146">-   UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="6631a-146">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="6631a-147">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="6631a-147">The default is UTF8.</span></span> <span data-ttu-id="6631a-148">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="6631a-148">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="6631a-149">Um valor de timespan que especifica a vida útil para a associação.</span><span class="sxs-lookup"><span data-stu-id="6631a-149">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6631a-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6631a-150">Child Elements</span></span>  
  
|<span data-ttu-id="6631a-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="6631a-151">Element</span></span>|<span data-ttu-id="6631a-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="6631a-152">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6631a-153">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6631a-153">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="6631a-154">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="6631a-154">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6631a-155">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="6631a-155">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6631a-156">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6631a-156">Parent Elements</span></span>  
  
|<span data-ttu-id="6631a-157">Elemento</span><span class="sxs-lookup"><span data-stu-id="6631a-157">Element</span></span>|<span data-ttu-id="6631a-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="6631a-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6631a-159">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6631a-159">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="6631a-160">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="6631a-160">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6631a-161">Comentários</span><span class="sxs-lookup"><span data-stu-id="6631a-161">Remarks</span></span>  
 <span data-ttu-id="6631a-162">O UdpBinding permite que os serviços do WCF para se comunicar por meio do transporte UDP.</span><span class="sxs-lookup"><span data-stu-id="6631a-162">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="6631a-163">Ele permite trocas de mensagens de "disparar e esquecer" em que um cliente envia uma mensagem para um serviço e não espera nenhuma resposta de volta.</span><span class="sxs-lookup"><span data-stu-id="6631a-163">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6631a-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6631a-164">Example</span></span>  
 <span data-ttu-id="6631a-165">O exemplo a seguir mostra como configurar o <xref:System.ServiceModel.UdpBinding> usando o <`udpBinding`> elemento.</span><span class="sxs-lookup"><span data-stu-id="6631a-165">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6631a-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6631a-166">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="6631a-167">Associações</span><span class="sxs-lookup"><span data-stu-id="6631a-167">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6631a-168">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="6631a-168">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6631a-169">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6631a-169">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6631a-170">\<binding></span><span class="sxs-lookup"><span data-stu-id="6631a-170">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
