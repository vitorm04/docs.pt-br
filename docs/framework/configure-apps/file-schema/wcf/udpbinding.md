---
title: '&lt;udpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f43462ac42c59407ae90f2d342a445a688e1b26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="30577-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="30577-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="30577-103">Um elemento de configuração usado para configurar o <xref:System.ServiceModel.UdpBinding> associação.</span><span class="sxs-lookup"><span data-stu-id="30577-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="30577-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="30577-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="30577-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="30577-105">\<bindings></span></span>  
<span data-ttu-id="30577-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="30577-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30577-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30577-107">Syntax</span></span>  
  
```xml  
<udpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       duplicateMessageHistoryLength="Integer"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"       maxPendingMessagesTotalSize="Integer"  
       maxReceivedMessageSize="Integer"       maxRetransmitCount="Integer"  
       multicastInterfaceId="Integer"  
              name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       timeToLive="TimeSpan">  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30577-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="30577-108">Attributes and Elements</span></span>  
 <span data-ttu-id="30577-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="30577-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30577-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="30577-110">Attributes</span></span>  
  
|<span data-ttu-id="30577-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="30577-111">Attribute</span></span>|<span data-ttu-id="30577-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="30577-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="30577-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="30577-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="30577-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="30577-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="30577-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="30577-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="30577-116">Um valor inteiro que especifica o comprimento do histórico de mensagens duplicadas.</span><span class="sxs-lookup"><span data-stu-id="30577-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="30577-117">Um valor inteiro que especifica a quantidade máxima de memória que é alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="30577-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="30577-118">O valor padrão é 524288 (0x80000) bytes.</span><span class="sxs-lookup"><span data-stu-id="30577-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="30577-119">Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="30577-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="30577-120">O valor padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="30577-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="30577-121">Um valor inteiro que especifica o número máximo de mensagens que são recebidos, mas ainda não foram removidas da fila de entrada para uma instância de canal individual.</span><span class="sxs-lookup"><span data-stu-id="30577-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="30577-122">Um inteiro positivo que define o tamanho máximo, em bytes, incluindo os cabeçalhos de uma mensagem que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="30577-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="30577-123">O remetente recebe uma falha de SOAP se a mensagem é muito grande para o receptor.</span><span class="sxs-lookup"><span data-stu-id="30577-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="30577-124">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="30577-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="30577-125">O padrão é 65.536 bytes.</span><span class="sxs-lookup"><span data-stu-id="30577-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="30577-126">Um valor inteiro que especifica o número máximo de mensagens de retransmissão.</span><span class="sxs-lookup"><span data-stu-id="30577-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="30577-127">Um valor inteiro que especifica a ID de interface de multicast.</span><span class="sxs-lookup"><span data-stu-id="30577-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="30577-128">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="30577-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="30577-129">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="30577-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="30577-130">Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="30577-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="30577-131">Além disso, esse nome é exclusivo entre as associações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="30577-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="30577-132">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="30577-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="30577-133">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="30577-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="30577-134">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="30577-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="30577-135">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="30577-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="30577-136">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="30577-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="30577-137">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="30577-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="30577-138">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="30577-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="30577-139">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="30577-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="30577-140">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="30577-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="30577-141">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="30577-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="30577-142">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="30577-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="30577-143">Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="30577-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="30577-144">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="30577-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="30577-145">-BigEndianUnicode: O Unicode BigEndian codificação.</span><span class="sxs-lookup"><span data-stu-id="30577-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="30577-146">-Unicode: codificação de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="30577-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="30577-147">-UTF8: codificação de 8 bits</span><span class="sxs-lookup"><span data-stu-id="30577-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="30577-148">O padrão é UTF8.</span><span class="sxs-lookup"><span data-stu-id="30577-148">The default is UTF8.</span></span> <span data-ttu-id="30577-149">Esse atributo é do tipo <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="30577-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="30577-150">Um valor timespan que especifica o tempo de vida para a associação.</span><span class="sxs-lookup"><span data-stu-id="30577-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30577-151">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="30577-151">Child Elements</span></span>  
  
|<span data-ttu-id="30577-152">Elemento</span><span class="sxs-lookup"><span data-stu-id="30577-152">Element</span></span>|<span data-ttu-id="30577-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="30577-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30577-154">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="30577-154">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="30577-155">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="30577-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="30577-156">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="30577-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30577-157">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="30577-157">Parent Elements</span></span>  
  
|<span data-ttu-id="30577-158">Elemento</span><span class="sxs-lookup"><span data-stu-id="30577-158">Element</span></span>|<span data-ttu-id="30577-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="30577-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30577-160">\<associações ></span><span class="sxs-lookup"><span data-stu-id="30577-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="30577-161">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="30577-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30577-162">Comentários</span><span class="sxs-lookup"><span data-stu-id="30577-162">Remarks</span></span>  
 <span data-ttu-id="30577-163">O UdpBinding permite que os serviços do WCF para se comunicar por meio do transporte UDP.</span><span class="sxs-lookup"><span data-stu-id="30577-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="30577-164">Permite trocas de mensagens de "disparar e esquecer" onde um cliente envia uma mensagem para um serviço e espera sem resposta de volta.</span><span class="sxs-lookup"><span data-stu-id="30577-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30577-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30577-165">Example</span></span>  
 <span data-ttu-id="30577-166">O exemplo a seguir mostra como configurar o <xref:System.ServiceModel.UdpBinding> usando o <`udpBinding`> elemento.</span><span class="sxs-lookup"><span data-stu-id="30577-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
                   timeToLive="00:10:00"  
          <readerQuotas/>   
        </binding>  
      </udpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30577-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30577-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="30577-168">Associações</span><span class="sxs-lookup"><span data-stu-id="30577-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="30577-169">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="30577-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="30577-170">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="30577-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="30577-171">\<associação ></span><span class="sxs-lookup"><span data-stu-id="30577-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
