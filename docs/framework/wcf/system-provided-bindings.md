---
title: Associações fornecidas pelo sistema
description: Saiba mais sobre todas as associações do WCF (Windows Communication Foundation) fornecidas pelo sistema.
ms.date: 06/05/2018
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
ms.openlocfilehash: 3c6c6b628d208aede8c547dcfa66fc189a26ae01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569593"
---
# <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema

As associações especificam o mecanismo de comunicação a ser usado ao se comunicar com um ponto de extremidade e indicam como se conectar a um ponto de extremidade. Uma associação contém os seguintes elementos:

- A pilha do protocolo determina a segurança, a confiabilidade e as configurações de fluxo de contexto a serem usadas para as mensagens que são enviadas ao ponto de extremidade.

- O transporte determina o protocolo de transporte subjacente a ser usado ao enviar mensagens para o ponto de extremidade, por exemplo, TCP ou HTTP.

- A codificação determina a codificação de transmissão a ser usada para as mensagens que são enviadas para o ponto de extremidade. Por exemplo, texto/XML, binário ou MTOM (Mecanismo de Otimização de Transmissão de Mensagem).

 Este artigo apresenta todas as associações do WCF (Windows Communication Foundation) fornecidas pelo sistema. Se nenhuma dessas associações atender aos critérios exatos de seu aplicativo, crie uma associação personalizada. Para obter mais informações sobre como criar associações personalizadas, confira [Associações personalizadas](./extending/custom-bindings.md).

 Uma associação segura e interoperável que dá suporte ao protocolo WS-Federation permite às organizações que estão em uma federação autenticar e autorizar usuários com eficiência.

> [!IMPORTANT]
> Sempre selecione uma associação que inclua a segurança. Por padrão, todas as associações, exceto o elemento [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md), têm a segurança habilitada. Se você não selecionar uma associação segura ou desabilitar a segurança, proteja seus dados de alguma outra forma, como armazená-los em um data center protegido ou em uma rede isolada.

> [!IMPORTANT]
> Nunca use contratos duplex com associações que não dão suporte à segurança ou que têm a segurança desabilitada, a menos que você proteja os dados por outros meios.

As seguintes associações são fornecidas com o WCF:

|Associação|Elemento de configuração|Descrição|
|-------------|---------------------------|-----------------|
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md)|Uma associação adequada para comunicação com serviços Web em conformidade com o WS-Basic Profile, por exemplo, serviços baseados em serviços Web do ASP.NET (ASMX). Essa associação usa HTTP como o transporte e texto/XML como a codificação de mensagem padrão.|
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)|Uma associação segura e interoperável que é adequada para contratos de serviço não duplex.|
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Uma associação segura e interoperável que é adequada para contratos de serviços duplex ou para comunicação por intermediários SOAP.|
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Uma associação segura e interoperável que dá suporte ao protocolo WS-Federation, que permite às organizações que estão em uma federação autenticar e autorizar usuários com eficiência.|
|<xref:System.ServiceModel.NetHttpBinding>|[\<netHttpBinding>](../configure-apps/file-schema/wcf/nethttpbinding.md)|Uma associação criada para consumir serviços HTTP ou WebSocket que usa a codificação binária por padrão.|
|<xref:System.ServiceModel.NetHttpsBinding>|[\<netHttpsBinding>](../configure-apps/file-schema/wcf/nethttpsbinding.md)|Uma associação segura criada para consumir serviços HTTP ou WebSocket que usa a codificação binária por padrão.|
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)|Uma associação segura e otimizada, adequada para comunicação de computadores entre aplicativos do WCF.|
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../configure-apps/file-schema/wcf/netnamedpipebinding.md)|Uma associação segura, confiável e otimizada, que é adequada para comunicação no computador entre aplicativos do WCF.|
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../configure-apps/file-schema/wcf/netmsmqbinding.md)|Uma associação na fila que é adequada para comunicação de computadores entre aplicativos do WCF.|
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../configure-apps/file-schema/wcf/netpeertcpbinding.md)|Uma associação que permite uma comunicação segura entre vários computadores.|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Uma associação adequada para comunicação de computadores entre um aplicativo do WCF e os aplicativos existentes do Enfileiramento de Mensagens.|
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding>](../configure-apps/file-schema/wcf/basichttpcontextbinding.md)|Uma associação adequada para comunicação com os serviços Web em conformidade com o WS-Basic Profile, que permite o uso de cookies HTTP para a troca de contexto.|
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding>](../configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Uma associação segura e otimizada, adequada para comunicação de computadores entre aplicativos do WCF que permite o uso de cabeçalhos SOAP para a troca de contexto.|
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../configure-apps/file-schema/wcf/webhttpbinding.md)|Uma associação usada para configurar pontos de extremidade para serviços Web WCF expostos por meio de solicitações HTTP, em vez de mensagens SOAP.|
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding>](../configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Uma associação segura e interoperável, adequada para contratos de serviço não duplex, que permite o uso de cabeçalhos SOAP para a troca de contexto.|
|<xref:System.ServiceModel.UdpBinding>|[\<udpBinding>](../configure-apps/file-schema/wcf/udpbinding.md)|Uma associação a ser usada ao enviar uma intermitência de mensagens simples para um grande número de clientes simultaneamente.|

 A tabela a seguir mostra as funcionalidades de cada uma das associações fornecidas pelo sistema. As associações encontram-se nas colunas da tabela; as funcionalidades são listadas nas linhas e descritas em uma segunda tabela. A tabela a seguir fornece um código para as abreviações de associação usadas. Para escolher uma associação, determine qual coluna atende a todas as funcionalidades de linha necessárias.

|Associação|Interoperabilidade|Segurança (padrão)|Session<br />(Padrão)|Transações|Duplex|Codificação (padrão)|Streaming<br />(Padrão)|
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Nenhum), Transporte, Mensagem, Misto|(Nenhum)|(Nenhum)|N/D|Texto, (MTOM)|Sim<br />(em buffer)|
|<xref:System.ServiceModel.WSHttpBinding>|WS|Transporte, (Mensagem), Misto|(Nenhum), Sessão Confiável, Sessão de Segurança|(Nenhum), Sim|N/D|(Texto), MTOM|Não|
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(Mensagem), Nenhum|(Sessão Confiável), Sessão de Segurança|(Nenhum), Sim|Sim|(Texto), MTOM|Não|
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(Mensagem), Misto, Nenhum|(Nenhum), Sessão Confiável, Sessão de Segurança|(Nenhum), Sim|Não|(Texto), MTOM|Não|
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(Nenhum), Transporte, Mensagem, TransportWithMessageCredential, TransportCredentialOnly|Veja a observação abaixo|Nenhum|Veja a observação abaixo|(Binário), Texto, MTOM|Sim (em buffer)|
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Transporte), TransportWithMessageCredential|Veja a observação abaixo|Nenhum|Veja a observação abaixo|(Binário), Texto, MTOM|Sim<br />(em buffer)|
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Transporte), Mensagem, Nenhum, Misto|(Transporte), Sessão Confiável, Sessão de Segurança|(Nenhum), Sim|Sim|Binário|Sim<br />(em buffer)|
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Transporte), Nenhum|Nenhum, (Transporte)|(Nenhum), Sim|Sim|Binário|Sim<br />(em buffer)|
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Mensagem, (Transporte), Nenhum|(Nenhum), Transporte|Nenhum, (Sim)|Não|Binário|Não|
|<xref:System.ServiceModel.NetPeerTcpBinding>|Par|(Transporte)|(Nenhum)|(Nenhum)|Sim||Não|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Transporte)|(Nenhum)|Nenhum, (Sim)|N/D|N/D|Não|
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(Nenhum), Transporte, Mensagem, Misto|(Nenhum)|(Nenhum)|N/D|Texto, (MTOM)|Sim<br />(em buffer)|
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Transporte), Mensagem, Nenhum, Misto|(Transporte), Sessão Confiável, Sessão de Segurança|(Nenhum), Sim|Sim|Binário|Sim<br />(em buffer)|
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Transporte, (Mensagem), Misto|(Nenhum), Sessão Confiável, Sessão de Segurança|(Nenhum), Sim|N/D|Texto, (MTOM)|Não|
|<xref:System.ServiceModel.UdpBinding> <br /><br /> **Observação:**  Interoperabilidade pode ser obtida com a implementação de especificações de SOAP-over-UDP padrão que implementa essa associação.|.NET|(Nenhum)|(Nenhum)|(Nenhum)|N/D|(Texto)|Não|

> [!IMPORTANT]
> O <xref:System.ServiceModel.NetHttpBinding> é uma associação criada para consumir HTTP ou serviços WebSocket e usa a codificação binária por padrão. <xref:System.ServiceModel.NetHttpBinding> detecta se ela é usada com um contrato de solicitação-resposta ou um contrato duplex e altera seu comportamento para fins de correspondência; ela usa o HTTP para a solicitação-resposta e o WebSockets para o duplex. Esse comportamento pode ser substituído usando o <xref:System.ServiceModel.Channels.WebSocketTransportUsage> configuração de associação: WhenDuplex - este é o valor padrão e comporta-se como descrito acima. Nunca - isso impede que o WebSockets seja usado. A tentativa de usar um contrato duplex com essa configuração resulta em uma exceção. Sempre - isso força o WebSockets a ser usado mesmo para contratos de solicitação-resposta. NetHttpBinding dá suporte a sessões confiáveis nos modos HTTP e WebSocket. No modo WebSocket as sessões são fornecidas pelo transporte.

 A tabela a seguir explica as funcionalidades listadas na tabela anterior.

|Recurso|Descrição|
|-------------|-----------------|
|Tipo de interoperabilidade|Nomeia a tecnologia ou o protocolo com o qual a associação garante a interoperação.|
|Segurança|Especifica como o canal é protegido:<br />-None: A mensagem SOAP não é seguras e o cliente não está autenticado.<br />-Transporte: Requisitos de segurança são satisfeitos na camada de transporte.<br />-Mensagem: Requisitos de segurança são satisfeitos na camada de mensagem.<br />-Misto: Declarações são transportadas no message; requisitos de integridade e confidencialidade forem atendidos pela camada de transporte.|
|Session|Especifica se essa associação dá suporte a contratos de sessão.|
|Transações|Especifica se as transações estão habilitadas.|
|Duplex|Especifica se há suporte para os contratos duplex. Observe que essa funcionalidade exige suporte para Sessões na associação.|
|Codificando|Especifica o formato de transmissão da mensagem. Os valores permitidos incluem:<br />- Texto: por exemplo, UTF-8.<br />- Binário<br />-Mecanismo de otimização de transmissão mensagem (MTOM): Um método de codificação com eficiência binários elementos XML dentro do contexto de um envelope SOAP.|
|Streaming|Especifica se há suporte para streaming em mensagens de entrada e de saída. Use a propriedade `TransferMode` na associação para definir o valor. Os valores permitidos incluem:<br />- <xref:System.ServiceModel.TransferMode.Buffered>: As mensagens de solicitação e resposta são armazenadas em buffer.<br />- <xref:System.ServiceModel.TransferMode.Streamed>: As mensagens de solicitação e resposta são transmitidas.<br />- <xref:System.ServiceModel.TransferMode.StreamedRequest>: A mensagem de solicitação é transmitida e a mensagem de resposta é armazenada em buffer.<br />- <xref:System.ServiceModel.TransferMode.StreamedResponse>: A mensagem de solicitação é armazenada em buffer e a mensagem de resposta é transmitida.|

## <a name="see-also"></a>Consulte também

- [Visão geral de criação de ponto de extremidade](endpoint-creation-overview.md)
- [Usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md)
- [Programação básica do WCF](basic-wcf-programming.md)
