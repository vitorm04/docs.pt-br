---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 95f6646041dc2dd7bae7691a0a9f748c844f50b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738751"
---
# \<reliableSession>
<span data-ttu-id="1c98d-101">Define a configuração para mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="1c98d-101">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="1c98d-102">Quando esse elemento é adicionado a uma associação personalizada, o canal resultante pode dar suporte a garantias de entrega exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="1c98d-102">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<reliableSession>**  
  
## <a name="syntax"></a><span data-ttu-id="1c98d-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c98d-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c98d-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1c98d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1c98d-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1c98d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c98d-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="1c98d-106">Attributes</span></span>  
  
|<span data-ttu-id="1c98d-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="1c98d-107">Attribute</span></span>|<span data-ttu-id="1c98d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c98d-109">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="1c98d-109">acknowledgementInterval</span></span>|<span data-ttu-id="1c98d-110">Um <xref:System.TimeSpan> valor que contém o intervalo de tempo máximo que o canal vai aguardar para enviar uma confirmação para as mensagens recebidas até esse ponto.</span><span class="sxs-lookup"><span data-stu-id="1c98d-110">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="1c98d-111">O padrão é 00:00:0.2.</span><span class="sxs-lookup"><span data-stu-id="1c98d-111">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="1c98d-112">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="1c98d-112">flowControlEnabled</span></span>|<span data-ttu-id="1c98d-113">Um valor booliano que indica se o controle de fluxo avançado, uma implementação específica da Microsoft de controle de fluxo para mensagens WS-Reliable, está ativado.</span><span class="sxs-lookup"><span data-stu-id="1c98d-113">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="1c98d-114">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="1c98d-114">The default is `true`.</span></span>|  
|<span data-ttu-id="1c98d-115">inactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="1c98d-115">inactivityTimeout</span></span>|<span data-ttu-id="1c98d-116">Um <xref:System.TimeSpan> valor que especifica a duração máxima em que o canal irá permitir que a outra parte de comunicação não envie mensagens antes de falhar o canal.</span><span class="sxs-lookup"><span data-stu-id="1c98d-116">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="1c98d-117">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1c98d-117">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="1c98d-118">A atividade em um canal é definida como recebendo mensagens de aplicativo ou de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="1c98d-118">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="1c98d-119">Essa propriedade controla a quantidade máxima de tempo para manter uma sessão inativa ativa.</span><span class="sxs-lookup"><span data-stu-id="1c98d-119">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="1c98d-120">Se o tempo mais longo passar sem atividade, a sessão será anulada pela infraestrutura e pelas falhas de canal.</span><span class="sxs-lookup"><span data-stu-id="1c98d-120">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="1c98d-121">**Observação:**  Não é necessário que o aplicativo envie mensagens periodicamente para manter a conexão ativa.</span><span class="sxs-lookup"><span data-stu-id="1c98d-121">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="1c98d-122">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="1c98d-122">maxPendingChannels</span></span>|<span data-ttu-id="1c98d-123">Um inteiro que especifica o número máximo de canais que podem aguardar a aceitação do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="1c98d-123">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="1c98d-124">Esse valor deve estar entre 1 e 16384, inclusive.</span><span class="sxs-lookup"><span data-stu-id="1c98d-124">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="1c98d-125">O padrão é 4.</span><span class="sxs-lookup"><span data-stu-id="1c98d-125">The default is 4.</span></span><br /><br /> <span data-ttu-id="1c98d-126">Os canais estão pendentes quando estão aguardando para serem aceitos.</span><span class="sxs-lookup"><span data-stu-id="1c98d-126">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="1c98d-127">Depois que esse limite for atingido, nenhum canal será criado.</span><span class="sxs-lookup"><span data-stu-id="1c98d-127">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="1c98d-128">Em vez disso, eles são colocados no modo pendente até que esse número fique inativo (aceitando canais pendentes).</span><span class="sxs-lookup"><span data-stu-id="1c98d-128">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="1c98d-129">Esse é um limite por fábrica.</span><span class="sxs-lookup"><span data-stu-id="1c98d-129">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="1c98d-130">Quando o limite é atingido e um aplicativo remoto tenta estabelecer uma nova sessão confiável, a solicitação é negada e a operação aberta que solicitou essa falha.</span><span class="sxs-lookup"><span data-stu-id="1c98d-130">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="1c98d-131">Esse limite não se aplica ao número de canais de saída pendentes.</span><span class="sxs-lookup"><span data-stu-id="1c98d-131">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="1c98d-132">maxRetryCount</span><span class="sxs-lookup"><span data-stu-id="1c98d-132">maxRetryCount</span></span>|<span data-ttu-id="1c98d-133">Um inteiro que especifica o número máximo de vezes que um canal confiável tenta retransmitir uma mensagem para a qual não recebeu uma confirmação, chamando Send em seu canal subjacente.</span><span class="sxs-lookup"><span data-stu-id="1c98d-133">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="1c98d-134">Esse valor deve ser maior que zero.</span><span class="sxs-lookup"><span data-stu-id="1c98d-134">This value should be greater than zero.</span></span> <span data-ttu-id="1c98d-135">O padrão é 8.</span><span class="sxs-lookup"><span data-stu-id="1c98d-135">The default is 8.</span></span><br /><br /> <span data-ttu-id="1c98d-136">Esse valor deve ser um número inteiro maior que zero.</span><span class="sxs-lookup"><span data-stu-id="1c98d-136">This value should be an integer greater than zero.</span></span> <span data-ttu-id="1c98d-137">Se uma confirmação não for recebida após a última retransmissão, as falhas de canal.</span><span class="sxs-lookup"><span data-stu-id="1c98d-137">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="1c98d-138">Uma mensagem será considerada para ser transferida se sua entrega no destinatário tiver sido confirmada pelo destinatário.</span><span class="sxs-lookup"><span data-stu-id="1c98d-138">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="1c98d-139">Se uma confirmação não tiver sido recebida dentro de um determinado período de tempo para uma mensagem que foi transmitida, a infraestrutura retransmitirá automaticamente a mensagem.</span><span class="sxs-lookup"><span data-stu-id="1c98d-139">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="1c98d-140">A infraestrutura tenta reenviar a mensagem para, no máximo, o número de vezes especificado por essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="1c98d-140">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="1c98d-141">Se uma confirmação não for recebida após a última retransmissão, as falhas de canal.</span><span class="sxs-lookup"><span data-stu-id="1c98d-141">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="1c98d-142">A infraestrutura usa um algoritmo de retirada exponencial para determinar quando retransmitir, com base em um tempo médio de ida e volta calculado.</span><span class="sxs-lookup"><span data-stu-id="1c98d-142">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="1c98d-143">O tempo inicialmente começa em 1 segundo antes da retransmissão e dobrando o atraso com cada tentativa, o que resulta em aproximadamente 8,5 minutos passando entre a primeira tentativa de transmissão e a última tentativa de retransmissão.</span><span class="sxs-lookup"><span data-stu-id="1c98d-143">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="1c98d-144">O tempo para a primeira tentativa de retransmissão é ajustado de acordo com o tempo de viagem de ida e volta calculado e o Stretch de tempo que essas tentativas levam variam de acordo.</span><span class="sxs-lookup"><span data-stu-id="1c98d-144">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="1c98d-145">Isso permite que o tempo de retransmissão se adapte dinamicamente a diferentes condições de rede.</span><span class="sxs-lookup"><span data-stu-id="1c98d-145">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="1c98d-146">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="1c98d-146">maxTransferWindowSize</span></span>|<span data-ttu-id="1c98d-147">Um inteiro que especifica o tamanho máximo do buffer.</span><span class="sxs-lookup"><span data-stu-id="1c98d-147">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="1c98d-148">Os valores válidos são de 1 a 4096, inclusive.</span><span class="sxs-lookup"><span data-stu-id="1c98d-148">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="1c98d-149">No cliente, esse atributo define o tamanho máximo do buffer usado por um canal confiável para manter as mensagens ainda não confirmadas pelo destinatário.</span><span class="sxs-lookup"><span data-stu-id="1c98d-149">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="1c98d-150">A unidade da cota é uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="1c98d-150">The unit of the quota is a message.</span></span> <span data-ttu-id="1c98d-151">Se o buffer estiver cheio, outras operações de envio serão bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="1c98d-151">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="1c98d-152">No receptor, esse atributo define o tamanho máximo do buffer usado pelo canal para armazenar as mensagens de entrada ainda não expedidas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1c98d-152">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="1c98d-153">Se o buffer estiver cheio, as mensagens adicionais serão silenciosamente descartadas pelo receptor e exigirão a retransmissão pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="1c98d-153">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="1c98d-154">ordered</span><span class="sxs-lookup"><span data-stu-id="1c98d-154">ordered</span></span>|<span data-ttu-id="1c98d-155">Um booliano que especifica se as mensagens são garantidas de chegar na ordem em que foram enviadas.</span><span class="sxs-lookup"><span data-stu-id="1c98d-155">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="1c98d-156">Se essa configuração for `false` , as mensagens poderão chegar fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="1c98d-156">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="1c98d-157">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="1c98d-157">The default is `true`.</span></span>|  
|<span data-ttu-id="1c98d-158">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="1c98d-158">reliableMessagingVersion</span></span>|<span data-ttu-id="1c98d-159">Um valor válido de <xref:System.ServiceModel.ReliableMessagingVersion> que especifica a versão WS-ReliableMessaging a ser usada.</span><span class="sxs-lookup"><span data-stu-id="1c98d-159">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c98d-160">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1c98d-160">Child Elements</span></span>  
 <span data-ttu-id="1c98d-161">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1c98d-161">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c98d-162">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1c98d-162">Parent Elements</span></span>  
  
|<span data-ttu-id="1c98d-163">Elemento</span><span class="sxs-lookup"><span data-stu-id="1c98d-163">Element</span></span>|<span data-ttu-id="1c98d-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c98d-164">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="1c98d-165">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1c98d-165">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c98d-166">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c98d-166">Remarks</span></span>  
 <span data-ttu-id="1c98d-167">As sessões confiáveis fornecem recursos para mensagens e sessões confiáveis.</span><span class="sxs-lookup"><span data-stu-id="1c98d-167">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="1c98d-168">A Reliable Messaging repete a comunicação em caso de falha e permite que as garantias de entrega, como a chegada da ordem das mensagens a serem especificadas.</span><span class="sxs-lookup"><span data-stu-id="1c98d-168">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="1c98d-169">As sessões mantêm o estado para clientes entre chamadas.</span><span class="sxs-lookup"><span data-stu-id="1c98d-169">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="1c98d-170">Esse elemento também fornece opcionalmente a entrega de mensagens ordenadas.</span><span class="sxs-lookup"><span data-stu-id="1c98d-170">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="1c98d-171">Essa sessão implementada pode cruzar o SOAP e transportar intermediários.</span><span class="sxs-lookup"><span data-stu-id="1c98d-171">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="1c98d-172">Cada elemento de associação representa uma etapa de processamento ao enviar ou receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="1c98d-172">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="1c98d-173">Em tempo de execução, os elementos de associação criam fábricas e ouvintes de canal que são necessários para criar pilhas de canal de entrada e de saída necessárias para enviar e receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="1c98d-173">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="1c98d-174">O `reliableSession` fornece uma camada opcional na pilha que pode estabelecer uma sessão confiável entre pontos de extremidade e configurar o comportamento dessa sessão.</span><span class="sxs-lookup"><span data-stu-id="1c98d-174">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="1c98d-175">Para obter mais informações, consulte [sessões confiáveis](../../../wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="1c98d-175">For more information, see [Reliable Sessions](../../../wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c98d-176">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c98d-176">Example</span></span>  
 <span data-ttu-id="1c98d-177">O exemplo a seguir demonstra como configurar uma associação personalizada com vários elementos de codificação de transporte e de mensagem, especialmente permitindo sessões confiáveis, que mantém o estado do cliente e especifica garantias de entrega em ordem.</span><span class="sxs-lookup"><span data-stu-id="1c98d-177">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="1c98d-178">Esse recurso é configurado nos arquivos de configuração do aplicativo para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="1c98d-178">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="1c98d-179">O exemplo mostra a configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="1c98d-179">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="1c98d-180">Confira também</span><span class="sxs-lookup"><span data-stu-id="1c98d-180">See also</span></span>

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [<span data-ttu-id="1c98d-181">Sessões confiáveis</span><span class="sxs-lookup"><span data-stu-id="1c98d-181">Reliable Sessions</span></span>](../../../wcf/feature-details/reliable-sessions.md)
- [<span data-ttu-id="1c98d-182">Associações</span><span class="sxs-lookup"><span data-stu-id="1c98d-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1c98d-183">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="1c98d-183">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1c98d-184">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="1c98d-184">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
