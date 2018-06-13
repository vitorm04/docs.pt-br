---
title: Transmissão de transferência de mensagem
ms.date: 03/30/2017
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
ms.openlocfilehash: 340c903e2cb34373514ea2f739cab57dc620df5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499135"
---
# <a name="streaming-message-transfer"></a>Transmissão de transferência de mensagem
Transportes do Windows Communication Foundation (WCF) oferecem suporte a dois modos de transferência de mensagens:  
  
-   Transferências em buffer armazenar a mensagem inteira em um buffer de memória até que a transferência for concluída. Uma mensagem em buffer deve ser entregue completamente antes de um destinatário possa lê-lo.  
  
-   Transferências em fluxo expõem a mensagem como um fluxo. O receptor inicia o processamento da mensagem antes de entregar completamente.  
  
-   Transferências em fluxo podem melhorar a escalabilidade de um serviço, eliminando a necessidade de buffers de memória grandes. Se alterar o modo de transferência melhora a escalabilidade depende do tamanho das mensagens que estão sendo transferidos. Tamanhos de mensagem grande favorecerem usando transferências em fluxo.  
  
 Por padrão, o HTTP, TCP/IP e transportes de pipe nomeado usam transferências em buffer. Este documento descreve como alternar esses transportes de um buffer para o modo de transferência em fluxo e as consequências de fazer isso.  
  
## <a name="enabling-streamed-transfers"></a>Habilitar transferências em fluxo  
 Selecionando entre os modos de transferência em buffer e transmitida é feito no elemento de associação de transporte. O elemento de associação tem um <xref:System.ServiceModel.TransferMode> propriedade que pode ser definida como `Buffered`, `Streamed`, `StreamedRequest`, ou `StreamedResponse`. Definir o modo de transferência para `Streamed` permite transmitir comunicação nas duas direções. Definir o modo de transferência para `StreamedRequest` ou `StreamedResponse` permite transmitir comunicação na direção indicada.  
  
 O <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding>, e <xref:System.ServiceModel.NetNamedPipeBinding> associações exponha o <xref:System.ServiceModel.TransferMode> propriedade. Para outros transportes, você deve criar uma associação personalizada para definir o modo de transferência.  
  
 A decisão de usar transferência em buffer ou em streaming é uma decisão local do ponto de extremidade. Para os transportes HTTP, o modo de transferência não se propaga por uma conexão, ou para servidores e outros intermediários. A definição do modo de transferência não é refletida na descrição da interface de serviço. Depois de gerar uma classe de cliente para um serviço, você deve editar o arquivo de configuração para serviços que se destina a ser usado com transferências em fluxo para definir o modo. Para transportes TCP e pipe nomeado, o modo de transferência é propagado como uma declaração de política.  
  
 Para obter exemplos de código, consulte [como: habilitar o Streaming](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Habilitando o streaming assíncrono  
 Para habilitar o streaming assíncrono, adicione o comportamento do ponto de extremidade <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> ao host de serviço e defina sua propriedade <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> como `true`.  
  
 Esta versão do WCF também adde a capacidade de streaming assíncrona verdadeiro no lado de envio. Isso melhora a escalabilidade do serviço em cenários onde ele está transmitindo mensagens a vários clientes, alguns dos quais estão lentos na leitura; possivelmente devido a congestionamento da rede ou estão não ler nenhum. Nesses cenários WCF não bloqueia segmentos individuais no serviço por cliente. Isso garante que o serviço possa processar muito mais clientes, melhorando dessa forma a escalabilidade do serviço.  
  
## <a name="restrictions-on-streamed-transfers"></a>Restrições em transferências em fluxo  
 Usar o modo de transferência em fluxo faz com que o tempo de execução para impor restrições adicionais.  
  
 As operações que ocorrem em um transporte em fluxo podem ter um contrato com no máximo uma entrada ou saído parâmetro. Esse parâmetro corresponde a todo o corpo da mensagem e deve ser um <xref:System.ServiceModel.Channels.Message>, um derivado do tipo de <xref:System.IO.Stream>, ou um <xref:System.Xml.Serialization.IXmlSerializable> implementação. Ter um valor de retorno para uma operação é equivalente a ter um parâmetro de saída.  
  
 Alguns recursos do WCF, como mensagens confiáveis, transações e segurança em nível de mensagem SOAP, dependem de mensagens para as transmissões de buffer. Usando esses recursos pode reduzir ou eliminar os benefícios de desempenho obtidos usando streaming. Para proteger um transporte em fluxo, use apenas a segurança de nível de transporte ou usar segurança em nível de transporte e segurança de mensagem somente autenticação.  
  
 Cabeçalhos SOAP são sempre armazenados em buffer, mesmo quando o modo de transferência é definido como em fluxo. Os cabeçalhos para uma mensagem não devem exceder o tamanho do `MaxBufferSize` cota de transporte. Para obter mais informações sobre essa configuração, consulte [cotas de transporte](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Diferenças entre as transferências em buffer e em fluxo  
 Alterar o modo de transferência do buffer transmitido também altera a forma de canal nativo do TCP e transportes de pipe nomeado. Para transferências em buffer, a forma de canal nativo é <xref:System.ServiceModel.Channels.IDuplexSessionChannel>. Para transferências em fluxo, os canais nativo são <xref:System.ServiceModel.Channels.IRequestChannel> e <xref:System.ServiceModel.Channels.IReplyChannel>. Alterar o modo de transferência em um aplicativo existente que usa estes transporta diretamente (ou seja, não por meio de um contrato de serviço) requer a alteração da forma de canal esperado para fábricas de canais e ouvintes.  
  
## <a name="see-also"></a>Consulte também  
 [Como habilitar o streaming](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
