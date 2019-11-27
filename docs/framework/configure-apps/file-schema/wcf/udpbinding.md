---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 7fa72d233d6489ab6a2c534f69c66a55a22d0f59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429836"
---
# <a name="udpbinding"></a><span data-ttu-id="5169b-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="5169b-101">\<udpBinding></span></span>
<span data-ttu-id="5169b-102">Um elemento de configuração usado para configurar a associação de <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5169b-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="5169b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5169b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5169b-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5169b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5169b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="5169b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5169b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding >**</span><span class="sxs-lookup"><span data-stu-id="5169b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5169b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5169b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5169b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5169b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5169b-109">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="5169b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5169b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5169b-110">Attributes</span></span>  
  
|<span data-ttu-id="5169b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5169b-111">Attribute</span></span>|<span data-ttu-id="5169b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5169b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="5169b-113">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="5169b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5169b-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5169b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5169b-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5169b-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="5169b-116">Um valor inteiro que especifica o comprimento do histórico de mensagens duplicado.</span><span class="sxs-lookup"><span data-stu-id="5169b-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="5169b-117">Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagens que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="5169b-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="5169b-118">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="5169b-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="5169b-119">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto elas são processadas para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="5169b-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="5169b-120">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="5169b-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="5169b-121">Um valor inteiro que especifica o número máximo de mensagens que são recebidas, mas ainda não foram removidas da fila de entrada para uma instância de canal individual.</span><span class="sxs-lookup"><span data-stu-id="5169b-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="5169b-122">Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, para uma mensagem que pode ser recebida em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="5169b-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="5169b-123">O remetente receberá uma falha de SOAP se a mensagem for muito grande para o destinatário.</span><span class="sxs-lookup"><span data-stu-id="5169b-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="5169b-124">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5169b-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5169b-125">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="5169b-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="5169b-126">Um valor inteiro que especifica o número máximo de mensagens de retransmissão.</span><span class="sxs-lookup"><span data-stu-id="5169b-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="5169b-127">Um valor inteiro que especifica a ID da interface multicast.</span><span class="sxs-lookup"><span data-stu-id="5169b-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="5169b-128">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="5169b-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5169b-129">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="5169b-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5169b-130">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="5169b-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5169b-131">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5169b-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="5169b-132">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="5169b-132">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5169b-133">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5169b-133">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5169b-134">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5169b-134">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="5169b-135">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="5169b-135">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5169b-136">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5169b-136">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5169b-137">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="5169b-137">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="5169b-138">Um valor <xref:System.TimeSpan> que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="5169b-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5169b-139">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5169b-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5169b-140">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5169b-140">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="5169b-141">Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="5169b-141">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="5169b-142">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5169b-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5169b-143">-BigEndianUnicode: codificação BigEndian Unicode.</span><span class="sxs-lookup"><span data-stu-id="5169b-143">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="5169b-144">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="5169b-144">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="5169b-145">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="5169b-145">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="5169b-146">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="5169b-146">The default is UTF8.</span></span> <span data-ttu-id="5169b-147">Este atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="5169b-147">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="5169b-148">Um valor TimeSpan que especifica a vida útil para a associação.</span><span class="sxs-lookup"><span data-stu-id="5169b-148">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5169b-149">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5169b-149">Child Elements</span></span>  
  
|<span data-ttu-id="5169b-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="5169b-150">Element</span></span>|<span data-ttu-id="5169b-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="5169b-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5169b-152">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5169b-152">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="5169b-153">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="5169b-153">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5169b-154">Este elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="5169b-154">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5169b-155">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="5169b-155">Parent Elements</span></span>  
  
|<span data-ttu-id="5169b-156">Elemento</span><span class="sxs-lookup"><span data-stu-id="5169b-156">Element</span></span>|<span data-ttu-id="5169b-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="5169b-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5169b-158">associações de \<></span><span class="sxs-lookup"><span data-stu-id="5169b-158">\<bindings></span></span>](bindings.md)|<span data-ttu-id="5169b-159">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5169b-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5169b-160">Comentários</span><span class="sxs-lookup"><span data-stu-id="5169b-160">Remarks</span></span>  
 <span data-ttu-id="5169b-161">O UdpBinding permite que os serviços WCF se comuniquem por meio do transporte UDP.</span><span class="sxs-lookup"><span data-stu-id="5169b-161">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="5169b-162">Ele permite trocas de mensagens de "incêndio e esquecido" onde um cliente envia uma mensagem a um serviço e não espera resposta.</span><span class="sxs-lookup"><span data-stu-id="5169b-162">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5169b-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5169b-163">Example</span></span>  
 <span data-ttu-id="5169b-164">O exemplo a seguir mostra como configurar o <xref:System.ServiceModel.UdpBinding> usando o elemento >`udpBinding`<.</span><span class="sxs-lookup"><span data-stu-id="5169b-164">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5169b-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5169b-165">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="5169b-166">Associações</span><span class="sxs-lookup"><span data-stu-id="5169b-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5169b-167">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="5169b-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5169b-168">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5169b-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5169b-169">> de associação de \<</span><span class="sxs-lookup"><span data-stu-id="5169b-169">\<binding></span></span>](bindings.md)
