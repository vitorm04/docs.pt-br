---
title: "Práticas recomendadas para sessões confiáveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6e20b5cf02e7aef31127bb88e27e21965a192a6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="best-practices-for-reliable-sessions"></a>Práticas recomendadas para sessões confiáveis

Este tópico discute as práticas recomendadas para sessões confiáveis.

## <a name="setting-maxtransferwindowsize"></a>Configuração MaxTransferWindowSize

Sessões confiáveis em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usam uma janela de transferência para manter as mensagens no cliente e no serviço. A propriedade configurável <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indica quantas mensagens pode manter a janela de transferência.

O remetente, isso indica quantas mensagens pode manter a janela de transferência durante a espera por confirmações; no destinatário, ele indica quantas mensagens para armazenar em buffer para o serviço.

Escolher o tamanho correto afeta a eficiência da rede e a capacidade ideal do serviço. As seções a seguir detalham o que considerar ao escolher um valor para essa propriedade e o impacto do valor.

O tamanho de janela de transferência padrão é de oito mensagens.

### <a name="efficient-use-of-the-network"></a>Uso eficiente da rede

Nesse contexto, o termo *rede* corresponde a todos os itens usados como a base de comunicação entre um cliente (remetente) e um serviço (destinatário). Isso inclui as conexões de transporte e qualquer intermediário ou pontes entre, incluindo roteadores SOAP ou HTTP proxies/firewalls.

Uso eficiente da rede garante que a capacidade de rede totalmente é usada. O volume de dados que podem ser transferidos pela rede por segundo (*taxa de dados*) e o tempo necessário para transferir dados do remetente para o receptor (*latência*) afetar como efetivamente a rede é utilizada.

No remetente, a propriedade <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indica a quantidade de mensagens pode conter sua janela de transferência durante a espera por confirmações. Se a latência de rede for alta e para garantir um remetente responsivo e utilização de rede eficaz, você deve aumentar o tamanho da janela de transferência.

Por exemplo mesmo se o remetente mantém o ritmo com taxa de dados, latência pode ser alta se existirem vários intermediários entre o remetente e o destinatário ou os dados devem passar por meio de um intermediário com perdas ou rede. Portanto, o remetente tem espera por confirmações para mensagens em sua janela de transferência antes de aceitar novas mensagens para enviar o percurso. Quanto menor o buffer com alta latência, menos eficazes a utilização da rede. Por outro lado, muito alta um tamanho de janela de transferência pode afetar o serviço porque o serviço talvez precise ficar em dia com alta taxa de dados enviados pelo cliente.

### <a name="running-the-service-to-capacity"></a>Executando o serviço de capacidade

Quanto a rede é usada com eficiência, idealmente, você também deseja o serviço para ser executado na capacidade total ideal. A propriedade de tamanho de janela de transferência no receptor indica quantas mensagens que o receptor pode buffer. Esse buffer de mensagem ajuda não só o controle de fluxo de rede, mas também permite que o serviço seja executado com capacidade total. Por exemplo, se o buffer é uma mensagem e as mensagens chegam mais rápido do que o serviço pode processá-las, em seguida, a rede pode receber mensagens de e capacidade pode ser perdida ou subutilizada.

Usar um buffer aumenta a disponibilidade do serviço como simultaneamente recebe e armazena em buffer uma mensagem durante o processamento das mensagens recebidas anteriormente.

É recomendável que você use o mesmo `MaxTransferWindowSize` no remetente e receptor.

### <a name="enabling-flow-control"></a>Habilitar o controle de fluxo

*Controle de fluxo* é um mecanismo que garante que o remetente e o destinatário acompanhar entre si, ou seja, as mensagens são consumidas e tratadas tão rápido quanto eles são produzidos. O tamanho da janela de transferência no cliente e serviço garante que o remetente e o destinatário dentro de uma janela razoável de sincronização.

É altamente recomendável que você defina a propriedade <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> para `true` quando você estiver usando uma sessão confiável entre um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.

## <a name="setting-maxpendingchannels"></a>Configuração MaxPendingChannels

Ao escrever um serviço que permite a comunicação de sessão confiável de diferentes clientes, é possível ter vários clientes estabelecer uma sessão confiável para o serviço ao mesmo tempo. A resposta do serviço nessas situações depende do `MaxPendingChannels` propriedade.

Quando o remetente cria um canal de sessão confiável a um destinatário, um handshake entre eles estabelece uma sessão confiável. Após o estabelecimento da sessão confiável, o canal é colocado em uma fila pendente de canal para aceitação pelo serviço. O `MaxPendingChannels` propriedade indica quantos canais podem ser nesse estado.

É possível que o serviço esteja em um estado em que ele não pode aceitar mais canais. Se a fila está cheia, uma tentativa de estabelecer uma sessão confiável é rejeitada e o cliente deve repetir.

Também é possível que os canais pendentes na fila de permanecem na fila por mais tempo. Enquanto isso, um tempo limite de inatividade na sessão confiável pode ocorrer, fazendo com que o canal a transição para um estado de falha.

Ao escrever um serviço que atende a vários clientes simultaneamente, você deve definir um valor que é adequado para suas necessidades. Definindo um valor muito alto para o `MaxPendingChannels` propriedade afeta o conjunto de trabalho.

O valor padrão para <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> é quatro canais.

## <a name="reliable-sessions-and-hosting"></a>Sessões confiáveis e hospedagem

Quando web hospeda um serviço que usa sessões confiáveis, você deve ter as seguintes considerações importantes em mente:

- Sessões confiáveis são com monitoração de estado e o estado é mantido no AppDomain. Isso significa que todas as mensagens que fazem parte de uma sessão confiável devem ser processadas no mesmo AppDomain. Web farms e ambientes web onde o tamanho do farm ou do ambiente é maior do que um nó não podem garantir essa restrição.

- Sessões confiáveis usando dois canais HTTP (por exemplo, usando `WsDualHttpBinding`) pode exigir mais do que o padrão de duas conexões por-cliente HTTP. Isso significa que uma sessão segura duplex pode exigir até duas conexões cada forma porque mensagens simultâneas do aplicativo e o protocolo podem transferir a cada forma em um determinado momento. Em determinadas condições, dependendo do padrão de troca de mensagens do serviço, isso significa que é possível deadlock um serviço hospedado da web usando HTTP dupla e sessões confiáveis. Para aumentar o número de conexões HTTP permitidas por cliente, adicione o seguinte ao arquivo de configuração relevantes (por exemplo, *Web. config* do serviço em questão):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  O valor de `maxconnection` atributo é o número de conexões necessárias. Nesse caso, o mínimo deve ser quatro conexões.
