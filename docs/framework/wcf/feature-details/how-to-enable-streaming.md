---
title: 'Como: habilitar a transmissão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 0d8428487c3c320a634914b99219e23befb70d55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773016"
---
# <a name="how-to-enable-streaming"></a>Como: habilitar a transmissão
Windows Communication Foundation (WCF) pode enviar mensagens usando transferências em buffer ou transmitidas. No modo de transferência em buffer padrão, uma mensagem deve ser entregue completamente antes de um destinatário possa lê-lo. No modo de transferência de streaming, o receptor pode começar a processar a mensagem antes que seja entregue completamente. O modo de streaming é útil quando as informações que são passadas são demoradas e podem ser processadas em série. Modo de streaming também é útil quando a mensagem é muito grande para ser totalmente armazenada em buffer.  
  
 Para habilitar o streaming, definir o `OperationContract` adequadamente e habilitar o streaming no nível do transporte.  
  
### <a name="to-stream-data"></a>Para transmitir dados  
  
1. Para transmitir dados, o `OperationContract` para o serviço deve atender aos dois requisitos:  
  
    1. O parâmetro que contém os dados sejam transmitidos deve ser o único parâmetro no método. Por exemplo, se a mensagem de entrada é à ser transmitido, a operação deve ter exatamente um parâmetro de entrada. Da mesma forma, se a mensagem de saída deve ser transmitido, a operação deve ter exatamente um parâmetro de saída ou um valor de retorno.  
  
    2. Pelo menos um dos tipos de valor de parâmetro e retorno deve ser <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, ou <xref:System.Xml.Serialization.IXmlSerializable>.  
  
     O exemplo a seguir é um exemplo de um contrato de dados transmitidos.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     O `GetStream` operação recebe alguns dados armazenados em buffer de entrada como uma `string`, que é armazenada em buffer e retorna um `Stream`, que é transmitido. Por outro lado `UploadStream` usa um `Stream` (em fluxo) e retorna um `bool` (em buffer). `EchoStream` usa e retorna `Stream` é um exemplo de uma operação cujas entradas e as mensagens de saída são transmitidas. Por fim, `GetReversedStream` não usa nenhuma entrada e retorna um `Stream` (em fluxo).  
  
2. Streaming deve estar habilitada na associação. Você define uma `TransferMode` propriedade, que pode assumir um dos seguintes valores:  
  
    1. `Buffered`,  
  
    2. `Streamed`, que permite a comunicação de streaming em ambas as direções.  
  
    3. `StreamedRequest`, que permite que apenas a solicitação de streaming.  
  
    4. `StreamedResponse`, que permite que apenas a resposta de streaming.  
  
     O `BasicHttpBinding` expõe o `TransferMode` propriedade na associação, como faz `NetTcpBinding` e `NetNamedPipeBinding`. O `TransferMode` propriedade também pode ser definida no elemento de associação de transporte e usada em uma associação personalizada.  
  
     Os exemplos a seguir mostram como definir `TransferMode` código e alterando o arquivo de configuração. Os exemplos também ambos definidos a `maxReceivedMessageSize` propriedade 64 MB, que coloca um limite para o tamanho máximo permitido de mensagens em receber. O padrão `maxReceivedMessageSize` é de 64 KB, que geralmente é muito baixa para cenários de streaming. Defina essa configuração de cota conforme apropriado, dependendo do tamanho máximo de mensagens que seu aplicativo espera receber. Observe também que `maxBufferSize` controla o tamanho máximo que é armazenada em buffer e defini-lo apropriadamente.  
  
    1. O trecho do exemplo de configuração a seguir mostra a configuração de `TransferMode` propriedade para transmissão no `basicHttpBinding` e uma ligação HTTP personalizada.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2. O trecho de código a seguir mostra a configuração de `TransferMode` propriedade para transmissão no `basicHttpBinding` e uma ligação HTTP personalizada.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. O trecho de código a seguir mostra a configuração de `TransferMode` propriedade para transmissão em uma associação personalizada do TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. As operações `GetStream`, `UploadStream`, e `EchoStream` todos lidam com o envio de dados diretamente de um arquivo ou salvar dados recebidos diretamente para um arquivo. O código a seguir é para `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Escrevendo um fluxo personalizado  
  
1. Para fazer um processamento especial em cada parte de um fluxo de dados conforme ele é enviado ou recebido, derive uma classe de fluxos personalizados de <xref:System.IO.Stream>. Como um exemplo de um fluxo personalizado, o código a seguir contém uma `GetReversedStream` método e um `ReverseStream` classe-.  
  
     `GetReversedStream` cria e retorna uma nova instância da `ReverseStream`. O processamento real ocorre conforme o sistema lê a partir de `ReverseStream` objeto. O `ReverseStream.Read` método lê um bloco de bytes do arquivo subjacente, reverta e retorna os bytes invertidos. Esse método não reverte o conteúdo do arquivo inteiro; ele reserva um bloco de bytes de cada vez. Este exemplo mostra como você pode executar o processamento de fluxo como o conteúdo está sendo lido para ou gravado no fluxo.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Dados grandes e streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [Fluxo](../../../../docs/framework/wcf/samples/stream.md)
