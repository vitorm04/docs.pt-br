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
# <a name="ltreliablesessiongt"></a>&lt;reliableSession&gt;
Define a configuração para mensagens WS-Reliable. Quando esse elemento é adicionado a uma associação personalizada, o canal resultante pode dar suporte a exatamente-uma vez garantias de entrega.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<reliableSession >  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|AcknowledgementInterval|Um <xref:System.TimeSpan> que contém o intervalo de tempo máximo que o canal vai esperar para enviar uma confirmação de mensagens recebidas até aquele ponto. O padrão é 00:00:0.2.|  
|FlowControlEnabled|Um valor booliano que indica se o controle de fluxo avançado, uma implementação específica da Microsoft de controle de fluxo de mensagens WS-Reliable, é ativado. O padrão é `true`.|  
|InactivityTimeout|Um <xref:System.TimeSpan> que especifica a duração máxima que o canal vai permitir que a outra parte da comunicação para não enviar qualquer mensagem, antes de haver falha no canal. O padrão é 00:10:00.<br /><br /> Atividade em um canal é definida como receber mensagens de infraestrutura ou de um aplicativo. Essa propriedade controla a quantidade máxima de tempo para manter uma sessão inativa ativa. Se passa mais tempo sem nenhuma atividade, a sessão é anulada, a infraestrutura e as falhas de canal. **Observação:** não é necessário para o aplicativo para enviar mensagens para manter a conexão ativa, periodicamente.|  
|MaxPendingChannels|Um inteiro que especifica o número máximo de canais que podem esperar no ouvinte para serem aceitos. Esse valor deve estar entre 1 a 16384 inclusivo. O padrão é 4.<br /><br /> Os canais estão pendentes quando estão aguardando para serem aceitos. Quando esse limite é atingido, não há canais são criados. Em vez disso, eles são colocados no pendentes modo até que esse número chegar para baixo (aceitando pendentes canais). Este é um limite por fábrica.<br /><br /> Quando o limite for atingido, e um aplicativo remoto tenta estabelecer uma nova sessão confiável, a solicitação será negada e a operação de abertura que gerou este falhas. Esse limite não se aplica ao número de pendente canais de saída.|  
|MaxRetryCount|Um inteiro que especifica o número máximo de vezes que um canal confiável tenta retransmitir uma mensagem não recebeu uma confirmação, chamando Send em seu canal subjacente.<br /><br /> Esse valor deve ser maior que zero. O padrão é 8.<br /><br /> Esse valor deve ser um inteiro maior que zero. Se uma confirmação não for recebida após a última retransmissão, as falhas de canal.<br /><br /> Uma mensagem é considerada a serem transferidos se sua entrega no destinatário foi reconhecida pelo destinatário.<br /><br /> Se uma confirmação não foi recebida dentro de um determinado período de tempo para uma mensagem que foi transmitida, a infraestrutura retransmite automaticamente a mensagem. A infraestrutura de tenta reenviar a mensagem no máximo o número de vezes especificado por essa propriedade. Se uma confirmação não for recebida após a última retransmissão, as falhas de canal.<br /><br /> A infraestrutura usa um algoritmo de retirada exponencial para determinar quando retransmitir, com base em um tempo de ida e volta média calculado. Inicialmente, o tempo começa em 1 segundo antes de retransmissão e dobrar o atraso em cada tentativa, o que resulta em aproximadamente 8,5 minutos passar entre a primeira tentativa de transmissão e a última tentativa de retransmissão com. O tempo para a primeira tentativa de retransmissão é ajustado de acordo com o tempo de ida e volta calculado e a ampliação resultante de tempo que levam as tentativas varia de acordo. Isso permite que o tempo de retransmissão para adaptar-se dinamicamente a condições variáveis de rede.|  
|MaxTransferWindowSize|Um inteiro que especifica o tamanho máximo do buffer. Os valores válidos são de 1 a 4096 inclusivo.<br /><br /> No cliente, este atributo define o tamanho máximo do buffer usado por um canal confiável para manter as mensagens ainda não foram reconhecidas pelo destinatário. A unidade da cota é uma mensagem. Se o buffer estiver cheio, mais operações de envio são bloqueadas.<br /><br /> O receptor, este atributo define o tamanho máximo do buffer usado pelo canal para armazenar as mensagens de entrada ainda não foram enviadas para o aplicativo. Se o buffer estiver cheio, outras mensagens serão descartadas silenciosamente pelo destinatário e exigem retransmissão pelo cliente.|  
|ordered|Um valor booleano que especifica se as mensagens são garantidas de chegar na ordem em que foram enviadas. Se essa configuração for `false`, as mensagens podem chegar fora de ordem. O padrão é `true`.|  
|ReliableMessagingVersion|Um valor válido de <xref:System.ServiceModel.ReliableMessagingVersion> que especifica a versão do WS-ReliableMessaging a ser usada.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Sessões confiáveis fornecem recursos de sistema de mensagens confiável e sessões. Mensagens confiáveis tentativas de comunicação em caso de falha e permite que as garantias de entrega, como na ordem de chegada de mensagens seja especificado. Sessões de mantêm o estado dos clientes entre chamadas. Esse elemento também fornece entrega de mensagens ordenadas. Esta sessão implementada pode cruzar com intermediários SOAP e transporte.  
  
 Cada elemento de associação representa uma etapa de processamento ao enviar ou receber mensagens. Em tempo de execução, os elementos de associação criam as fábricas de canais e ouvintes que são necessários para construir as pilhas de canal de entrada e saída necessárias para enviar e receber mensagens. O `reliableSession` fornece uma camada opcional na pilha que pode estabelecer uma sessão confiável entre os pontos de extremidade e configurar o comportamento da sessão.  
  
 Para obter mais informações, consulte [sessões confiáveis](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como configurar uma associação personalizada com vários transporte e mensagem elementos de codificação, especialmente habilitar sessões confiáveis, que mantém o estado do cliente e especifica as garantias de entrega em ordem. Este recurso é configurado nos arquivos de configuração do aplicativo para o cliente e o serviço. O exemplo mostra a configuração do serviço.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [Sessões confiáveis](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
