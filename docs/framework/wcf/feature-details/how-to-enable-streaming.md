---
title: Como habilitar transmissão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 1d1eaa1ebf41ef86478dda795b3b199239cd37b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184943"
---
# <a name="how-to-enable-streaming"></a>Como habilitar transmissão
O Windows Communication Foundation (WCF) pode enviar mensagens usando transferências tamponadas ou transmitidas. No modo de transferência tampão padrão, uma mensagem deve ser completamente entregue antes que um receptor possa lê-la. No modo de transferência por streaming, o receptor pode começar a processar a mensagem antes de ser completamente entregue. O modo de streaming é útil quando as informações passadas são longas e podem ser processadas em série. O modo de streaming também é útil quando a mensagem é muito grande para ser totalmente tamponada.  
  
 Para habilitar o `OperationContract` streaming, defina o fluxo adequadamente e habilite o streaming no nível de transporte.  
  
### <a name="to-stream-data"></a>Para transmitir dados  
  
1. Para transmitir dados, o `OperationContract` serviço deve satisfazer dois requisitos:  
  
    1. O parâmetro que contém os dados a serem transmitidos deve ser o único parâmetro no método. Por exemplo, se a mensagem de entrada for a que deve ser transmitida, a operação deve ter exatamente um parâmetro de entrada. Da mesma forma, se a mensagem de saída for transmitida, a operação deve ter exatamente um parâmetro de saída ou um valor de retorno.  
  
    2. Pelo menos um dos tipos de parâmetro e <xref:System.IO.Stream>valor <xref:System.ServiceModel.Channels.Message>de <xref:System.Xml.Serialization.IXmlSerializable>retorno deve ser, ou .  
  
     A seguir, um exemplo de um contrato para dados transmitidos.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     A `GetStream` operação recebe alguns dados `string`de entrada tamponados `Stream`como a , que é tamponado, e retorna um , que é transmitido. Por `UploadStream` outro lado, recebe um `Stream` (transmitido) e retorna um `bool` (tampão). `EchoStream`leva e `Stream` retorna e é um exemplo de uma operação cujas mensagens de entrada e saída são transmitidas. Finalmente, `GetReversedStream` não pega entradas `Stream` e retorna um (transmitido).  
  
2. O streaming deve ser ativado na ligação. Você define `TransferMode` uma propriedade, que pode levar um dos seguintes valores:  
  
    1. `Buffered`,  
  
    2. `Streamed`, que permite a comunicação por streaming em ambas as direções.  
  
    3. `StreamedRequest`, que permite apenas transmitir a solicitação.  
  
    4. `StreamedResponse`, que permite transmitir apenas a resposta.  
  
     O `BasicHttpBinding` expõe `TransferMode` a propriedade na vinculação, assim `NetTcpBinding` como e `NetNamedPipeBinding`. A `TransferMode` propriedade também pode ser definida no elemento de ligação de transporte e usada em uma vinculação personalizada.  
  
     As amostras a seguir `TransferMode` mostram como definir por código e alterando o arquivo de configuração. As amostras também `maxReceivedMessageSize` definem a propriedade como 64 MB, o que coloca uma tampa no tamanho máximo permitido das mensagens no recebimento. O `maxReceivedMessageSize` padrão é 64 KB, que geralmente é muito baixo para cenários de streaming. Defina essa configuração de cota conforme apropriado, dependendo do tamanho máximo das mensagens que seu aplicativo espera receber. Observe também `maxBufferSize` que controla o tamanho máximo que é tamponado e defina-o adequadamente.  
  
    1. O trecho de configuração a seguir `TransferMode` da amostra `basicHttpBinding` mostra a configuração da propriedade para streaming na e uma vinculação HTTP personalizada.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. O trecho de código a `TransferMode` seguir mostra `basicHttpBinding` a configuração da propriedade para streaming na e uma vinculação HTTP personalizada.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. O trecho de código a `TransferMode` seguir mostra a configuração da propriedade para streaming em uma vinculação TCP personalizada.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. As `GetStream`operações `UploadStream` `EchoStream` , e todas lidam com o envio de dados diretamente de um arquivo ou a economia de dados recebidos diretamente para um arquivo. O seguinte código `GetStream`é para .  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Escrevendo um fluxo personalizado  
  
1. Para fazer um processamento especial em cada pedaço de um fluxo de dados <xref:System.IO.Stream>à medida que ele está sendo enviado ou recebido, obtenha uma classe de fluxo personalizada de . Como exemplo de um fluxo personalizado, `GetReversedStream` o código `ReverseStream` a seguir contém um método e uma classe-.  
  
     `GetReversedStream`cria e retorna uma `ReverseStream`nova instância de . O processamento real acontece quando o `ReverseStream` sistema lê do objeto. O `ReverseStream.Read` método lê um pedaço de bytes do arquivo subjacente, inverte-os e retorna os bytes invertidos. Este método não reverte todo o conteúdo do arquivo; ele inverte um pedaço de bytes de cada vez. Este exemplo mostra como você pode executar o processamento de fluxo à medida que o conteúdo está sendo lido ou escrito a partir do fluxo.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Confira também

- [Dados grandes e streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [Fluxo](../../../../docs/framework/wcf/samples/stream.md)
