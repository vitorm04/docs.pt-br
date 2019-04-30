---
title: Visão geral de sessões confiáveis
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 6dd90ef800daf236d77c419d48c0857ac2d78aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962650"
---
# <a name="reliable-sessions-overview"></a>Visão geral de sessões confiáveis

Mensagens confiáveis do Windows Communication Foundation (WCF) SOAP fornece confiabilidade de transferência de mensagem de ponta a ponta entre pontos de extremidade SOAP. Ele faz isso em redes que não são confiáveis por superar falhas de transporte e de nível de mensagem SOAP. Em particular, ele fornece entrega baseada em sessão, única e (opcionalmente) ordenada para as mensagens enviadas em intermediários SOAP ou transporte. Fornece entrega baseada em sessão para o agrupamento de mensagens em uma sessão com a ordenação opcional das mensagens.

Este tópico descreve as sessões confiáveis, como e quando usá-los e como protegê-los.

## <a name="wcf-reliable-sessions"></a>Sessões confiáveis do WCF

Sessões confiáveis do WCF é uma implementação de SOAP reliable messaging conforme definido pelo protocolo WS-ReliableMessaging.

O sistema de mensagens confiável do WCF SOAP fornece uma sessão confiável de ponta a ponta entre dois pontos de extremidade, independentemente do número ou tipo de intermediários que separam os pontos de extremidade de mensagens. Isso inclui qualquer intermediário de transporte que não usa SOAP (por exemplo, proxies HTTP) ou intermediários que usam o SOAP (por exemplo, roteadores baseados em SOAP ou pontes) que são necessários para que as mensagens fluam entre os pontos de extremidade. Dá suporte a um canal de sessão confiável *interativa* comunicação para que os serviços conectados por esse canal são executados simultaneamente e as mensagens do exchange e o processo sob condições de baixa latência, ou seja, dentro do relativamente curtos intervalos de tempo. Esse acoplamento significa que esses componentes progredir juntos ou falham juntas, portanto, não há nenhum isolamento fornecido entre eles.

Uma sessão confiável mascara a dois tipos de falhas:

- Falhas de nível de mensagem SOAP, que inclui mensagens perdidas ou duplicadas e as mensagens que chegam em uma ordem diferente da ordem em que foram enviadas.

- Falhas de transporte.

Uma sessão confiável implementa o protocolo WS-ReliableMessaging e uma janela de transferência na memória para falhas de nível de mensagem SOAP de máscara e restabelece as conexões no caso de falhas de transporte.

Uma sessão confiável fornece para mensagens SOAP que TCP fornece para pacotes IP. Uma conexão de soquete TCP fornece uma única, em ordem e a transferência de pacotes IP entre os nós. O canal confiável fornece o mesmo tipo de transferência confiável, mas ele difere da confiabilidade de soquete TCP das seguintes maneiras:

- A confiabilidade é a mensagem SOAP nível, não para um pacote arbitrariamente tamanho de bytes.

- A confiabilidade é transporte neutro, não apenas para transferência de TCP.

- A confiabilidade não está vinculada a uma sessão de transporte específico (por exemplo, a sessão fornece uma conexão TCP) e pode usar várias sessões de transporte simultaneamente ou sequencialmente durante a vida útil da sessão confiável.

- A sessão confiável está entre o remetente e receptor pontos de extremidade SOAP, independentemente do número de conexões de transporte necessários para a conectividade entre eles. Em resumo, a confiabilidade TCP termina em que a conexão de transporte termina, enquanto uma sessão confiável fornece confiabilidade de ponta a ponta.

## <a name="reliable-sessions-and-bindings"></a>Associações e sessões confiáveis

Como mencionado anteriormente, uma sessão confiável é neutro de transporte. Além disso, você pode estabelecer uma sessão confiável ao longo de muitos padrões de troca de mensagem, como solicitação-resposta ou duplex. Uma sessão confiável do WCF é exposta como uma propriedade de um conjunto de associações.

Use uma sessão confiável nos pontos de extremidade que usam:

- Associações padrão de transporte com base em HTTP:

  - `WsHttpBinding` e expõem contratos unidirecionais ou solicitação-resposta.

  - Ao usar a sessão confiável em uma solicitação-resposta ou contrato de serviço unidirecional simples.

  - `WsDualHttpBinding` e expõem contratos unidirecionais, solicitação-resposta ou duplex.

  - `WsFederationHttpBinding` e expõem contratos unidirecionais ou solicitação-resposta.

- Associações de transporte com base em TCP padrão:

  - `NetTcpBinding` e expõem contratos unidirecionais, solicitação de resposta ou duplex.

Usar uma sessão confiável em quaisquer outras associações, criando uma ligação personalizada, como HTTPS (para obter mais informações sobre problemas, consulte <a href="#reliable-sessions-and-security">segurança e sessões confiáveis</a>) ou uma associação de pipe nomeado.

Você pode empilhar uma sessão confiável em diferentes tipos de canais subjacente e a forma de canal de sessão confiável resultante varia. No cliente e o servidor, o tipo de canal de sessão confiável com suporte depende do tipo de canal subjacente usado. A tabela a seguir lista os tipos de canais de sessão com suporte no cliente como uma função do tipo de canal subjacente.

| Suporte para tipos de canais de sessão confiável&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Sim               | Sim                      | Sim              | Sim                     |
| `IRequestSessionChannel`                        | Sim               | Sim                      | Não               | Não                      |
| `IDuplexSessionChannel`                         | Não                | Não                       | Sim              | Sim                     |

&#8224;Os tipos de canal com suporte são os valores disponíveis para o genérico `TChannel` valor de parâmetro que é passado para o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> método.

A tabela a seguir lista os tipos de canais de sessão com suporte no servidor como uma função do tipo de canal subjacente.

| Suporte para tipos de canais de sessão confiável&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Sim             | Sim                    | Sim              | Sim                     |
| `IReplySessionChannel`                          | Sim             | Sim                    | Não               | Não                      |
| `IDuplexSessionChannel`                         | Não              | Não                     | Sim              | Sim                     |

&#8225;Os tipos de canal com suporte são os valores disponíveis para o genérico `TChannel` valor de parâmetro que é passado para o <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> método.

## <a name="reliable-sessions-and-security"></a>Segurança e sessões confiáveis

Proteger uma sessão confiável é importante garantir que as partes da comunicação (cliente e serviço) são autenticadas e que as mensagens trocadas na sessão não são alteradas. Além disso, é importante garantir a integridade de cada sessão confiável individual. Uma sessão confiável é protegida pela associação a um contexto de segurança representado e gerenciado por um canal de sessão de segurança. O canal de segurança fornece uma sessão de segurança. Tokens de segurança trocados durante o estabelecimento da sessão, em seguida, são usados para proteger as mensagens na sessão confiável.

Quando uma sessão confiável está sobre TCP-S, a sessão TCP é vinculada à sessão confiável. Portanto, a segurança de transporte garante a segurança também está vinculada para a sessão confiável. Nesse caso, restabelecimento da conexão é desativado.

A única exceção é ao usar HTTPS. A sessão de Secure Sockets Layer (SSL) não está associada à sessão confiável. Isso impõe uma ameaça, porque as sessões que estão compartilhando um contexto de segurança (a sessão SSL) não estão protegidas uns dos outros; Isso pode ou não ser realmente uma ameaça, dependendo do aplicativo.

## <a name="using-reliable-sessions"></a>Usando sessões confiáveis

Para usar sessões confiáveis do WCF, crie um ponto de extremidade com uma associação que dá suporte a uma sessão confiável. Use uma das associações fornecidas pelo sistema que o WCF fornece com a sessão confiável habilitada ou criar sua própria associação personalizada que faz isso.

As associações definidas pelo sistema que dão suporte e habilitam uma sessão confiável por padrão incluem:

- <xref:System.ServiceModel.WSDualHttpBinding>

As associações fornecidas pelo sistema que dão suporte a uma sessão confiável como uma opção, mas não habilitar por padrão incluem:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Para obter um exemplo de como criar uma ligação personalizada, consulte [como: Criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

Para uma discussão sobre associações do WCF que dão suporte a sessões confiáveis, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Quando usar sessões confiáveis

É importante entender quando usar sessões confiáveis em seu aplicativo. O WCF oferece suporte a sessões confiáveis entre pontos de extremidade que estão ativas e ativo ao mesmo tempo. Se seu aplicativo requer que um dos pontos de extremidade ficar indisponível por um período de duração, em seguida, usar filas para atingir a confiabilidade.

Se o cenário exigir dois pontos de extremidade conectados por TCP, TCP pode ser suficiente para fornecer as trocas de mensagens confiável. No entanto, ele não é necessário usar uma sessão confiável, como TCP garante que os pacotes chegam na ordem e apenas uma vez.

Se seu cenário tenha qualquer uma das seguintes características, você deve seriamente considere usar uma sessão confiável.

- Intermediários do SOAP, como roteadores SOAP

- Intermediários de proxy ou pontes de transporte

- Conectividade intermitente

- Sessões sobre HTTP

## <a name="see-also"></a>Consulte também

- [Usando associações para configurar serviços e clientes](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Sessão confiável de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
