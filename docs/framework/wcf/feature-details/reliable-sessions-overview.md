---
title: "Visão geral de sessões confiáveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d2749188214f3f68ee3ed5df87fc0aa7cac604d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-sessions-overview"></a>Visão geral de sessões confiáveis

[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Mensagens confiáveis do SOAP oferece confiabilidade de transferência de mensagem de ponta a ponta entre pontos de extremidade SOAP. Ele faz isso em redes que não são confiáveis pelo superar falhas de transporte e de nível de mensagem SOAP. Em particular, ele fornece entrega baseada em sessão, único e (opcionalmente) ordenada para mensagens enviadas em SOAP ou transporte intermediários. Fornece entrega baseada em sessão para o agrupamento de mensagens em uma sessão com a ordenação opcional das mensagens.

Este tópico descreve as sessões confiáveis, como e quando usá-los e como protegê-los.

## <a name="wcf-reliable-sessions"></a>Sessões confiáveis do WCF

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]sessões confiáveis é uma implementação de SOAP confiável conforme definido pelo protocolo WS-ReliableMessaging de mensagens.

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Mensagens confiáveis do SOAP fornece uma sessão confiável de ponta a ponta entre dois pontos de extremidade, independentemente do número ou tipo de intermediários que separam os pontos de extremidade de mensagens. Isso inclui qualquer intermediários de transporte que não usam o SOAP (por exemplo, proxies HTTP) ou intermediários que usam SOAP (por exemplo, roteadores baseados em SOAP ou pontes) que são necessários para mensagens entre os pontos de extremidade. Oferece suporte a um canal de sessão confiável *interativo* comunicação para que os serviços conectados por esse canal executadas simultaneamente e as mensagens do exchange e o processo sob condições de baixa latência, ou seja, em relativamente curtos intervalos de tempo. Esse acoplamento significa que esses componentes progredir juntos ou falham juntas, portanto não há nenhum isolamento fornecido entre eles.

Uma sessão confiável mascara dois tipos de falhas:

- Falhas de nível de mensagem SOAP, que inclui mensagens perdidas ou duplicadas e as mensagens que chegam em uma ordem diferente da ordem em que foram enviadas.

- Falhas de transporte.

Uma sessão confiável implementa o protocolo WS-ReliableMessaging e uma janela de transferência na memória para falhas de máscara de nível de mensagem SOAP e restabelece as conexões no caso de falhas de transporte.

Uma sessão confiável fornece para mensagens SOAP, o TCP fornece para pacotes IP. Uma conexão de soquete TCP fornece uma forma singular, na ordem de transferência de pacotes IP entre os nós. O canal confiável fornece o mesmo tipo de transferência confiável, mas ele é diferente de confiabilidade de soquete TCP das seguintes maneiras:

- A confiabilidade é a mensagem SOAP nível, não para um pacote de tamanho arbitrário de bytes.

- A confiabilidade é neutro de transporte, não apenas para a transferência via TCP.

- A confiabilidade não está vinculada a uma sessão de transporte específico (por exemplo, a sessão que fornece uma conexão TCP) e pode usar várias sessões de transporte simultaneamente ou sequencialmente durante o tempo de vida da sessão confiável.

- A sessão confiável está entre o remetente e o destinatário pontos de extremidade SOAP, independentemente do número de conexões de transporte necessárias para conectividade entre eles. Em resumo, a confiabilidade TCP termina em que a conexão de transporte termina, enquanto uma sessão confiável oferece confiabilidade de ponta a ponta.

## <a name="reliable-sessions-and-bindings"></a>Associações e sessões confiáveis

Como mencionado anteriormente, uma sessão confiável é neutro de transporte. Além disso, você pode estabelecer uma sessão confiável em vários padrões de troca de mensagens, como solicitação-resposta ou duplex. Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessão confiável é exposta como uma propriedade de um conjunto de associações.

Use uma sessão confiável nos pontos de extremidade que usam:

- Associações de transporte com base em HTTP padrão:

  - `WsHttpBinding`e expor contratos unidirecionais ou solicitação-resposta.

  - Ao usar a sessão confiável em um contrato de serviço unidirecional simples ou de solicitação-resposta.

  - `WsDualHttpBinding`e expor os contratos unidirecionais, solicitação / resposta ou duplex.

  - `WsFederationHttpBinding`e expor contratos unidirecionais ou solicitação-resposta.

- Associações de transporte com base em TCP padrão:

  - `NetTcpBinding`e expor os contratos unidirecionais, solicitação resposta ou duplex.

Usar uma sessão confiável em quaisquer outras associações, criando uma associação personalizada, como HTTPS (para obter mais informações sobre problemas, consulte <a href="#reliable-sessions-and-security">sessões confiáveis e segurança</a>) ou uma associação de pipe nomeado.

Você pode empilhar uma sessão confiável em diferentes tipos de canais subjacente e a forma de canal de sessão confiável resultante varia. No cliente e o servidor, o tipo de canal de sessão confiável com suporte depende do tipo de canal subjacente usado. A tabela a seguir lista os tipos de canais de sessão com suporte no cliente, como uma função do tipo de canal subjacente.

| Suporte para tipos de canal de sessão confiável &#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Sim               | Sim                      | Sim              | Sim                     |
| `IRequestSessionChannel`                        | Sim               | Sim                      | Não               | Não                      |
| `IDuplexSessionChannel`                         | Não                | Não                       | Sim              | Sim                     |

&#8224; Os tipos de canal com suporte são os valores disponíveis para genérica `TChannel` valor de parâmetro que é passado para o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> método.

A tabela a seguir lista os tipos de canais de sessão com suporte no servidor como uma função do tipo de canal subjacente.

| Suporte para tipos de canal de sessão confiável &#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Sim             | Sim                    | Sim              | Sim                     |
| `IReplySessionChannel`                          | Sim             | Sim                    | Não               | Não                      |
| `IDuplexSessionChannel`                         | Não              | Não                     | Sim              | Sim                     |

&#8225; Os tipos de canal com suporte são os valores disponíveis para genérica `TChannel` valor de parâmetro que é passado para o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> método.

## <a name="reliable-sessions-and-security"></a>Segurança e sessões confiáveis

Proteger uma sessão confiável é importante para garantir que as partes da comunicação (cliente e serviço) são autenticadas e que as mensagens trocadas na sessão não são alteradas. Além disso, é importante garantir a integridade de cada sessão confiável individual. Uma sessão confiável é protegida por associação a um contexto de segurança representado e gerenciado por um canal de sessão de segurança. O canal de segurança fornece uma sessão de segurança. Tokens de segurança trocados durante o estabelecimento da sessão são usados para proteger as mensagens na sessão confiável.

Quando uma sessão confiável está sobre TCP-S, a sessão TCP está vinculada à sessão confiável. Portanto, a segurança de transporte garante que a segurança também está associada à sessão confiável. Nesse caso, restabelecimento da conexão está desativado.

A única exceção é quando usando HTTPS. A sessão de Secure Sockets Layer (SSL) não está associada à sessão confiável. Isso impõe uma ameaça porque as sessões que estão compartilhando um contexto de segurança (a sessão SSL) não estão protegidas uns dos outros; Isso pode ou não pode ser uma ameaça real dependendo do aplicativo.

## <a name="using-reliable-sessions"></a>Usando sessões confiáveis

Para usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessões confiáveis, crie um ponto de extremidade com uma associação que dá suporte a uma sessão confiável. Use uma das associações fornecidas pelo sistema que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece com a sessão confiável habilitada ou criar sua própria associação personalizada que faz isso.

As associações definidas pelo sistema que oferece suporte e habilitam uma sessão confiável por padrão incluem:

- <xref:System.ServiceModel.WSDualHttpBinding>

As associações fornecidas pelo sistema que oferecem suporte a uma sessão confiável como uma opção, mas não habilitado por padrão incluem:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Para obter um exemplo de como criar uma associação personalizada, consulte [como: criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

Para obter uma discussão de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações que oferecem suporte a sessões confiáveis, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Quando usar sessões confiáveis

É importante entender quando usar sessões confiáveis em seu aplicativo. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte a sessões confiáveis entre pontos de extremidade que estão ativos e ativo ao mesmo tempo. Se seu aplicativo requer que um dos pontos de extremidade ficar indisponível por um período de duração, em seguida, usar filas para alcançar a confiabilidade.

Se o cenário exigir dois pontos de extremidade conectados por TCP, TCP pode ser suficiente para fornecer as trocas de mensagens confiável. Embora, não é necessário usar uma sessão confiável, como TCP garante que os pacotes de chegarem na ordem e apenas uma vez.

Se seu cenário de qualquer uma das características a seguir, você deve seriamente considere usar uma sessão confiável.

- Intermediários SOAP, como roteadores SOAP

- Intermediários de proxy ou pontes de transporte

- Conectividade intermitentes

- Sessões sobre HTTP

## <a name="see-also"></a>Consulte também

[Usando associações para configurar serviços e clientes](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
[Sessão confiável de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
