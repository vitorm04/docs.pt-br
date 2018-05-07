---
title: Como habilitar transmissão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: b28764c4bad88511096ab09fd71cc2a73c735096
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-streaming"></a>Como habilitar transmissão
Windows Communication Foundation (WCF) pode enviar mensagens usando transferências em buffer ou transmitidas. No modo de transferência em buffer padrão, uma mensagem deve ser entregue completamente antes de um destinatário possa lê-lo. No modo de transferência de streaming, o receptor pode começar a processar a mensagem antes de entregar completamente. O modo de streaming é útil quando as informações que são passadas é demoradas e podem ser processadas em série. O modo contínuo também é útil quando a mensagem é muito grande para ser totalmente armazenada em buffer.  
  
 Para habilitar o streaming, definir o `OperationContract` adequadamente e habilitar o streaming no nível do transporte.  
  
### <a name="to-stream-data"></a>Para transmitir dados  
  
1.  Para transmitir dados, o `OperationContract` para o serviço deve atender a dois requisitos:  
  
    1.  O parâmetro que contém os dados sejam transmitidos deve ser o único parâmetro do método. Por exemplo, se a mensagem de entrada for a ser transmitido, a operação deve ter exatamente um parâmetro de entrada. Da mesma forma, se a mensagem de saída é a transmissão, a operação deve ter exatamente uma saída ou um valor de retorno.  
  
    2.  Pelo menos um dos tipos de valor de parâmetro e retorno deve ser <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, ou <xref:System.Xml.Serialization.IXmlSerializable>.  
  
     Este é um exemplo de um contrato de dados em fluxo.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     O `GetStream` operação recebe alguns dados no buffer de entrada como um `string`, que é armazenado em buffer e retorna um `Stream`, que é transmitido. Por outro lado `UploadStream` assume um `Stream` (Streaming) e retorna um `bool` (em buffer). `EchoStream` Obtém e retorna `Stream` e é um exemplo de uma operação cujas entradas e mensagens de saída ambos são transmitidas. Por fim, `GetReversedStream` não usa nenhuma entrada e retorna um `Stream` (Streaming).  
  
2.  Streaming deve ser habilitado na associação. Definir um `TransferMode` propriedade, que pode ter um dos seguintes valores:  
  
    1.  `Buffered`,  
  
    2.  `Streamed`, que permite a comunicação de streaming em ambas as direções.  
  
    3.  `StreamedRequest`, que permite que a solicitação apenas de streaming.  
  
    4.  `StreamedResponse`, que permite que o fluxo de resposta.  
  
     O `BasicHttpBinding` expõe o `TransferMode` propriedade na associação, como o `NetTcpBinding` e `NetNamedPipeBinding`. O `TransferMode` propriedade também pode ser definida no elemento de associação de transporte e usada em uma associação personalizada.  
  
     Os exemplos a seguir mostram como definir `TransferMode` código e alterando o arquivo de configuração. Os exemplos também definido o `maxReceivedMessageSize` propriedade 64 MB, que impõe um limite de tamanho máximo permitido de mensagens no recebimento. O padrão `maxReceivedMessageSize` é 64 KB, que geralmente é muito baixa para cenários de streaming. Defina essa configuração de cota conforme apropriado, dependendo do tamanho máximo de mensagens de que seu aplicativo espera receber. Observe também que `maxBufferSize` controla o tamanho máximo que é armazenado em buffer e defini-lo apropriadamente.  
  
    1.  O trecho do exemplo de configuração a seguir mostra a configuração de `TransferMode` propriedade para streaming no `basicHttpBinding` e uma associação HTTP personalizada.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  O trecho de código a seguir mostra a configuração de `TransferMode` propriedade para streaming no `basicHttpBinding` e uma associação HTTP personalizada.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  O trecho de código a seguir mostra a configuração de `TransferMode` propriedade para streaming em uma associação personalizada de TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  As operações `GetStream`, `UploadStream`, e `EchoStream` todos lidam com enviar dados diretamente de um arquivo ou salvar dados recebidos diretamente para um arquivo. O código a seguir é para `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Gravando um fluxo personalizados  
  
1.  Para fazer um processamento especial em cada parte de um fluxo de dados como ele está sendo enviado ou recebida, derive uma classe de fluxo personalizados de <xref:System.IO.Stream>. Como um exemplo de um fluxo personalizado, o código a seguir contém um `GetReversedStream` método e uma `ReverseStream` classe-.  
  
     `GetReversedStream` cria e retorna uma nova instância da `ReverseStream`. O processamento real ocorre como o sistema lê a partir de `ReverseStream` objeto. O `ReverseStream.Read` método lê um bloco de bytes do arquivo de base, reverte-los e retorna os bytes invertidos. Esse método não reverte o conteúdo do arquivo inteiro; ele reserva um bloco de bytes de cada vez. Este exemplo mostra como você pode executar o processamento de fluxo que o conteúdo está sendo lida para ou gravada do fluxo.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Dados grandes e streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [Fluxo](../../../../docs/framework/wcf/samples/stream.md)
