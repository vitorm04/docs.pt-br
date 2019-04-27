---
title: Práticas recomendadas para sessões confiáveis
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 1d9671e7e3124d535b66de8cd8468f76dcb32b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857980"
---
# <a name="best-practices-for-reliable-sessions"></a>Práticas recomendadas para sessões confiáveis

Este tópico discute as práticas recomendadas para sessões confiáveis.

## <a name="setting-maxtransferwindowsize"></a>Configuração MaxTransferWindowSize

Sessões confiáveis no Windows Communication Foundation (WCF) usam uma janela de transferência para manter as mensagens no cliente e o serviço. A propriedade configurável <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indica quantas mensagens a janela de transferência pode conter.

No remetente, isso indica quantas mensagens a janela de transferência pode conter enquanto aguarda as confirmações; no receptor, ele indica quantas mensagens para armazenar em buffer para o serviço.

Escolher o tamanho correto afeta a eficiência da rede e a capacidade ideal do serviço. As seções a seguir detalham o que considerar ao escolher um valor para essa propriedade e o impacto do valor.

O tamanho de janela de transferência padrão é oito mensagens.

### <a name="efficient-use-of-the-network"></a>Uso eficiente da rede

Nesse contexto, o termo *rede* corresponde a tudo o que usado como a base da comunicação entre um cliente (remetente) e um serviço (receptor). Isso inclui as conexões de transporte e qualquer intermediário ou pontes entre elas, incluindo HTTP proxies/firewalls ou roteadores SOAP.

Uso eficiente da rede garante a capacidade de rede estiver totalmente utilizada. O volume de dados que podem ser transferidos pela rede por segundo (*taxa de dados*) e o tempo necessário para transferir dados do remetente para o receptor (*latência*) afetar como efetivamente a rede é utilizado.

No remetente, a propriedade <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indica quantas mensagens sua janela de transferência pode conter enquanto aguarda as confirmações. Se a latência de rede é alta e para garantir que um remetente responsivo e a utilização da rede em vigor, você deve aumentar o tamanho da janela de transferência.

Por exemplo, mesmo se o remetente mantém o ritmo com taxa de dados, a latência pode ser alta se vários intermediários existem entre o remetente e receptor ou os dados devem passar por um intermediário com perdas ou rede. Portanto, o remetente possui a espera por confirmações para mensagens em sua janela de transferência antes de aceitar novas mensagens para enviar durante a transmissão. Quanto menor o buffer com alta latência, menos eficazes a utilização da rede. Por outro lado, muito alta um tamanho de janela de transferência pode afetar o serviço porque o serviço talvez precisem ser atualizado para a alta taxa de dados enviados pelo cliente.

### <a name="running-the-service-to-capacity"></a>Executando o serviço a capacidade

Quanto tempo a rede é usada com eficiência, idealmente, você também deseja o serviço seja executado na capacidade total ideal. A propriedade de tamanho de janela de transferência no receptor indica quantas mensagens que o receptor pode armazenar em buffer. Esse buffer de mensagem ajuda não só o controle de fluxo de rede, mas também permite que o serviço seja executado a capacidade total. Por exemplo, se o buffer é uma mensagem e as mensagens chegam mais rápido do que o serviço pode processá-las, em seguida, a rede pode ignorar mensagens e capacidade pode ser desperdiçada ou subutilizada.

Usando um buffer aumenta a disponibilidade do serviço que recebe e armazena uma mensagem em buffer ao processar a mensagem recebida anteriormente simultaneamente.

É recomendável que você use o mesmo `MaxTransferWindowSize` no remetente e receptor.

### <a name="enabling-flow-control"></a>Habilitar o controle de fluxo

*Controle de fluxo* é um mecanismo que garante que o remetente e receptor acompanhar uns aos outros, ou seja, as mensagens são consumidas e influenciadas tão rápido quanto eles são produzidos. O tamanho da janela de transferência no cliente e o serviço garante que o remetente e receptor dentro de uma janela razoável de sincronização.

É altamente recomendável que você defina a propriedade <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> para `true` quando você estiver usando uma sessão confiável entre um cliente WCF e um serviço WCF.

## <a name="setting-maxpendingchannels"></a>Configuração MaxPendingChannels

Ao escrever um serviço que permite a comunicação de sessão confiável de clientes diferentes, é possível ter vários clientes estabelecer uma sessão confiável para o serviço ao mesmo tempo. A resposta do serviço nessas situações depende o `MaxPendingChannels` propriedade.

Quando o remetente cria um canal de sessão confiável a um destinatário, um handshake entre eles estabelece uma sessão confiável. Depois que a sessão confiável foi estabelecida, o canal é colocado em uma fila de canal pendentes para aceitação pelo serviço. O `MaxPendingChannels` propriedade indica quantos canais podem ficar nesse estado.

É possível que o serviço esteja em um estado em que ele não pode aceitar mais canais. Se a fila está cheia, uma tentativa de estabelecer uma sessão confiável é rejeitada e o cliente deve repetir.

Também é possível que os canais pendentes na fila permanecem na fila por mais tempo. Nesse ínterim, um tempo limite de inatividade da sessão confiável pode ocorrer, fazendo com que o canal de fazer a transição para um estado de falha.

Ao escrever um serviço que atende a vários clientes simultaneamente, você deve definir um valor que é adequado para suas necessidades. Definindo um valor muito alto para o `MaxPendingChannels` propriedade afeta o conjunto de trabalho.

O valor padrão para <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> é quatro canais.

## <a name="reliable-sessions-and-hosting"></a>Sessões confiáveis e hospedagem

Quando web a hospedar um serviço que usa as sessões confiáveis, você deve ter as seguintes considerações importantes em mente:

- Sessões confiáveis são com monitoração de estado e o estado é mantido no AppDomain. Isso significa que todas as mensagens que fazem parte de uma sessão confiável devem ser processadas no mesmo AppDomain. Web farms e ambientes web onde o tamanho do farm ou do ambiente é maior que um nó não podem garantir essa restrição.

- Sessões confiáveis usando dois canais HTTP (por exemplo, usando `WsDualHttpBinding`) pode exigir mais do que o padrão de duas conexões por-cliente HTTP. Isso significa que uma sessão confiável duplex pode exigir até duas conexões cada forma porque mensagens simultâneas do aplicativo e o protocolo podem transferir a cada forma em um determinado momento. Sob certas condições, dependendo do padrão de troca de mensagem do serviço, isso significa que é possível que ocorra um deadlock um serviço hospedado na web usando HTTP duplo e sessões confiáveis. Para aumentar o número de conexões de HTTP permitidas por cliente, adicione o seguinte ao arquivo de configuração relevante (por exemplo, *Web. config* do serviço em questão):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  O valor da `maxconnection` atributo é o número de conexões necessárias. Nesse caso, o mínimo deve ser quatro conexões.
