---
title: '&lt;reliableSession&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8484fe902b356f7fae4e526bdaa5610bf7d7ac6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltreliablesessiongt"></a><span data-ttu-id="e96e9-102">&lt;reliableSession&gt;</span><span class="sxs-lookup"><span data-stu-id="e96e9-102">&lt;reliableSession&gt;</span></span>
<span data-ttu-id="e96e9-103">Define a configuração para mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="e96e9-103">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="e96e9-104">Quando esse elemento é adicionado a uma associação personalizada, o canal resultante pode dar suporte a exatamente-uma vez garantias de entrega.</span><span class="sxs-lookup"><span data-stu-id="e96e9-104">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
 <span data-ttu-id="e96e9-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e96e9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e96e9-106">\<associações ></span><span class="sxs-lookup"><span data-stu-id="e96e9-106">\<bindings></span></span>  
<span data-ttu-id="e96e9-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e96e9-107">\<customBinding></span></span>  
<span data-ttu-id="e96e9-108">\<associação ></span><span class="sxs-lookup"><span data-stu-id="e96e9-108">\<binding></span></span>  
<span data-ttu-id="e96e9-109">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="e96e9-109">\<reliableSession></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e96e9-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e96e9-110">Syntax</span></span>  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"  
        flowControlEnabled="Boolean"   
    inactivityTimeout="TimeSpan"  
    maxPendingChannels="Integer"  
    maxRetryCount="Integer"   
        maxTransferWindowSize="Integer"  
    reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"  
    ordered="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e96e9-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e96e9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e96e9-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e96e9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e96e9-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="e96e9-113">Attributes</span></span>  
  
|<span data-ttu-id="e96e9-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="e96e9-114">Attribute</span></span>|<span data-ttu-id="e96e9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e96e9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e96e9-116">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="e96e9-116">acknowledgementInterval</span></span>|<span data-ttu-id="e96e9-117">Um <xref:System.TimeSpan> que contém o intervalo de tempo máximo que o canal vai esperar para enviar uma confirmação de mensagens recebidas até aquele ponto.</span><span class="sxs-lookup"><span data-stu-id="e96e9-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="e96e9-118">O padrão é 00:00:0.2.</span><span class="sxs-lookup"><span data-stu-id="e96e9-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="e96e9-119">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="e96e9-119">flowControlEnabled</span></span>|<span data-ttu-id="e96e9-120">Um valor booliano que indica se o controle de fluxo avançado, uma implementação específica da Microsoft de controle de fluxo de mensagens WS-Reliable, é ativado.</span><span class="sxs-lookup"><span data-stu-id="e96e9-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="e96e9-121">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="e96e9-121">The default is `true`.</span></span>|  
|<span data-ttu-id="e96e9-122">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="e96e9-122">inactivityTimeout</span></span>|<span data-ttu-id="e96e9-123">Um <xref:System.TimeSpan> que especifica a duração máxima que o canal vai permitir que a outra parte da comunicação para não enviar qualquer mensagem, antes de haver falha no canal.</span><span class="sxs-lookup"><span data-stu-id="e96e9-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="e96e9-124">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="e96e9-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="e96e9-125">Atividade em um canal é definida como receber mensagens de infraestrutura ou de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e96e9-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="e96e9-126">Essa propriedade controla a quantidade máxima de tempo para manter uma sessão inativa ativa.</span><span class="sxs-lookup"><span data-stu-id="e96e9-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="e96e9-127">Se passa mais tempo sem nenhuma atividade, a sessão é anulada, a infraestrutura e as falhas de canal.</span><span class="sxs-lookup"><span data-stu-id="e96e9-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="e96e9-128">**Observação:** não é necessário para o aplicativo para enviar mensagens para manter a conexão ativa, periodicamente.</span><span class="sxs-lookup"><span data-stu-id="e96e9-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="e96e9-129">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="e96e9-129">maxPendingChannels</span></span>|<span data-ttu-id="e96e9-130">Um inteiro que especifica o número máximo de canais que podem esperar no ouvinte para serem aceitos.</span><span class="sxs-lookup"><span data-stu-id="e96e9-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="e96e9-131">Esse valor deve estar entre 1 a 16384 inclusivo.</span><span class="sxs-lookup"><span data-stu-id="e96e9-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="e96e9-132">O padrão é 4.</span><span class="sxs-lookup"><span data-stu-id="e96e9-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="e96e9-133">Os canais estão pendentes quando estão aguardando para serem aceitos.</span><span class="sxs-lookup"><span data-stu-id="e96e9-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="e96e9-134">Quando esse limite é atingido, não há canais são criados.</span><span class="sxs-lookup"><span data-stu-id="e96e9-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="e96e9-135">Em vez disso, eles são colocados no pendentes modo até que esse número chegar para baixo (aceitando pendentes canais).</span><span class="sxs-lookup"><span data-stu-id="e96e9-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="e96e9-136">Este é um limite por fábrica.</span><span class="sxs-lookup"><span data-stu-id="e96e9-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="e96e9-137">Quando o limite for atingido, e um aplicativo remoto tenta estabelecer uma nova sessão confiável, a solicitação será negada e a operação de abertura que gerou este falhas.</span><span class="sxs-lookup"><span data-stu-id="e96e9-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="e96e9-138">Esse limite não se aplica ao número de pendente canais de saída.</span><span class="sxs-lookup"><span data-stu-id="e96e9-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="e96e9-139">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="e96e9-139">maxRetryCount</span></span>|<span data-ttu-id="e96e9-140">Um inteiro que especifica o número máximo de vezes que um canal confiável tenta retransmitir uma mensagem não recebeu uma confirmação, chamando Send em seu canal subjacente.</span><span class="sxs-lookup"><span data-stu-id="e96e9-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="e96e9-141">Esse valor deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="e96e9-141">This value should be greater than zero.</span></span> <span data-ttu-id="e96e9-142">O padrão é 8.</span><span class="sxs-lookup"><span data-stu-id="e96e9-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="e96e9-143">Esse valor deve ser um inteiro maior que zero.</span><span class="sxs-lookup"><span data-stu-id="e96e9-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="e96e9-144">Se uma confirmação não for recebida após a última retransmissão, as falhas de canal.</span><span class="sxs-lookup"><span data-stu-id="e96e9-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="e96e9-145">Uma mensagem é considerada a serem transferidos se sua entrega no destinatário foi reconhecida pelo destinatário.</span><span class="sxs-lookup"><span data-stu-id="e96e9-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="e96e9-146">Se uma confirmação não foi recebida dentro de um determinado período de tempo para uma mensagem que foi transmitida, a infraestrutura retransmite automaticamente a mensagem.</span><span class="sxs-lookup"><span data-stu-id="e96e9-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="e96e9-147">A infraestrutura de tenta reenviar a mensagem no máximo o número de vezes especificado por essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="e96e9-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="e96e9-148">Se uma confirmação não for recebida após a última retransmissão, as falhas de canal.</span><span class="sxs-lookup"><span data-stu-id="e96e9-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="e96e9-149">A infraestrutura usa um algoritmo de retirada exponencial para determinar quando retransmitir, com base em um tempo de ida e volta média calculado.</span><span class="sxs-lookup"><span data-stu-id="e96e9-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="e96e9-150">Inicialmente, o tempo começa em 1 segundo antes de retransmissão e dobrar o atraso em cada tentativa, o que resulta em aproximadamente 8,5 minutos passar entre a primeira tentativa de transmissão e a última tentativa de retransmissão com.</span><span class="sxs-lookup"><span data-stu-id="e96e9-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="e96e9-151">O tempo para a primeira tentativa de retransmissão é ajustado de acordo com o tempo de ida e volta calculado e a ampliação resultante de tempo que levam as tentativas varia de acordo.</span><span class="sxs-lookup"><span data-stu-id="e96e9-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="e96e9-152">Isso permite que o tempo de retransmissão para adaptar-se dinamicamente a condições variáveis de rede.</span><span class="sxs-lookup"><span data-stu-id="e96e9-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="e96e9-153">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="e96e9-153">maxTransferWindowSize</span></span>|<span data-ttu-id="e96e9-154">Um inteiro que especifica o tamanho máximo do buffer.</span><span class="sxs-lookup"><span data-stu-id="e96e9-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="e96e9-155">Os valores válidos são de 1 a 4096 inclusivo.</span><span class="sxs-lookup"><span data-stu-id="e96e9-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="e96e9-156">No cliente, este atributo define o tamanho máximo do buffer usado por um canal confiável para manter as mensagens ainda não foram reconhecidas pelo destinatário.</span><span class="sxs-lookup"><span data-stu-id="e96e9-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="e96e9-157">A unidade da cota é uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="e96e9-157">The unit of the quota is a message.</span></span> <span data-ttu-id="e96e9-158">Se o buffer estiver cheio, mais operações de envio são bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="e96e9-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="e96e9-159">O receptor, este atributo define o tamanho máximo do buffer usado pelo canal para armazenar as mensagens de entrada ainda não foram enviadas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e96e9-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="e96e9-160">Se o buffer estiver cheio, outras mensagens serão descartadas silenciosamente pelo destinatário e exigem retransmissão pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="e96e9-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="e96e9-161">ordered</span><span class="sxs-lookup"><span data-stu-id="e96e9-161">ordered</span></span>|<span data-ttu-id="e96e9-162">Um valor booleano que especifica se as mensagens são garantidas de chegar na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="e96e9-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="e96e9-163">Se essa configuração for `false`, as mensagens podem chegar fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="e96e9-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="e96e9-164">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="e96e9-164">The default is `true`.</span></span>|  
|<span data-ttu-id="e96e9-165">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="e96e9-165">reliableMessagingVersion</span></span>|<span data-ttu-id="e96e9-166">Um valor válido de <xref:System.ServiceModel.ReliableMessagingVersion> que especifica a versão do WS-ReliableMessaging a ser usada.</span><span class="sxs-lookup"><span data-stu-id="e96e9-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e96e9-167">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e96e9-167">Child Elements</span></span>  
 <span data-ttu-id="e96e9-168">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e96e9-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e96e9-169">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e96e9-169">Parent Elements</span></span>  
  
|<span data-ttu-id="e96e9-170">Elemento</span><span class="sxs-lookup"><span data-stu-id="e96e9-170">Element</span></span>|<span data-ttu-id="e96e9-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="e96e9-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e96e9-172">\<associação ></span><span class="sxs-lookup"><span data-stu-id="e96e9-172">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e96e9-173">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="e96e9-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e96e9-174">Comentários</span><span class="sxs-lookup"><span data-stu-id="e96e9-174">Remarks</span></span>  
 <span data-ttu-id="e96e9-175">Sessões confiáveis fornecem recursos de sistema de mensagens confiável e sessões.</span><span class="sxs-lookup"><span data-stu-id="e96e9-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="e96e9-176">Mensagens confiáveis tentativas de comunicação em caso de falha e permite que as garantias de entrega, como na ordem de chegada de mensagens seja especificado.</span><span class="sxs-lookup"><span data-stu-id="e96e9-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="e96e9-177">Sessões de mantêm o estado dos clientes entre chamadas.</span><span class="sxs-lookup"><span data-stu-id="e96e9-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="e96e9-178">Esse elemento também fornece entrega de mensagens ordenadas.</span><span class="sxs-lookup"><span data-stu-id="e96e9-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="e96e9-179">Esta sessão implementada pode cruzar com intermediários SOAP e transporte.</span><span class="sxs-lookup"><span data-stu-id="e96e9-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="e96e9-180">Cada elemento de associação representa uma etapa de processamento ao enviar ou receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="e96e9-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="e96e9-181">Em tempo de execução, os elementos de associação criam as fábricas de canais e ouvintes que são necessários para construir as pilhas de canal de entrada e saída necessárias para enviar e receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="e96e9-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="e96e9-182">O `reliableSession` fornece uma camada opcional na pilha que pode estabelecer uma sessão confiável entre os pontos de extremidade e configurar o comportamento da sessão.</span><span class="sxs-lookup"><span data-stu-id="e96e9-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="e96e9-183">Para obter mais informações, consulte [sessões confiáveis](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="e96e9-183">For more information, see [Reliable Sessions](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e96e9-184">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e96e9-184">Example</span></span>  
 <span data-ttu-id="e96e9-185">O exemplo a seguir demonstra como configurar uma associação personalizada com vários transporte e mensagem elementos de codificação, especialmente habilitar sessões confiáveis, que mantém o estado do cliente e especifica as garantias de entrega em ordem.</span><span class="sxs-lookup"><span data-stu-id="e96e9-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="e96e9-186">Este recurso é configurado nos arquivos de configuração do aplicativo para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="e96e9-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="e96e9-187">O exemplo mostra a configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="e96e9-187">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
        <!-- specify customBinding binding and a binding configuration to use -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <reliableSession />  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e96e9-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e96e9-188">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [<span data-ttu-id="e96e9-189">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="e96e9-189">Reliable Sessions</span></span>](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 <span data-ttu-id="e96e9-190">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="e96e9-190">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="e96e9-191">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="e96e9-191">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="e96e9-192">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="e96e9-192">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="e96e9-193">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e96e9-193">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
